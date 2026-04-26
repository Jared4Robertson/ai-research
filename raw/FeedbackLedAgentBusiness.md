## Core Activities

- Gathering Feedback from Users & Stakeholders and analyzing it
- Mapping & Iterating on User Journeys for the product based on the feedback
- Determining & Iterating on Capabilities & Rules
- Designing & Iterating on System Architecture
- Planning & Iterating on Product Roadmap
- Designing & Iterating on Development Lifecycle
- Creating Technical Tasks based on Development Lifecycle (CI/CD, Testing, Deployment, etc.)
- Creating Epics/PRDs
- Creating Technical Design Documents (TDDs)
- Creating User Stories based on the Epics/PRDs/TDDs
- Creating Sub-Tasks based on the User Stories
- Implementing the Sub-Tasks based on the User Stories/Sub-Tasks
- Testing & Evaluating the Technical Tasks/User Stories/Sub-Tasks/Epics/PRDs/TDDs Implementations

## Core Artifacts

- User Feedback & Analysis
- User Journeys
- Capabilities & Rules
- System Architecture
- Product Roadmap
- Development Lifecycle
- Technical Tasks
- Epics/PRDs
- Technical Design Documents (TDDs)
- User Stories
- Sub-Tasks
- Software Assets (Code, Documentation, Tests, etc.)

## Product Life Cycle Pseudo Code

The same workflow expressed in three different styles. All three reuse the vocabulary from the Core Activities and Core Artifacts above.

### Style A — Imperative / Procedural

A single outer loop that walks the artifacts in dependency order. The feedback-led nature shows up as the loop refresh trigger.

```text
function run_product_lifecycle():
    artifacts = initialize_artifacts()
    while product_exists:
        feedback        = gather_feedback(users, stakeholders)
        analysis        = analyze(feedback)                       # -> UserFeedback&Analysis

        artifacts.user_journeys      = iterate(artifacts.user_journeys, analysis)
        artifacts.capabilities_rules = iterate(artifacts.capabilities_rules, artifacts.user_journeys)
        artifacts.system_architecture= iterate(artifacts.system_architecture, artifacts.capabilities_rules)
        artifacts.product_roadmap    = iterate(artifacts.product_roadmap, artifacts.user_journeys, artifacts.system_architecture)
        artifacts.dev_lifecycle      = iterate(artifacts.dev_lifecycle, artifacts.product_roadmap)

        technical_tasks = create_technical_tasks(artifacts.dev_lifecycle)
        epics_prds      = create_epics_prds(artifacts.product_roadmap, artifacts.user_journeys)
        tdds            = create_tdds(epics_prds, artifacts.system_architecture)
        user_stories    = create_user_stories(epics_prds, tdds)
        sub_tasks       = create_sub_tasks(user_stories)

        for task in technical_tasks + sub_tasks:
            artifacts.software_assets += implement(task)
            results = test_and_evaluate(task, artifacts.software_assets)
            record(results)  # feeds back into next loop's gather_feedback()
```

### Style B — Event-Driven

Handlers reacting to events. Each artifact update emits an event that downstream handlers subscribe to. Models how feedback ripples asynchronously through the org.

```text
on FeedbackReceived(feedback):
    emit AnalysisReady(analyze(feedback))

on AnalysisReady(analysis):
    emit UserJourneysUpdated(iterate(user_journeys, analysis))

on UserJourneysUpdated(journeys):
    emit CapabilitiesUpdated(iterate(capabilities_rules, journeys))
    emit RoadmapNeedsReview(journeys)

on CapabilitiesUpdated(caps):
    emit ArchitectureUpdated(iterate(system_architecture, caps))

on ArchitectureUpdated(arch) | RoadmapNeedsReview(_):
    emit RoadmapUpdated(iterate(product_roadmap, arch, journeys))

on RoadmapUpdated(roadmap):
    emit DevLifecycleUpdated(iterate(dev_lifecycle, roadmap))
    emit EpicsReady(create_epics_prds(roadmap, user_journeys))

on DevLifecycleUpdated(dlc):
    emit TechnicalTasksReady(create_technical_tasks(dlc))

on EpicsReady(epics):
    emit TDDsReady(create_tdds(epics, system_architecture))

on TDDsReady(tdds):
    emit UserStoriesReady(create_user_stories(epics, tdds))

on UserStoriesReady(stories):
    emit SubTasksReady(create_sub_tasks(stories))

on TechnicalTasksReady(tasks) | SubTasksReady(tasks):
    for t in tasks:
        assets  = implement(t)
        results = test_and_evaluate(t, assets)
        emit FeedbackReceived(results)   # closes the loop
```

### Style C — Agent-Oriented

Each Core Activity becomes an autonomous agent that owns one Core Artifact and subscribes to upstream artifacts. Closest to the "feedback-led agent business" framing.

```text
agent FeedbackAgent:
    owns:      UserFeedback&Analysis
    inputs:    [users, stakeholders, prior_release_results]
    loop:
        raw = poll(inputs)
        owns.update(analyze(raw))
        notify(downstream)

agent UserJourneyAgent:
    owns:      UserJourneys
    subscribes:[UserFeedback&Analysis]
    on update: owns.iterate(inputs); notify([CapabilitiesAgent, RoadmapAgent])

agent CapabilitiesAgent:
    owns:      Capabilities&Rules
    subscribes:[UserJourneys]
    on update: owns.iterate(inputs); notify([ArchitectureAgent])

agent ArchitectureAgent:
    owns:      SystemArchitecture
    subscribes:[Capabilities&Rules]
    on update: owns.iterate(inputs); notify([RoadmapAgent, TDDAgent])

agent RoadmapAgent:
    owns:      ProductRoadmap
    subscribes:[UserJourneys, SystemArchitecture]
    on update: owns.iterate(inputs); notify([DevLifecycleAgent, EpicAgent])

agent DevLifecycleAgent:
    owns:      DevelopmentLifecycle
    subscribes:[ProductRoadmap]
    on update: owns.iterate(inputs); notify([TechnicalTaskAgent])

agent TechnicalTaskAgent:
    owns:      TechnicalTasks
    subscribes:[DevelopmentLifecycle]
    on update: owns.regenerate(inputs); dispatch_to(ImplementationAgent)

agent EpicAgent:
    owns:      Epics/PRDs
    subscribes:[ProductRoadmap, UserJourneys]
    on update: owns.regenerate(inputs); notify([TDDAgent])

agent TDDAgent:
    owns:      TDDs
    subscribes:[Epics/PRDs, SystemArchitecture]
    on update: owns.regenerate(inputs); notify([UserStoryAgent])

agent UserStoryAgent:
    owns:      UserStories
    subscribes:[Epics/PRDs, TDDs]
    on update: owns.regenerate(inputs); notify([SubTaskAgent])

agent SubTaskAgent:
    owns:      SubTasks
    subscribes:[UserStories]
    on update: owns.regenerate(inputs); dispatch_to(ImplementationAgent)

agent ImplementationAgent:
    owns:      SoftwareAssets
    subscribes:[TechnicalTasks, SubTasks]
    on dispatch(task):
        owns.append(implement(task))
        results = test_and_evaluate(task, owns)
        send_to(FeedbackAgent, results)  # closes the loop
```

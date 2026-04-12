# Legacy System Replacement: The Question Chain

A step-by-step sequence of simple questions that walks a team from "we need to replace a legacy system" to well-defined epics, stories, and tasks. Each question has a clear expected answer format, and each answer feeds the next question.

---

## 1. Orient

### Q1: What does this system do?

- Answer in one sentence: "The settlement system does _____ for _____."
- If different people give different one-sentence answers, that's your first red flag.

**Expected answer:** A single sentence.

---

## 2. People

### Q2: What roles directly use the system?

- List every role title that interacts with the system — e.g. settlement analyst, operations manager, client support rep.
- Roles, not individual names. Each role represents a distinct way someone uses the system.

**Expected answer:** A list of role titles.

### Q3: For each role, what are they trying to accomplish with the system?

- One sentence per role: "[Role] uses the system to _____."
- Stay at the goal level, not the step-by-step level. "Process daily settlements" not "click the reconcile button then export the CSV."

**Expected answer:** A list of role + goal pairs.

### Q4: Who depends on the system's results but doesn't use it directly?

- These are stakeholders — e.g. compliance officer, finance director, client relationship manager.
- They care about outcomes (accuracy, timeliness, compliance) but don't log in.

**Expected answer:** A list of role titles.

---

## 3. Value

### Q5: What would happen if this system stopped working tomorrow?

- What breaks first? What breaks worst?
- Which roles from Q2–Q4 are impacted, and how?
- What would people have to do manually as a workaround?
- What consequences would reach customers, regulators, or the business's bottom line?

**Expected answer:** A list of concrete consequences, naturally sorted by severity.

**Why this matters:** The things that would break worst are the things the replacement must get right first. The things nobody would miss are candidates to drop. This answer becomes your priority map.

---

## 4. Pain

### Q6: Why are we replacing this system instead of just keeping it?

- What can't the current system do that the business needs it to do?
- What is it costing us — in time, money, risk, or missed opportunity?
- What workarounds have people built around its limitations?
- Where is it fragile, slow, or error-prone?

**Expected answer:** A list of specific limitations and their business impact.

**Why this matters:** This is the business case for the replacement. If the answers are vague ("it's old," "it's legacy"), the team doesn't actually understand *why* they're rebuilding — and that's how you end up with a new system that has new problems instead of fewer problems.

---

## 5. Vision

### Q7: What should the new system make possible that the current one can't?

- Not a technology wish list. Not "microservices" or "cloud-native."
- Answer in terms of what changes for the roles from Q2–Q4: what can they do that they couldn't before?
- What business outcomes become achievable that aren't today?

**Expected answer:** A short list of concrete capabilities or outcomes, tied to the pain from Q6.

**Why this matters:** This is the product vision — grounded in real pain, not aspiration. If a proposed capability doesn't trace back to a pain from Q6 or a goal from Q3, it's scope creep before you've even started.

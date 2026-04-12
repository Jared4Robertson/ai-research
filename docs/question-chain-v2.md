# The Question Chain: From Idea to Defined Work

A step-by-step sequence of simple questions that walks a team from "we need to build a product" to well-defined epics, stories, and tasks. Each question has a clear expected answer format, and each answer feeds the next question.

The answers land in four artifacts.

---

## 1. Product Brief

**Owner:** PM-A with Product Director

### Q1: What are we building and why?

- Answer in one sentence: "We are building _____ so that _____."
- If different people give different answers, that's your first red flag.

**Expected answer:** A single sentence.

### Q2: Who cares about this product's results but won't use it directly?

- These are stakeholders — e.g. compliance officer, finance director, client relationship manager.
- They care about outcomes (accuracy, timeliness, compliance) but won't log in.

**Expected answer:** A list of role titles.

### Q3: Who is our customer?

- The external people or organizations who receive value from this product.
- Roles, not individual names — e.g. client settlement operator, fund manager.

**Expected answer:** A list of customer role titles.

---

## 2. User Journeys

**Owner:** PM-B with EM

### Q4: Who are our internal users?

- The people inside our organization who use this product to deliver value to the customer.
- Roles, not individual names — e.g. settlement analyst, operations manager, client support rep.

**Expected answer:** A list of internal role titles.

### Q5: For each role, what are they trying to accomplish?

- One sentence per role: "[Role] needs to _____."
- Stay at the goal level, not the step-by-step level.
- Covers both customer roles from Q3 and internal roles from Q4.

**Expected answer:** A list of role + goal pairs.

### Q6: For each role, what is the step-by-step experience of using this product to accomplish their goal?

- Walk through the journey: "First they _____, then they _____, then they _____."
- Include the moments where they're waiting, making decisions, handing off to someone else, or leaving the product entirely.
- Note where different roles' journeys overlap or connect.

**Expected answer:** A step-by-step journey per role, in plain language.

---

## 3. Capabilities & Rules

**Owner:** PM-B + EM + PM-A

### Q7: Based on the user journeys, what must this product be able to do?

- Each capability is a thing the product does, stated without specifying how — e.g. "calculate settlement amounts," "notify users when reconciliation fails," "generate audit reports."
- Every capability should trace back to a step in a user journey (Q6). If it doesn't trace back, question whether it's needed.

**Expected answer:** A list of capabilities.

### Q8: What are the business rules this product must follow, regardless of how it's built?

- These are rules of the business, not rules of the software.
- The test: if a rule would still be true even if you did everything on paper and spreadsheets, it belongs here.
- Number each rule so they can be referenced later in stories and technical decisions (e.g. BR-01, BR-02).

**Expected answer:** A numbered list of non-negotiable rules.

---

## 4. System Map

**Owner:** EM with Senior Engineers

### Q9: What is inside this system and what is outside?

- What does this product own vs. what does it get from other systems?
- Where are the integration points — what data comes in, what goes out, and to/from where?
- What is explicitly not part of this system, even if it's related?

**Expected answer:** A list of what's in, what's out, and where the edges are.

### Q10: How do the pieces inside this system relate to each other?

- What are the major modules or services inside the product?
- Which module owns which capabilities from Q7?
- How do they communicate — what data flows between them?
- Where are the seams between different teams' ownership?

**Expected answer:** A list of internal modules/services, what each owns, and how they connect.

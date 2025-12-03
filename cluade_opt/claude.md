# AI-Assisted Development Framework for Non-Programmers

This is a thorough analysis of your pain points and a complete restructured workflow.

---

## Root Cause Diagnosis

Your current workflow fails because of these structural gaps:

| Symptom | Root Cause |
|---------|------------|
| Unrealizable features | No feasibility check before coding |
| Disorganized codebase | No architecture phase; AI jumps straight to implementation |
| Unresolvable bugs | No incremental testing; errors compound |
| Stalled projects | No living document tracking state; AI loses context |
| Feature modification breaks things | No modular design; no impact analysis |

---

## The 7-Phase Framework

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE 0: PROJECT INITIALIZATION                                            │
│  → Scope, constraints, success criteria                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 1: REQUIREMENTS ENGINEERING                                          │
│  → Transform vague ideas into structured specs                              │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 2: ARCHITECTURE & DESIGN (★ Most commonly skipped!)                  │
│  → Modular design BEFORE any code                                           │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 3: INCREMENTAL DEVELOPMENT                                           │
│  → Build & verify in small units                                            │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 4: TESTING & DEBUGGING                                               │
│  → Structured error reporting & isolation                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 5: FEATURE EVOLUTION                                                 │
│  → Safe modification with impact analysis                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 6: PROJECT TRACKING DOCUMENT (★ Critical for AI context!)            │
│  → Living document maintained throughout all phases                         │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## PHASE 0: Project Initialization

### Purpose
Establish boundaries BEFORE any development. This prevents scope creep and "unrealizable features."

### Your Current Approach
> *"I want a tool that does X"* → immediately ask AI to code

### Systematic Actions
1. Define what the project **is** and **is not**
2. Identify hard constraints (platform, dependencies, skill level)
3. Set explicit success criteria

### Optimized Prompt Template

```markdown
## Project Initialization Request

### 1. Project Goal (one sentence)
I want to build: [A tool/script that accomplishes X primary purpose]

### 2. Scope Boundaries
**In scope:**
- [Core feature 1]
- [Core feature 2]

**Explicitly out of scope:**
- [Feature I do NOT need]
- [Complexity I want to avoid]

### 3. Constraints
- **Platform/Environment:** [Windows/Mac/Linux, Python version, etc.]
- **Dependencies:** [Prefer no external libraries / Specific libraries allowed]
- **My skill level:** [Cannot debug complex code / Can read but not write code]
- **Performance requirements:** [None / Must handle X records]

### 4. Success Criteria
This project is "done" when:
- [ ] Criterion 1
- [ ] Criterion 2

---

**Request:** Before any coding, please:
1. Confirm you understand the scope
2. Identify any potential technical risks or ambiguities
3. Flag anything that might be difficult to implement given my constraints
4. Ask clarifying questions if needed
```

---

## PHASE 1: Requirements Engineering

### Purpose
Transform vague ideas into testable specifications. This prevents "I meant something else" iterations.

### Your Current Approach
> *"The input is a file, do some processing, output results"*

### Systematic Actions
1. Define EXACT input format with examples
2. Define EXACT output format with examples
3. Specify edge cases and error handling
4. Create acceptance test cases

### Optimized Prompt Template

```markdown
## Requirements Specification

### Input Specification
- **Source:** [File path / User input / API / etc.]
- **Format:** [CSV / JSON / plain text / etc.]
- **Structure:** [Describe columns, fields, or format]

**Sample Input:**
```
[Paste 3-5 representative examples, including edge cases]
```

### Processing Logic
**Step-by-step workflow (in plain language):**
1. First, [action 1]
2. Then, [action 2]
3. If [condition], then [action]; otherwise [alternative]
4. Finally, [action N]

**Business Rules:**
- Rule 1: [e.g., "Dates before 2020 should be flagged as invalid"]
- Rule 2: [e.g., "Empty fields default to 0"]

### Output Specification
- **Destination:** [File / Console / GUI / etc.]
- **Format:** [Describe exact structure]

**Expected Output for Sample Input:**
```
[Show exact expected output corresponding to your sample input]
```

### Edge Cases & Error Handling
| Scenario | Expected Behavior |
|----------|-------------------|
| Empty input file | [Show error message and exit] |
| Malformed row | [Skip and log warning] |
| [Other edge case] | [Behavior] |

---

**Request:** Please:
1. Restate these requirements in your own words to confirm understanding
2. Identify any ambiguities or missing specifications
3. Suggest any edge cases I may have overlooked
4. DO NOT write code yet
```

---

## PHASE 2: Architecture & Design

### Purpose
Design the structure BEFORE implementation. This is **the most skipped phase** and the #1 reason for "disorganized codebase."

### Your Current Approach
> *Skipped entirely* → AI produces monolithic, unmodifiable code

### Systematic Actions
1. Request architecture proposal (no code yet)
2. Review and approve module breakdown
3. Understand data flow between components
4. Identify which parts are "stable" vs "likely to change"

### Optimized Prompt Template

```markdown
## Architecture Design Request

Based on the requirements above, please design the architecture BEFORE writing code.

### Requested Deliverables:

**1. Module Breakdown**
List each logical module/function with:
- Name
- Single responsibility (one sentence)
- Inputs and outputs

**2. Data Flow Diagram (text-based)**
Show how data moves through the system:
```
[Input] → [Module A] → [Module B] → [Output]
              ↓
         [Module C]
```

**3. Interface Definitions**
For each module, specify:
- Function signature (name, parameters, return type)
- Brief description

**4. Dependency Map**
Which modules depend on which? (This helps me understand impact of changes)

**5. Risk Assessment**
- Which parts are most complex?
- Which parts are most likely to need modification later?
- Recommended development order (build stable parts first)

---

**Rules:**
- DO NOT write implementation code yet
- Keep each module focused on ONE responsibility
- Design for my skill level: [simple/intermediate]
```

---

## PHASE 3: Incremental Development

### Purpose
Build in small, verified steps. Never write >50 lines without testing.

### Your Current Approach
> *"Give me all the code"* → 200+ lines → Something fails → No idea where

### Systematic Actions
1. Request ONE module at a time
2. Test that module in isolation
3. Confirm it works before requesting the next
4. Integrate gradually

### Optimized Prompt Template

```markdown
## Incremental Development Request

### Current Progress
**Completed and verified modules:**
- [x] Module A (tested, working)
- [x] Module B (tested, working)

**Current request:** Module C

---

### Request for This Iteration

Please implement ONLY: `[module_name]`

**Requirements for this module:**
- Input: [what it receives]
- Output: [what it returns]
- Logic: [reference requirements doc section]

**Provide:**
1. The module code
2. A standalone test snippet I can run to verify it works
3. Example test input and expected output

**Test Criteria:**
- Test case 1: Input X → Expected output Y
- Test case 2: Input A → Expected output B

---

**DO NOT:**
- Implement other modules
- Modify previously completed modules
- Add features not in the specification
```

### Module Verification Template

After receiving code, USE THIS before moving on:

```markdown
## Module Verification Report

**Module:** [name]
**Status:** [PASS / FAIL]

### Test Results
| Test Case | Input | Expected | Actual | Status |
|-----------|-------|----------|--------|--------|
| Test 1 | X | Y | Y | ✅ PASS |
| Test 2 | A | B | C | ❌ FAIL |

### Issues Found
- [Issue description if any]

### Decision
- [ ] Proceed to next module
- [ ] Request fixes (see debugging prompt below)
```

---

## PHASE 4: Testing & Debugging

### Purpose
Structured problem diagnosis. This prevents "AI changed one thing and broke three others."

### Your Current Approach
> *"It's not working, please fix"* → AI guesses → Makes random changes → Worse

### Systematic Actions
1. Isolate the problem (which module? which input?)
2. Provide COMPLETE error context
3. Request diagnosis BEFORE fix
4. Verify fix doesn't break existing functionality

### Optimized Prompt Template: Bug Report

```markdown
## Bug Report

### Environment
- Python version: [X.X]
- OS: [Windows/Mac/Linux]
- Dependencies: [list with versions]

### Bug Location
- **File/Module:** [name]
- **Function:** [name]
- **Line number (if known):** [N]

### Reproduction Steps
1. [Exact step 1]
2. [Exact step 2]
3. [Exact step 3]

### Input That Causes the Bug
```
[Paste exact input]
```

### Expected Behavior
[What should happen]

### Actual Behavior
[What actually happens]

### Complete Error Message
```
[Paste FULL error traceback, not just the last line]
```

### What I Already Tried
- [Attempt 1 and result]
- [Attempt 2 and result]

---

**Request:**
1. FIRST: Diagnose the root cause (explain what's happening and why)
2. THEN: Propose a fix
3. CONFIRM: This fix will not affect [list other working modules]
4. PROVIDE: A test to verify the fix works
```

### Optimized Prompt Template: Regression Check

```markdown
## Post-Fix Verification Request

You just modified [module/function] to fix [bug].

Please provide a test suite that verifies:
1. The original bug is fixed
2. All previously working functionality still works

**Previously Working Test Cases (must still pass):**
| Test | Input | Expected Output |
|------|-------|-----------------|
| [Original test 1] | X | Y |
| [Original test 2] | A | B |

**New Test Case (for the bug fix):**
| Test | Input | Expected Output |
|------|-------|-----------------|
| [Bug scenario] | [Problematic input] | [Correct output] |
```

---

## PHASE 5: Feature Evolution

### Purpose
Safely modify working code. This prevents "adding feature X broke feature Y."

### Your Current Approach
> *"Add this feature"* → AI rewrites everything → Previous features break

### Systematic Actions
1. Request IMPACT ANALYSIS before changes
2. Decide: extend existing module or add new one?
3. Update architecture document
4. Maintain backward compatibility

### Optimized Prompt Template: Feature Addition

```markdown
## Feature Addition Request

### Current State
The following features are COMPLETE and WORKING:
- Feature A: [description]
- Feature B: [description]

### Requested New Feature
**Description:** [What I want to add]

**User workflow for this feature:**
1. [Step 1]
2. [Step 2]

**Input/Output:**
- New input: [if any]
- New output: [if any]

---

**Request - Phase 1 (Analysis):**
Before writing any code:
1. Which existing modules need modification?
2. Do we need new modules?
3. What is the risk of breaking existing features?
4. Proposed approach (brief)

**DO NOT write code until I approve the approach.**
```

### Optimized Prompt Template: Feature Modification

```markdown
## Feature Modification Request

### Feature to Modify
**Current behavior:** [What it does now]
**Desired behavior:** [What I want it to do instead]

### Constraints
- **Must preserve:** [List functionality that must NOT change]
- **Can modify:** [What's allowed to change]

### Example
**Current:** Input X → Output Y
**Desired:** Input X → Output Z

---

**Request:**
1. Explain what changes are needed
2. Confirm what will NOT be affected
3. Implement the change
4. Provide test cases for both old and new behavior
```

### Optimized Prompt Template: Feature Removal

```markdown
## Feature Removal Request

### Feature to Remove
[Description of feature to be removed]

### Reason
[Why it's being removed]

### Cleanup Requirements
1. Remove all code related to this feature
2. Remove related configuration/parameters
3. Update any comments/documentation
4. Ensure no "dead code" remains

---

**Request:**
1. List all code sections that will be affected
2. Confirm which modules will change
3. Confirm no other features will be impacted
4. Perform the removal
5. Provide updated code with clear indication of what was removed
```

---

## PHASE 6: Project Tracking Document

### Purpose
Maintain AI context across sessions. **This is critical** — without it, AI "forgets" and suggests breaking changes.

### Your Current Pain Point
> *"After several rounds, the AI contradicts itself and forgets what we built"*

### Systematic Actions
1. Create a tracking document at project start
2. Update it after EVERY significant change
3. Include it in EVERY prompt to the AI
4. Keep a version history with working checkpoints

### Project Tracking Document Template

```markdown
# PROJECT TRACKING DOCUMENT
**Project:** [Name]
**Last Updated:** [Date]
**Current Version:** [v0.1, v0.2, etc.]

---

## 1. Project Overview
[One paragraph summary]

## 2. Current Status
**Phase:** [Requirements / Design / Development / Testing / Maintenance]
**Overall Status:** [On Track / Blocked / Complete]

### Completed Components ✅
| Component | Description | Test Status | Notes |
|-----------|-------------|-------------|-------|
| Module A | Does X | Verified | Stable |
| Module B | Does Y | Verified | Stable |

### In Progress 🔄
| Component | Description | Status | Blockers |
|-----------|-------------|--------|----------|
| Module C | Does Z | 50% | Waiting on bug fix |

### Planned 📋
| Component | Description | Priority | Dependencies |
|-----------|-------------|----------|--------------|
| Module D | Does W | High | Requires Module C |

---

## 3. Architecture Summary
```
[Input] → [Module A] → [Module B] → [Output]
```

**Module Interfaces:**
- `module_a(input) → intermediate_result`
- `module_b(intermediate_result) → output`

---

## 4. Known Issues
| ID | Description | Severity | Status |
|----|-------------|----------|--------|
| #1 | Edge case X not handled | Low | Open |
| #2 | Performance slow for large files | Medium | Investigating |

---

## 5. Change History
| Version | Date | Changes | Impact |
|---------|------|---------|--------|
| v0.1 | 2024-01-01 | Initial implementation | - |
| v0.2 | 2024-01-05 | Added feature X | Modified Module A |

---

## 6. Working Checkpoint
**Last known stable version:** v0.2
**Checkpoint code location:** [Saved in conversation/file/etc.]
**To restore:** [Instructions]

---

## 7. Important Decisions & Context
- [Decision 1]: We chose approach A over B because [reason]
- [Decision 2]: [Description]

---

## 8. Test Cases (Master List)
| ID | Module | Input | Expected Output | Status |
|----|--------|-------|-----------------|--------|
| T1 | A | X | Y | Pass |
| T2 | B | M | N | Pass |
```

### Session Initialization Prompt

Use this at the START of every new conversation:

```markdown
## Session Initialization

I'm continuing development on [Project Name].

**Attached:** Project Tracking Document (see below)

**Last session ended at:** [Brief description]

**Today's objectives:**
1. [Objective 1]
2. [Objective 2]

---

[PASTE FULL PROJECT TRACKING DOCUMENT HERE]

---

Please confirm you understand:
1. The current project state
2. What is complete and working
3. What we're working on today

Ask any clarifying questions before we proceed.
```

---

## PHASE 7: Workflow Quick Reference

### Decision Tree for Any Situation

```
Start
  │
  ├─→ "I have a new project idea"
  │      └─→ Phase 0 → Phase 1 → Phase 2 (NO CODE YET)
  │
  ├─→ "I want to start coding"
  │      └─→ Is architecture approved? 
  │            ├─ No → Go to Phase 2
  │            └─ Yes → Phase 3 (one module at a time)
  │
  ├─→ "Something isn't working"
  │      └─→ Phase 4 (structured bug report)
  │
  ├─→ "I want to add/change/remove a feature"
  │      └─→ Phase 5 (impact analysis FIRST)
  │
  ├─→ "Starting a new AI session"
  │      └─→ Phase 6 (session initialization with tracking doc)
  │
  └─→ "Any significant change completed"
         └─→ Update tracking document
```

### Red Flags — Stop and Reassess

| Warning Sign | Action |
|--------------|--------|
| AI suggests rewriting >50% of code | STOP. Request modular change instead. |
| AI asks "What did we do before?" | STOP. Provide tracking document. |
| Error in code you didn't change | STOP. AI may have introduced side effects. Rollback. |
| >3 iterations on same bug | STOP. Request root cause analysis from fresh perspective. |
| "I'll just add this one feature" | STOP. Go through Phase 5 process. |

---

## Common Scenarios & Exact Prompts

### Scenario A: "Code works but is messy"

```markdown
## Refactoring Request

**Current state:** Code works correctly but needs cleanup.

**Goals:**
1. Improve readability (better variable names, comments)
2. Improve structure (extract repeated logic into functions)
3. DO NOT change any functionality

**Working test cases (must still pass after refactoring):**
| Input | Expected Output |
|-------|-----------------|
| X | Y |
| A | B |

**Request:**
1. Show proposed refactoring plan
2. Implement changes
3. Confirm all test cases still pass
```

### Scenario B: "I don't understand the code"

```markdown
## Code Explanation Request

Please explain this code section:
```
[paste code]
```

**Format your explanation as:**
1. **Purpose:** What does this code do overall?
2. **Line-by-line breakdown:** Explain each significant line
3. **Data flow:** What data goes in? What comes out?
4. **Key concepts:** What programming concepts are used?
5. **Analogy:** Explain it in plain language as if I'm non-technical
```

### Scenario C: "Need to undo recent changes"

```markdown
## Rollback Request

**Problem:** Recent changes broke the project.

**Last working version:** [version number or description]
**What was changed since then:** [list changes]

**Request:**
1. Restore to the last working version
2. Identify what in the recent changes caused the break
3. Suggest safer approach to implement the intended changes
```

### Scenario D: "Project stalled, don't know how to proceed"

```markdown
## Project Assessment Request

This project has stalled. Please help me assess and restart.

**Attached:** [Current code / Tracking document]

**Symptoms:**
- [e.g., "Multiple bugs appearing", "Can't add features without breaking"]

**Request:**
1. Diagnose why the project is stuck
2. Identify the top 3 issues to address
3. Recommend whether to:
   - Fix current codebase (and how)
   - Partially rewrite (which parts)
   - Start over with lessons learned
4. Provide action plan with next steps
```

---

## Summary: Before/After Comparison

| Stage | ❌ Old Approach | ✅ New Approach |
|-------|----------------|-----------------|
| Start | "Make me a tool that..." | Phase 0-1-2: Scope → Requirements → Architecture |
| Develop | "Give me all the code" | Phase 3: One module at a time, verify each |
| Debug | "It doesn't work, fix it" | Phase 4: Structured bug report with context |
| Modify | "Add this feature" | Phase 5: Impact analysis first |
| Every session | Start fresh, repeat context | Phase 6: Initialize with tracking document |

---

Would you like me to create this as a document you can reference and customize? I can also elaborate on any specific phase or create tailored templates for a particular project type you have in mind.
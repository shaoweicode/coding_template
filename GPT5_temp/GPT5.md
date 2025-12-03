Below is a reusable, multi‑stage framework you can follow for almost any AI‑assisted development project, from small scripts to general‑purpose apps.

For each stage:

- I describe the **goal** and **what you should do** as a non‑professional developer.
- I give you **prompt templates** that start from your *rough, natural-language inputs* and turn them into **standardized, professional‑style outputs** from the AI.

You can copy/paste and adapt these prompts each time you start a new project.

---

## 0. Core principles (to fix your current pain points)

Before the stages, a few rules that address the common problems you mentioned:

1. **Never ask for “the whole app” in one go.**
   - Instead: build in **small slices** (1–2 features at a time), fully implement + test + clean up before adding more.

2. **Always maintain 3 small “source-of-truth” texts** (you can keep them in files like `requirements.md`, `plan.md`, `changelog.md`):
   - `requirements.md`: what the app should do (features, inputs, outputs).
   - `plan.md`: current architecture and next tasks.
   - `changelog.md`: what changed recently and what’s still broken.
   - You will periodically paste *summaries* of these into the AI so it has context.

3. **Make the AI validate feasibility and assumptions before coding.**
   - This reduces “unrealizable features” and surprises.

4. **Control the size of code changes.**
   - Ask the AI to modify **only specific functions or sections**, not rewrite everything each time.
   - Use diff‑style or “only show changed parts” when the project grows.

5. **For bugs, always provide:**
   - The **exact command** you ran.
   - The **full error trace** or output snippet.
   - What you **expected vs what happened**.
   - Any **recent changes** you made.

6. **Re-use structured prompts.**
   - Use the templates below as checklists. Over time you’ll adjust them to your style.

---

## Stage 1 – Clarify idea & feasibility (before any code)

### Goal
Turn your rough idea into:

- A clear description of the problem.
- Constraints (OS, language, allowed libraries, performance, security).
- A **feasibility check**, so the AI can tell you what is realistic and what is not.

### Your actions

1. Write your idea in your natural style: what you want, your user workflow, example inputs/outputs.
2. Note any **constraints** you know:
   - OS (Windows/Mac/Linux).
   - Programming language preference (Python? JS?).
   - Where it runs (local script, web, CLI, notebook).
   - Any limitations (no external APIs? offline only?).
3. Paste that into the following prompt and let the AI reformulate it.

### Prompt template: “Idea → feasibility & clarification”

```text
I’m a non-professional developer. I want to build something with your help.

First, I’ll paste my rough idea and user workflow. Then I want you to:

1. Rewrite my idea as a clear, concise problem statement.
2. List the main functional requirements (what the system should do) in bullet points.
3. List the non-functional requirements and constraints (OS, language, performance, security, etc.).
4. Identify any parts that might be unrealistic or ambiguous, and ask me focused clarification questions.
5. Propose 2–3 feasible implementation options (e.g., language, architecture) and recommend one for my skill level.

Here is my rough idea and workflow (in my own words):

[PASTE YOUR CURRENT STYLE DESCRIPTION HERE]
```

Use the AI’s response as the initial content for `requirements.md` (you can copy it into a file and keep evolving it).

---

## Stage 2 – Turn idea into a structured requirements spec

### Goal
Create a **compact, structured specification** that:

- Is understandable by you.
- Is detailed enough for the AI to generate consistent code.

### Your actions

1. Answer the AI’s clarification questions from Stage 1.
2. Ask the AI to produce a **single, structured spec** you can keep as `requirements.md`.
3. Keep this file updated; it’s your “contract” with the AI.

### Prompt template: “Refine into structured spec”

```text
Now that we’ve discussed the idea and you’ve asked your questions, please:

1. Produce a structured, concise requirements document for this project with these sections:
   - Overview (2–4 sentences)
   - User roles and user stories
   - Detailed functional requirements (as numbered items)
   - Non-functional requirements and constraints
   - Example inputs and outputs (with realistic examples)
   - Out-of-scope items (things we explicitly will NOT implement for now)
2. Make sure all requirements are realistic for a small project and for a non-professional developer.
3. Highlight any open questions that still need decisions.

Use clear headings and bullet points so I can copy this into a file called `requirements.md`.

Here is the latest information you have from me (including your previous summary). Please consolidate it:

[PASTE LATEST SUMMARY / ANSWERS HERE]
```

This cures the “unrealizable features” problem early.

---

## Stage 3 – High-level design & implementation plan

### Goal
Get a **high-level architecture and incremental plan** instead of jumping to full code.

### Your actions

1. Tell the AI your preferred language and environment (if not already set).
2. Ask for:
   - Overall architecture.
   - Data flow.
   - File/module structure.
   - **Milestone plan**: small steps you can implement one by one.

3. Save the resulting plan as `plan.md`.

### Prompt template: “Architecture & step-by-step plan”

```text
Using the requirements below, I want you to propose a simple, robust architecture and an incremental implementation plan suitable for a non-professional developer.

Here are the requirements:
[PASTE requirements.md OR A SUMMARY]

Constraints and preferences:
- Programming language: [your choice, e.g., Python 3.x]
- Target environment: [e.g., Windows 11, run as CLI script]
- Allowed third-party libraries: [list or “keep as few as possible”]

Please:
1. Propose a high-level architecture:
   - Main components/modules and their responsibilities
   - Data flow between components
   - Any important design decisions and trade-offs
2. Propose an initial project structure (files and folders) with a brief description for each file.
3. Create an incremental implementation plan broken into small milestones:
   - Milestone 1: [e.g., minimal end-to-end flow]
   - Milestone 2: [next feature] 
   ...etc.
4. For each milestone, list:
   - What exactly will be implemented
   - How we can test it manually (simple test plan)
   - Any risks or tricky parts

Format it clearly so I can copy it into `plan.md`.
```

---

## Stage 4 – Project setup & “first slice” of functionality

### Goal
Set up the project skeleton and implement the **smallest functional slice** that runs end-to-end.

### Your actions

1. Decide whether you want a single-file script or multi-file project (for anything non-trivial, multi-file is better).
2. Ask the AI to generate only:
   - The initial file structure.
   - Minimal code needed for the **simplest working scenario**.

3. Create the files locally and copy/paste.
4. Run them and ensure they at least start, even if they do very little.

### Prompt template: “Generate minimal skeleton & first slice”

```text
Using the architecture and plan we have in `plan.md`, I want to implement only the first small milestone as a minimal end-to-end slice.

Here is the relevant plan section:
[PASTE THE PART OF plan.md ABOUT MILESTONE 1]

Please:
1. Generate the initial project structure (files and folders) and show me:
   - The tree of files/folders
   - Which file I should run as the entry point
2. For this milestone, implement only the minimal code needed so that:
   - I can run the entry-point script.
   - It performs a very basic end-to-end flow, even if it uses placeholders or stub implementations.
3. Include comments in the code explaining the role of each main function/class.
4. Keep the code as simple and explicit as possible because I am not a professional developer.
5. Do NOT implement future milestones yet; just stubs with TODO comments.

If code becomes long, focus on the main files I need to create and run first, then we can iterate.
```

---

## Stage 5 – Testing, debugging, and fixing the first slice

This is where you previously get stuck. We’ll standardize the loop.

### Goal
Create a **repeatable debug loop**:

- Run the code.
- Gather all relevant evidence.
- Provide it to the AI in a structured way.
- Get targeted fixes, not large rewrites.

### Your actions when something fails

1. Run the script with a **specific command**.
2. When it fails or behaves incorrectly:
   - Copy the full error trace or output.
   - Describe, in simple words, what you expected vs what happened.
3. Paste these into a debug prompt and ask the AI for:
   - Root cause.
   - Minimal change to fix it.
   - Explanation you can understand.

### Prompt template: “Debug a runtime error”

```text
I tried to run the code you helped me write, and I got an error.

I will provide:
- The command I ran
- The environment
- The full error message / stack trace
- What I expected vs what actually happened
- Any recent code changes I made manually

Please:
1. Identify the most likely root cause.
2. Explain the cause in simple language so I can understand.
3. Propose a minimal fix:
   - Show only the code sections that need changing.
   - Clearly mark old vs new code, or provide a short patch/diff-style suggestion.
4. Warn me if you suspect other parts of the code might also be affected and what to test after the fix.

Environment:
[OS, Python version, etc.]

Command:
[PASTE EXACT COMMAND]

Error / output:
[PASTE FULL ERROR TRACE OR RELEVANT OUTPUT]

Expected vs actual behavior:
[YOUR DESCRIPTION]

Recent changes:
[WHAT YOU CHANGED, IF ANY]
```

### Prompt template: “Behavior is wrong but no error”

```text
The script runs without crashing, but the behavior is incorrect.

I will provide:
- The inputs I used
- The actual output
- The output I expected
- The relevant parts of the code

Please:
1. Compare the expected behavior with the actual behavior.
2. Identify which part of the logic is likely wrong.
3. Propose a minimal fix:
   - Show only the changed code segments.
4. Suggest 2–3 simple test cases I can run to confirm the fix.

Inputs used:
[PASTE]

Actual output:
[PASTE]

Expected output:
[DESCRIBE OR PASTE]

Relevant code:
[PASTE ONLY THE FUNCTIONS OR SECTIONS LIKELY INVOLVED]
```

Use this loop repeatedly. Always update `changelog.md` briefly after successful fixes (e.g., “Fixed bug where X…; tested with inputs A,B”).

---

## Stage 6 – Confirm core functionality & then refine features

Once the core works reasonably well, you’ll usually want to adjust logic, UX, or features.

### Goal
Change behavior **safely** by:

- Clearly stating what stays the same vs what changes.
- Asking for localized modifications, not total rewrites.

### Your actions

1. Describe the current behavior and the new behavior you want.
2. Tell the AI which files/functions may be touched.
3. Ask for changes that preserve existing working parts.

### Prompt template: “Modify specific features / workflow”

```text
The core functionality is working, but I want to change some behaviors.

I will provide:
- A brief description of the current behavior and workflow
- A description of the new behavior/workflow I want
- The relevant code sections

Please:
1. Restate, in your own words, the current behavior and the desired new behavior.
2. Propose a minimal set of code changes to achieve this, focusing on modifying existing functions rather than rewriting everything.
3. Show only the functions or sections that need to change, clearly indicating old vs new versions.
4. Point out any risks or side effects and suggest quick tests to verify correctness.

Current behavior:
[DESCRIBE]

Desired new behavior:
[DESCRIBE]

Relevant code:
[PASTE ONLY THE FUNCTIONS / SECTIONS INVOLVED]
```

---

## Stage 7 – Removing obsolete features and adding new ones

As your project evolves, some parts become obsolete. Mess builds up if you’re not systematic.

### Goal
Cleanly remove old logic and integrate new logic without breaking the architecture.

### Your actions

1. List outdated features and which code sections implement them.
2. List new features you want and how they relate to existing ones.
3. Ask AI to:
   - Mark and remove obsolete parts.
   - Integrate new features consistent with `requirements.md` and `plan.md`.

### Prompt template: “Clean-up obsolete logic and add new features”

```text
I need to remove some obsolete features and add new ones.

I will provide:
- A list of features/behaviors that should be removed
- A list of new features/behaviors to add
- Relevant files or code sections
- Any updated requirements/plan information

Please:
1. Analyze the impact of removing the obsolete features:
   - Which functions/files are affected?
   - What can be safely deleted vs what should be refactored?
2. Propose changes to integrate the new features:
   - Where in the existing architecture they should go.
   - How they interact with existing components.
3. Provide updated code, focusing on:
   - Removing or deprecating obsolete code paths.
   - Implementing new features in a clean, modular way.
4. Suggest an updated short summary for `requirements.md` and `plan.md` to reflect these changes.

Obsolete features to remove:
[LIST]

New features to add:
[LIST]

Relevant code and notes:
[PASTE CODE / SUMMARIES]
```

---

## Stage 8 – Refactoring & organizing a messy codebase

This targets the “disorganized codebase” pain point.

### Goal
Improve structure and readability *without changing behavior*.

### Your actions

1. Identify that the main functionality is mostly correct.
2. Tell the AI that this is a **refactor-only** step (no new features).
3. Ask for better structure, naming, separation into modules, plus docstrings and comments.

Because you can’t easily upload all files at once, you can do it module by module.

### Prompt template: “Refactor for clarity & structure (no behavior change)”

```text
The code is working, but it has become messy and hard for me to understand.

I want to refactor it for clarity and better structure, WITHOUT changing behavior.

I will provide:
- The current file or module
- A short description of what this module is supposed to do
- Any specific problems I see (e.g., long functions, duplicated code, confusing naming)

Please:
1. Analyze the current code and identify structural problems and code smells.
2. Propose a refactored version with:
   - Clear function and variable names
   - Shorter, more focused functions
   - Comments and docstrings explaining each main part
   - If appropriate, splitting into smaller helper functions or classes
3. Confirm what tests or example runs I should execute to verify that behavior did not change.
4. Keep the code at a level a non-professional can still follow.

Module description:
[DESCRIBE]

Current code:
[PASTE THE FILE OR RELEVANT PARTS]

Problems I notice:
[YOUR NOTES]
```

---

## Stage 9 – Testing strategy and test case generation

To avoid regression and catch bugs earlier, you should have at least minimal tests.

### Goal
Create manual test cases (and optionally automated tests) aligned with your requirements.

### Your actions

1. Provide your requirements (`requirements.md`) and basic knowledge of how you run the script.
2. Ask for:
   - A list of simple manual tests.
   - Optionally, actual code for automated tests (e.g., `pytest`).

### Prompt template: “Design tests from requirements”

```text
I want a simple testing strategy for this project.

I will provide:
- The current requirements (or summary)
- A brief description of how the user runs the script/app
- Any critical behaviors I’m worried about

Please:
1. From the requirements, derive a list of manual test cases:
   - For each test: Input, steps to perform, and expected output/behavior.
   - Cover normal cases, edge cases, and error cases.
2. Optionally, propose simple automated tests:
   - Assume [e.g., Python + pytest] if appropriate.
   - Show example test functions for core features.
3. Suggest a minimal routine (e.g., “run these 5 tests after each major change”) that I can realistically follow.

Requirements / summary:
[PASTE]

How I run the app:
[DESCRIBE]

Specific things I’m concerned about:
[LIST]
```

---

## Stage 10 – Documentation & user instructions

### Goal
Produce user-facing documentation and a small internal “developer notes” file.

### Your actions

1. Provide the AI with:
   - Current behavior.
   - Example runs.
   - Any quirks or limitations.
2. Ask for:
   - `README` for users.
   - Developer notes for you (architecture summary, how to modify safely).

### Prompt template: “Generate README and developer notes”

```text
The core functionalities are working, and I want good documentation.

I will provide:
- A short summary of what the tool does now
- How to install and run it
- Any limitations or caveats
- The current architecture summary (if any)

Please:
1. Write a clear `README` for end-users, including:
   - Overview
   - Requirements
   - Installation steps
   - Usage examples (with example commands and inputs/outputs)
   - Known limitations
2. Write a short `DEVELOPER_NOTES` section for me, summarizing:
   - High-level architecture (modules and responsibilities)
   - Where to add new features in the future
   - Any tricky parts of the code to be careful with

Here is the information you need:
[PASTE SUMMARY, USAGE, ARCHITECTURE INFO]
```

---

## Stage 11 – Ongoing maintenance & future changes

You’ll keep coming back later with new ideas or bug reports.

### Goal
Have a **repeatable “change request” prompt** that keeps things organized.

### Your actions

1. Maintain `requirements.md`, `plan.md`, and `changelog.md` as brief records.
2. For each new change, summarize:
   - Current state.
   - New goals.
   - Known issues.

### Prompt template: “New change request with project context”

```text
I’m returning to this existing project for new changes.

I will provide:
- A short summary of the current state from my perspective
- Excerpts from `requirements.md`, `plan.md`, and `changelog.md`
- The new changes or issues I want to address

Please:
1. Restate the current project state and objectives in your own words.
2. Analyze the requested changes:
   - What parts of the system they affect
   - Potential risks or conflicts
3. Update the implementation plan:
   - List the next 2–4 concrete tasks I should do, in order.
4. For the first task, propose a detailed plan and the code changes we’ll need.

Current state summary:
[YOUR WORDS]

Relevant requirements:
[PASTE EXCERPTS]

Current plan:
[PASTE EXCERPTS]

Changelog highlights:
[PASTE EXCERPTS]

New changes / issues:
[DESCRIBE]
```

---

## How to use this framework in practice

1. **Create 3 text files** in your project:
   - `requirements.md`
   - `plan.md`
   - `changelog.md`
2. At the start of a project:
   - Use Stage 1 → 3 prompts to fill `requirements.md` and `plan.md`.
3. For implementation:
   - Use Stage 4 (skeleton), Stage 5 (debug), Stage 6–7 (feature changes).
4. Periodically:
   - Use Stage 8 (refactor) and Stage 9 (testing).
5. When stabilizing:
   - Use Stage 10 (docs).
6. When revisiting later:
   - Use Stage 11 (change request with context).

If you’d like, you can next paste a real, rough description of one of your current projects, and I can walk you through Stages 1–3 step by step so you see this framework in action on something concrete.
# Generalized Multi-Stage Framework for AI-Assisted Programming (Non-Professional Developers)
This framework is tailored to non-professional developers using AI tools (especially Coding Agents) on Linux/WSL environments. It covers the full lifecycle of script/application development, addressing core pain points like vague requirements, disorganized code, and unresolvable bugs. Each stage includes **systematic user actions**, **industry-aligned best practices**, and **structured prompts** that transform your original simple inputs into professional, actionable instructions for AI. The framework is generalized, reusable, and prioritizes practicality and operability.

## Core Design Principles
1. **User-Centric & Non-Professional Friendly**: Avoids complex technical jargon, focuses on step-by-step actionable operations.
2.  **AI Capability Maximization**: Guides LLM/Coding Agent to output standardized, maintainable, and testable results through structured prompts.
3.  **Full Lifecycle Coverage**: Supplements missing links in your original workflow (e.g., requirements decomposition, architecture design, test planning, documentation).
4.  **Environment Adaptability**: Integrates Linux/WSL-specific considerations (e.g., dependency installation, file path standards, permission handling).
5.  **Iterative & Traceable**: Establishes document tracking (requirements list, TODOs, bug logs) to avoid development stagnation.

---

# Stage 1: Pre-Development - Requirement Standardization & Project Initialization
**Core Objective**: Convert vague conceptual ideas into clear, testable, and AI-understandable requirements; lay the foundation for organized development (solve "unrealizable features" from the source).
**User Pain Points Solved**: Ambiguous requirements leading to AI-generated code that misses the mark; no project roadmap for tracking progress.
**Deliverables**: Standardized Requirement Document, Project Initialization File (README, TODO list), Technology Stack Confirmation.

### Systematic User Actions
1.  **Conceptual Idea Refinement**: Write down your original idea (1-3 paragraphs), including core purpose, target users (yourself/team), input/output formats, and key constraints (e.g., "must run on WSL", "no network dependency", "support CSV input").
2.  **Supplement Context Constraints**: Explicitly specify the development environment (Linux/WSL), programming language preferences (e.g., Python 3.10+), and forbidden dependencies (e.g., "avoid heavy libraries like TensorFlow").
3.  **Request AI to Standardize Requirements**: Submit your raw idea and constraints to AI, and ask it to output a structured document.
4.  **Confirm & Finalize Requirements**: Review the AI's standardized requirements, propose revisions (e.g., "remove the cloud storage feature", "add local file encryption"), and lock the final version.

### Structured AI Prompt (Copy-Paste & Modify Placeholders)
```
I am a non-professional developer working on Linux/WSL. I need you to standardize my raw development idea into a professional, testable requirement document. Please follow these rules strictly:

1. Raw Idea & Constraints:
   - Core Purpose: [PASTE YOUR ORIGINAL IDEA HERE, e.g., "A script to automatically sort baby's daily photo files by date, rename them with timestamps, and classify them into 'sleep', 'feeding', 'play' folders based on keywords in the file name"]
   - Environment Constraints: Must run on Linux/WSL, programming language: [e.g., Python 3.10+]
   - Key Limitations: [e.g., "No internet access required", "Must handle Chinese file names without garbling", "Avoid installing large third-party libraries"]
   - Input/Output: Input: [e.g., Folder path containing messy photo files]; Output: [e.g., Organized folders with renamed files, a log file recording changes]

2. AI Output Requirements (Must include all of the following sections, use clear headings):
   a. Project Overview: 1-sentence summary of the project's purpose and scope.
   b. Core Functional Requirements (User Stories): List 3-5 user stories in the format "As a user, I want to [action] so that [benefit]".
   c. Non-Functional Requirements: Specify performance (e.g., "Process 1000 photos within 1 minute"), compatibility (e.g., "Supports .jpg/.png/.heic formats"), and usability (e.g., "Command-line interface with clear prompts").
   d. Acceptance Criteria: For each core function, define clear, testable success criteria (e.g., "All files in the input folder are moved to the correct category folder; no duplicate files; log file records the old and new paths of each file").
   e. Recommended Technology Stack: List dependencies/libraries suitable for Linux/WSL (avoid overkill), e.g., "Python + os.path (built-in) + pillow (for image format verification)".
```

---

# Stage 2: Architecture Design - Modularization & Framework Planning
**Core Objective**: Design a clear code structure before generating code to avoid "disorganized codebase" (the root cause of subsequent bugs and unmaintainability).
**User Pain Points Solved**: AI-generated code is a monolithic block with no separation of concerns; difficult to modify or debug later.
**Deliverables**: Modular Architecture Diagram (text-based), Module Responsibility List, Code File Structure.

### Systematic User Actions
1.  **Provide Standardized Requirements**: Submit the final requirement document from Stage 1 to AI.
2.  **Request Modular Architecture Design**: Ask AI to split the project into logical modules (e.g., "file reading module", "classification logic module", "log generation module") suitable for non-professionals.
3.  **Confirm Architecture Feasibility**: Focus on whether the modules are simple enough (avoid overly complex design patterns) and whether the file structure is clear (e.g., 1 main script + 1-2 auxiliary modules at most for small projects).

### Structured AI Prompt (Copy-Paste & Modify Placeholders)
```
Based on the following standardized requirements, design a simple, maintainable modular architecture for a non-professional developer using Linux/WSL. The project should avoid complex design patterns and ensure that the code can be easily modified later.

1. Reference Document: [PASTE THE FINAL REQUIREMENT DOCUMENT FROM STAGE 1 HERE]

2. AI Output Requirements (Must be concise and practical, avoid professional jargon):
   a. Text-Based Architecture Diagram: Use indentation to show the relationship between modules, e.g.,
      Main Script (main.py)
      ├── File Processing Module (handles reading/writing files, path operations)
      ├── Core Logic Module (implements classification/renaming rules)
      └── Log Module (generates operation logs)
   b. Module Responsibility List: For each module, explain its core functions (1-2 sentences per module) and the input/output data.
   c. File Structure: List all files needed for the project (e.g., main.py, config.py, log.py, README.md) and their respective roles.
   d. Key Function Interfaces: Define 3-5 core functions (with function names and parameter descriptions) that cross modules, e.g., "def classify_photo(file_path, keyword_map) -> str: Returns the target folder path".
```

---

# Stage 3: Code Generation - Standardized Initial Draft Output
**Core Objective**: Guide AI to generate modular, annotated, and Linux/WSL-compatible initial code based on the architecture design (solve "disorganized code" from the start).
**User Pain Points Solved**: AI's initial code lacks comments, uses non-cross-platform syntax, or does not conform to the agreed architecture.
**Deliverables**: Modular initial code files (with comments), dependency installation instructions (Linux/WSL-specific).

### Systematic User Actions
1.  **Provide Architecture Design**: Submit the architecture document from Stage 2 to AI.
2.  **Add Code Quality Constraints**: Emphasize code readability (detailed comments), Linux/WSL compatibility (e.g., use `/` for file paths instead of `\`), and error handling (e.g., "handle file not found errors gracefully").
3.  **Request Batch Code Generation**: Ask AI to output code for each file separately, with clear file names and start/end markers.

### Structured AI Prompt (Copy-Paste & Modify Placeholders)
```
Based on the following modular architecture design, generate the initial code for a Linux/WSL environment. I am a non-professional developer, so the code must be simple, well-commented, and follow Linux/WSL best practices.

1. Reference Document: [PASTE THE ARCHITECTURE DESIGN FROM STAGE 2 HERE]

2. Code Generation Rules (Strictly Follow):
   a. Language & Environment: [e.g., Python 3.10+], Linux/WSL-compatible (use posix-style file paths, avoid Windows-specific libraries like win32api).
   b. Code Style: Use consistent naming (snake_case for functions/variables), add docstrings for each function (explain purpose, parameters, return values), and inline comments for complex logic.
   c. Error Handling: Add try-except blocks for common exceptions (e.g., FileNotFoundError, PermissionError) and output user-friendly error messages (e.g., "Error: The input folder does not exist, please check the path").
   d. Modularity: Strictly follow the module division in the architecture design; do not write all code in one function.
   e. Dependency Management: List all third-party libraries used at the top of each file, and provide a separate "Dependency Installation Guide" for Linux/WSL (e.g., "Run 'pip install pillow' in the terminal").

3. AI Output Format:
   - For each file: Start with "### File: [FILE_NAME]" and end with "### End of [FILE_NAME]".
   - After all files, add a "Quick Start Guide" (Linux/WSL terminal commands) to run the script, e.g., "python3 main.py --input /home/user/photos".
```

---

# Stage 4: Testing & Debugging - Systematic Bug Identification & Resolution
**Core Objective**: Establish a standardized process for testing code, reporting bugs, and requesting AI fixes (solve "unresolvable bugs" by providing AI with complete error context).
**User Pain Points Solved**: Unable to clearly describe bugs to AI; bugs recur due to incomplete fixes; no way to verify if bugs are fully resolved.
**Deliverables**: Test Case List, Bug Fix Log, Debugged Code.

### Systematic User Actions
1.  **Create a Simple Test Case List**: Based on the acceptance criteria in Stage 1, design 3-5 test cases (including normal input, edge cases like empty folders, and invalid inputs like non-image files).
2.  **Run Code & Capture Errors**: Execute the code in WSL/Linux terminal, copy **full error information** (including traceback logs), and record unexpected outputs (e.g., "File was renamed incorrectly", "No log file generated").
3.  **Submit Bug Reports to AI**: Package test cases, error logs, and current code into a structured prompt, requesting AI to locate and fix bugs.
4.  **Verify Fixes**: Re-run the failed test cases with the modified code; repeat the process until all test cases pass.

### Structured AI Prompt for Bug Fixes (Copy-Paste & Modify Placeholders)
```
I ran the code you generated in Linux/WSL and encountered bugs. Please help me locate the root cause and provide the modified complete code. Below is the full context for debugging:

1. Test Environment: Linux/WSL, [e.g., Python 3.10.12]
2. Test Case That Failed: [e.g., Test Case 2: Input folder with empty files and Chinese-named images]
3. Full Error Log (Copied from Terminal):
   [PASTE THE COMPLETE ERROR TRACEBACK HERE, e.g., "Traceback (most recent call last): File "main.py", line 45, in <module> classify_photo(file_path) UnicodeEncodeError: 'ascii' codec can't encode characters in position 10-12: ordinal not in range(128)"]
4. Unexpected Behavior (If No Error Log But Output Is Wrong): [e.g., "The script classified all photos into 'play' folder regardless of keywords; the log file is empty"]
5. Current Code Snippet (Relevant Part): [PASTE THE CODE BLOCK RELATED TO THE BUG HERE, e.g., the classify_photo function in main.py]

6. AI Fix Requirements:
   a. Explain the root cause of the bug in 1-2 sentences (avoid complex jargon).
   b. Provide the **complete modified code file** (not just the changed lines) with comments explaining the fix.
   c. Ensure the fix is compatible with Linux/WSL (e.g., handle Chinese character encoding with UTF-8).
   d. Add a verification step: Tell me which test case to run to confirm the bug is fixed.
```

---

# Stage 5: Iterative Optimization - Feature Adjustment & Logic Refinement
**Core Objective**: Standardize the process of modifying features, adjusting logic, and adding new functions (avoid code degradation during iterations).
**User Pain Points Solved**: Adding new features breaks existing functionality; code becomes more chaotic after multiple revisions; obsolete logic accumulates.
**Deliverables**: Optimized Code, Feature Change Log.

### Systematic User Actions
1.  **Define Iteration Scope**: Clearly distinguish between "feature additions" (e.g., "add support for .gif files"), "logic adjustments" (e.g., "change the date sorting from 'file creation time' to 'photo shooting time'"), and "obsolete feature removal" (e.g., "delete the log file generation function").
2.  **Prioritize Changes**: Mark high-priority changes (must-have) and low-priority changes (nice-to-have) to avoid AI being overwhelmed.
3.  **Request AI to Modify Code**: Submit the current code, change list, and priority to AI, requiring it to maintain code modularity and compatibility.
4.  **Regression Testing**: After modification, re-run all previous test cases to ensure existing functions are not broken.

### Structured AI Prompt for Feature Optimization (Copy-Paste & Modify Placeholders)
```
I need to optimize the current code by adjusting existing features, adding new functions, and removing obsolete logic. Please modify the code while maintaining its modularity and Linux/WSL compatibility. Ensure that existing core functions are not broken.

1. Current Code Base: [PASTE THE LATEST COMPLETE CODE (e.g., main.py, core.py) HERE, or specify file names if too long]
2. Change List (With Priority: High/Low):
   a. [High] Feature Adjustment: [e.g., "Change the photo classification logic from keyword matching to file metadata (EXIF) shooting time"]
   b. [High] New Feature: [e.g., "Add a function to compress images after classification, with a compression ratio parameter (default 80%)"]
   c. [Low] Obsolete Feature Removal: [e.g., "Delete the 'file duplication check' function, as it is not needed anymore"]
3. Constraints: Do not modify the existing file structure; keep comments updated; ensure all changes are compatible with Linux/WSL.

4. AI Output Requirements:
   a. Feature Change Log: List each change with a brief explanation of how it was implemented.
   b. Complete Modified Code: Output all updated files (marked with "### File: [NAME]"), highlighting modified lines with comments (e.g., "# Modified: Changed classification logic to EXIF time").
   c. Regression Test Guide: List 2-3 key test cases to verify that existing functions are still working.
```

---

# Stage 6: Code Refactoring - Simplification & Standardization
**Core Objective**: Clean up redundant code, improve readability, and reduce maintenance costs (solve "disorganized codebase" accumulated from iterations).
**User Pain Points Solved**: Code has duplicate logic; functions are too long; variable names are confusing; difficult to understand or modify later.
**Deliverables**: Refactored Code, Refactoring Log.

### Systematic User Actions
1.  **Identify Refactoring Needs**: Based on your understanding, list code problems (e.g., "the same file path processing logic is used in 3 functions", "variable names like 'x' and 'temp' are unclear").
2.  **Request AI to Refactor**: Submit the current code and refactoring needs to AI, requiring it to maintain functionality while improving code quality.
3.  **Confirm Functionality Unchanged**: Run all test cases again to ensure refactoring does not introduce new bugs (this is critical for non-professionals).

### Structured AI Prompt for Code Refactoring (Copy-Paste & Modify Placeholders)
```
I am a non-professional developer. The current code works correctly but has issues like redundant logic and unclear naming. Please refactor the code to make it simpler, more readable, and maintainable. **Ensure that the core functionality remains 100% unchanged** (no behavior modifications).

1. Code to Refactor: [PASTE THE LATEST COMPLETE CODE OR SPECIFY FILE NAMES HERE]
2. Known Code Issues (For Reference):
   a. Redundant logic: [e.g., "The file path validation logic is duplicated in 2 functions"]
   b. Naming issues: [e.g., "Variable names like 'data' and 'func' are too vague"]
   c. Readability issues: [e.g., "Some functions are over 50 lines long, with no clear separation of steps"]
3. Refactoring Rules (Strictly Follow):
   a. No functional changes: The refactored code must produce the same output as the original for all test cases.
   b. Linux/WSL compatibility: Keep all Linux-specific syntax (e.g., path separators, permission handling).
   c. Simplify without over-engineering: Avoid complex design patterns; keep the code accessible to non-professionals.
   d. Keep comments: Update existing comments to match refactored code; add comments for complex logic.

4. AI Output Requirements:
   a. Refactoring Log: List each refactoring action (e.g., "Extracted duplicate path validation into a separate function: validate_file_path()") and explain its purpose.
   b. Refactored Complete Code: Output all files with clear structure and updated comments.
   c. Verification Confirmation: A brief statement confirming that functionality remains unchanged and that the user only needs to re-run existing test cases.
```

---

# Stage 7: Delivery & Documentation - Finalization & Knowledge Preservation
**Core Objective**: Complete the project delivery with user-friendly documentation, enabling future reuse and maintenance (solve "forgot how to use the code" after a long time).
**User Pain Points Solved**: No documentation for how to run the code; unable to remember the purpose of functions; cannot troubleshoot simple issues independently later.
**Deliverables**: Final Code Package, User Guide (README.md), Maintenance Notes.

### Systematic User Actions
1.  **Request AI to Generate Documentation**: Submit the final code to AI, asking for a Linux/WSL-specific user guide and maintenance notes.
2.  **Customize Documentation**: Add personal notes (e.g., "I use this script to sort baby photos every Sunday", "The input folder is usually /home/user/baby_photos").
3.  **Archive Project**: Organize all files (code, documentation, test cases) into a single folder on Linux/WSL, with a clear naming convention (e.g., "baby_photo_sorter_v1.0").

### Structured AI Prompt for Documentation (Copy-Paste & Modify Placeholders)
```
Based on the final code of the project, generate a comprehensive, user-friendly documentation package for a non-professional developer using Linux/WSL. The documentation should enable me to run, maintain, and troubleshoot the code independently in the future.

1. Final Project Code: [PASTE THE FINAL CODE FILES OR SPECIFY FILE NAMES HERE]
2. Project Background: [e.g., "This is a script to sort and compress baby's daily photos, used personally on WSL Ubuntu 22.04"]

3. AI Output Requirements (Must Include All of the Following in Markdown Format):
   a. README.md:
      - Project Overview: Purpose, core features, and Linux/WSL environment requirements.
      - Quick Start: Step-by-step terminal commands (installation dependencies → run script → example usage).
      - Parameter Explanation: If the script has command-line parameters, list them clearly (e.g., "--input: Input folder path (required)").
      - Common Issues & Fixes: Top 3 Linux/WSL-specific issues (e.g., "Permission denied: Run 'chmod +x main.py' to add execution permission").
   b. Maintenance Notes:
      - Core Function Introduction: Explain the purpose of each key function (1 sentence per function).
      - Future Modification Tips: Suggestions for common changes (e.g., "To add a new photo category, modify the 'CATEGORY_KEYWORDS' dictionary in core.py").
```

---

# Stage 8: Post-Delivery - Maintenance & Iteration Tracking
**Core Objective**: Establish a lightweight process for future updates and bug fixes (ensure the project can evolve with your needs).
**User Pain Points Solved**: No record of past changes; unable to track version updates; difficult to resume development after a long break.
**Deliverables**: Version Log, Iteration Plan Template.

### Systematic User Actions
1.  **Maintain a Version Log**: Ask AI to generate a simple version log template, and record each update (e.g., "v1.0: Initial release; v1.1: Added image compression; v1.2: Fixed Chinese character encoding bug").
2.  **Track Future Needs**: Record new ideas (e.g., "Add support for video files") in the TODO section of the README.md.
3.  **Reuse the Framework**: For new projects, repeat Stages 1-7, reusing the prompts and processes from this framework.

### Structured AI Prompt for Version Log (Copy-Paste & Modify Placeholders)
```
Generate a simple, maintainable version log template for my project, suitable for a non-professional developer. The log should track updates, bug fixes, and compatibility changes for Linux/WSL.

1. Project Name: [e.g., Baby Photo Sorter]
2. Current Version: [e.g., v1.0]
3. Past Changes (For Initial Log): [e.g., "v1.0: Initial release with photo sorting, renaming, and classification functions; v1.1: Added image compression and fixed Chinese character encoding bug"]

4. AI Output Requirements:
   a. A Markdown-formatted version log (named "CHANGELOG.md") with columns for Version, Date, Changes, and Linux/WSL Compatibility Notes.
   b. A simple template for future updates (so I can fill in new changes easily).
```

---

# Framework Application Tips for Non-Professional Developers
1.  **File Management**: Store all project files in a single folder on WSL (e.g., `/home/[your_username]/projects/[project_name]`) to avoid path confusion.
2.  **Prompt Reuse**: Save the structured prompts from each stage as a text file (e.g., `ai_prompts.txt`) in your project folder for quick access in future projects.
3.  **AI Tool Selection**: For Linux/WSL, use Coding Agents that support terminal integration (e.g., GitHub Copilot CLI, CodeLlama) to directly run AI-generated commands.
4.  **Incremental Development**: For complex projects, split them into small sub-projects and apply this framework to each sub-project sequentially.

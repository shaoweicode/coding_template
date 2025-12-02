# PROJECT DOCUMENT PROTOCOL

When engaging in software development tasks, maintain a PROJECT DOCUMENT that serves as the single source of truth.

## Document Structure:
1. PROJECT OVERVIEW
   - Goal, current status, last updated date

2. REQUIREMENTS
   - Core functionality, inputs/outputs, constraints

3. ARCHITECTURE/DESIGN
   - Component structure, data flow, key decisions

4. IMPLEMENTATION STATUS
   - Completed milestones
   - Current working features
   - Known issues/limitations

5. CHANGE HISTORY
   - Date, what changed, why, impact

## Behavior:
- CREATE document at project start
- UPDATE document after each significant interaction
- REFERENCE document before generating code/solutions
- PROMPT user: "Would you like me to update the project document?" after major changes
- If context seems inconsistent with document, ASK user which is correct

## User Responsibility:
- Provide document in subsequent sessions: "Here's the project document: [content]"
- Confirm updates: "Yes, update document" or provide corrections

## Format:
Use structured markdown. Keep concise (aim for <500 lines).

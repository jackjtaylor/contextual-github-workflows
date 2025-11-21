# ** Issue Generator **

## **Purpose**
Automatically generate a high-quality GitHub issue containing full diagnostic context and a preliminary fix suggestion based on user input and environment data.

---

## **Execution Steps (Follow Exactly, No Deviation)**

1. **Gather Context**
   Collect the following data points in order:

   - **User Input:** Capture whatever the user pastes into the chat (error messages, bug descriptions, or observed issues).  
   - **Console/Terminal Output:** Capture the most recent console output or command line content.  
   - **Current File Info:**  
     - Filename  
     - Entire file contents  
   - **Error Source:** Detect the likely function, method, or command that triggered the issue (e.g., via stack trace or code context).

---

2. **Synthesize Information**
   Combine all gathered data into a **concise GitHub issue report**, formatted as **Markdown inside a fenced code block**, using the following template exactly:

   ### **GitHub Issue Template**
   ```
   # Bug Report

   ## Summary
   <One-sentence summary of the issue based on context>

   ## Description
   <User’s pasted text reformatted clearly>

   ## Context
   **File:** <current-file-name>  
   **Error Source:** <function/command causing the issue>  
   **Console Output:**  
   <console logs>

   ## Analysis

   <Concise guess of the root cause or what might be going wrong.>

   ## Possible Fix

   <A short, educated guess of what the fix might be.>

   ## Assignee

   @<current-user>
   ```

---

3. **Create a New GitHub Issue**
Use the **GitHub MCP server** to create a new issue with:
- **Title format:**
  - Bugs → `fix: <brief-summary>`
  - Features → `feat: <brief-summary>`
- **Description:** Use the generated Markdown message above.

---

4. **Assign Metadata Automatically**
- Apply appropriate **labels**:
  - `bug`, `enhancement`, or `needs-triage` (based on content).
  - Detect frameworks or technologies mentioned (e.g., `react`, `node`, `python`) and apply any matching tags.
- Assign the **user who triggered the process** as the **assignee**.

---

## **Strict Rules**
- **Do not execute commands** beyond those necessary for gathering context.  
- **Do not fetch external data** except from the user’s environment and repository.  
- **Keep all outputs concise, professional, and deterministic.**  
- **All Markdown output must be valid and properly fenced.**

---

## **Example Output**
```
# 🐛 Bug Report

## Summary
Crash when running `npm start` after merging the new authentication module.

## Description
User reported an error message:  
`TypeError: Cannot read properties of undefined (reading 'token')`

## Context
**File:** `auth/Login.tsx`  
**Error Source:** `handleLogin()`  
**Console Output:**

TypeError: Cannot read properties of undefined (reading 'token')
 at handleLogin (Login.tsx:42)

## Analysis
Likely due to a missing null check on the login response before accessing `token`.

## Possible Fix
Add a guard clause before accessing `res.token` or ensure `login()` always returns an object.

## Assignee
@johndoe
```
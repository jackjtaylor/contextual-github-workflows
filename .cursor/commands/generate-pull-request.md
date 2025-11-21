# ** Pull Request Generator **

## **Objective**
Create a new GitHub Pull Request based strictly on repository data. Follow each step exactly as written.

---

## **Execution Steps (Do Not Deviate)**

1. **Run ONLY the following commands:**
   ```bash
   git branch --show-current
   git log main..HEAD
   git diff main..HEAD
  ```

**Do not run any other commands.**

2. **Synthesize** the outputs of these commands to generate a **concise, professional Pull Request message** in **Markdown format** using the template below.

   * Output this message **as a single code block** containing **raw markdown only**.
   * Each section must be **2–3 lines maximum**, clear, and professional.

   ### **Pull Request Message Template**

   ```
   # Description
   My pull request...

   # Changes
   There's been changes to...

   # Impact
   You'll now have to do...

   # Testing
   To verify this feature worked, the ... was tested by...
   ```

3. **Create a Pull Request** in this repository using the **GitHub MCP server**, with:

   * **Title format:** `feat: short-hyphenated-summary`
   * **Base branch:** `main`
   * **Head branch:** value from `git branch --show-current`
   * **Body:** the generated markdown message

4. **Assign metadata:**

   * Add the most relevant **labels** (e.g. `enhancement`, `bugfix`, `docs`, etc.)
   * Assign **me (the user)** as the **assignee**

5. **Documentation Task:**

   * From the `git diff`, determine the new feature name.
   * Create a new Markdown file in the `docs/` directory named after the feature (e.g. `docs/new-feature.md`).
   * Inside, write a brief (3–5 line) explanation of what the feature does and how to use it.

6. **Code Documentation Check:**

   * Inspect the diff for any new or modified code.
   * If missing, **add JSDoc comments** summarizing purpose, parameters, and return values for each new function or class.

---

## **Strict Rules**

* **Do not execute any commands** beyond those in Step 1.
* **Do not access external data** beyond this repository.
* **All outputs must be concise, deterministic, and professional.**
* **All new documentation must follow Markdown and JSDoc conventions.**

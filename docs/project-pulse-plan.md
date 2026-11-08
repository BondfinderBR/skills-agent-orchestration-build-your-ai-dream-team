# Project Pulse Dashboard Plan

## Summary

Build Project Pulse as a lightweight static dashboard using HTML, CSS, and JSON. Contributors should be able to scan project ownership, status, recent activity, priority or risk, and a short summary. Use the existing Copilot CLI agent team to plan, design, implement, and validate the work.

The JSON must contain a top-level `projects` array. Each project includes `name`, `owner`, `status`, `recentActivity`, and `priority`. The brief asks for contributor-friendly summaries but does not define a summary data field, so present a short summary in the UI using the required fields without changing the specified data shape.

## Implementation steps

### 1. Agree on design and shared contracts

- **Designer:** Define the dashboard's information hierarchy, card layout, typography, spacing, status and priority treatment, accessibility, and responsive behavior. Share proposed markup hooks with the Coder.
- **Coder:** Confirm the data shape and expected HTML/CSS hooks before implementation.
- **Files:** No implementation files; this is a design handoff.
- **Dependency:** Complete the shared design and class-name contract before integrating the page and styles.

### 2. Create project data and launch configuration

- **Coder — `app/project-data.json`:** Create representative project records using only the required fields: `name`, `owner`, `status`, `recentActivity`, and `priority`.
- **Coder — `.vscode/launch.json`:** Create strict JSON with no comments and a configuration named **Run Project Pulse Dashboard**. Use `python3 -m http.server 5500`, serve from `app/`, and configure `serverReadyAction` to open `http://localhost:%s/index.html`.
- **Dependency:** Both files follow requirements already defined in the brief and Step 3; they can be created independently of one another.

### 3. Implement and integrate the dashboard

- **Coder — `app/index.html`:** Create the page with the exact title **Project Pulse**. Reference `styles.css` and `project-data.json`, then render visible `.project-card` elements showing project name, owner, status, recent activity, and priority. Include the contributor-friendly summary in the UI without adding a summary property to the JSON.
- **Coder — `app/styles.css`:** Apply the Designer's recommendations. Include `.dashboard` and `.project-card` selectors, responsive layout, readable spacing, and polished card styling with `border-radius` and `box-shadow`.
- **Dependencies:** Use the shared design contract and exact JSON field names. The markup and CSS hooks must agree, and the page's data-loading behavior must work when served over HTTP.

### 4. Validate the integrated app

- **Coder:** Validate the data and launch JSON, inspect the required files and selectors, and run the dashboard using the launch configuration.
- **Orchestrator:** Review the integrated result against the brief, coordinate fixes if needed, and report validation outcomes and remaining issues.
- **Dependency:** Run the end-to-end checks after all assigned files are implemented and integrated.

## Responsibilities and file assignments

| Owner | File(s) | Responsibility |
| --- | --- | --- |
| Designer | No implementation-file ownership | Guide visual design, accessibility, information hierarchy, and responsive behavior; hand recommendations to the Coder without overlapping implementation edits. |
| Coder | `app/project-data.json` | Create the top-level `projects` array with the five required fields per project. |
| Coder | `.vscode/launch.json` | Create the named strict-JSON launch configuration, serve from `app/`, and open `index.html`. |
| Coder | `app/index.html` | Create the titled dashboard, load the data, render project cards and required fields, and include a contributor-friendly summary. |
| Coder | `app/styles.css` | Implement the agreed visual treatment, responsive layout, accessibility, and required CSS selectors. |
| Orchestrator | No implementation-file ownership | Coordinate specialists, keep file ownership clear, sequence dependent work, integrate results, and report the outcome. |

## Dependencies and parallel work

1. **Sequential:** Designer and Coder agree on the design, class names, and data contract before implementation integration.
2. **Parallel:** Once requirements are clear, the Coder can create `app/project-data.json` and `.vscode/launch.json` independently. The Designer can finalize visual recommendations in parallel.
3. **Sequential integration:** The Coder connects `app/index.html` to the JSON and stylesheet, ensuring that the agreed class names and required data fields match.
4. **Sequential validation:** Run the complete checks after the four assigned files are integrated.

Keep the Designer advisory-only and the Coder as the sole editor of implementation files to avoid conflicting edits. HTML and CSS can be drafted in parallel only after their shared selectors and markup expectations are agreed.

## Validation expectations

- Confirm these files exist:
  - `app/index.html`
  - `app/styles.css`
  - `app/project-data.json`
  - `.vscode/launch.json`
- Parse both JSON files:
  - `python3 -m json.tool app/project-data.json`
  - `python3 -m json.tool .vscode/launch.json`
- Check that `app/index.html` has the exact **Project Pulse** title, references `styles.css` and `project-data.json`, renders `.project-card` elements, and shows project name, owner, status, recent activity, priority, and a short contributor-friendly summary.
- Check that each project in the top-level `projects` array contains `name`, `owner`, `status`, `recentActivity`, and `priority`.
- Check that `app/styles.css` includes `.dashboard`, `.project-card`, `border-radius`, and `box-shadow`, with readable, responsive, accessible styling.
- Check that `.vscode/launch.json` has no comments, defines **Run Project Pulse Dashboard**, serves from `app/`, uses `python3 -m http.server 5500`, and opens `http://localhost:%s/index.html`.
- Run **Run Project Pulse Dashboard** in VS Code and confirm the browser shows the dashboard from `app/index.html`, not a directory listing. Stop the preview server after checking.
- Use the Step 3 workflow checks for required files, phrases, and JSON parsing; perform the launch test separately.

## Risks and open questions

- The brief does not provide production project records or a fixed status/priority vocabulary; use clearly representative sample data unless approved values are supplied.
- The short summary is requested by the brief but is not part of the specified JSON schema; display it in the UI without changing the data shape.
- Verify that the launch configuration opens the app page, not a directory listing, and that data loading works when served over HTTP.

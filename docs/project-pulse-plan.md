# Project Pulse implementation plan

## Summary

Mona's Project Pulse dashboard is a small static frontend that helps contributors quickly understand which projects are active, who owns each one, the current status, recent activity, and priority or risk. The work should be split into a clear planning and implementation flow led by the Orchestrator, with the Designer focused on frontend experience and the Coder focused on production-ready static app files and launch support.

## Objective

Build a polished dashboard that:

- renders a project overview from a structured data source
- presents each project as a clear card with owner, status, recent activity, and priority
- uses readable layout, spacing, badges, and visual hierarchy
- runs via a dedicated VS Code launch configuration that opens the app in the browser without showing a directory listing

## File assignments

### 1. HTML shell and dashboard structure
- Primary file: `app/index.html`
- Responsibility: create the semantic dashboard layout, project card placeholders, and data-binding hooks for the project list.
- Notes: include a top-level dashboard container and deterministic selectors such as `.dashboard` and `.project-card` so the verification workflow can check for them.

### 2. Styles and visual polish
- Primary file: `app/styles.css`
- Responsibility: implement spacing, typography, color treatments, badges, card styling, shadows, and rounded corners to create a polished dashboard frontend.
- Notes: the Designer should own the CSS decisions to ensure the page reads like a clear, contributor-friendly control center.

### 3. Project data model
- Primary file: `app/project-data.json`
- Responsibility: define a top-level `projects` array with each project including `name`, `owner`, `status`, `recentActivity`, and `priority`.
- Notes: use realistic sample data that supports the dashboard cards and status highlighting.

### 4. Launch configuration
- Primary file: `.vscode/launch.json`
- Responsibility: create a deterministic launch configuration named `Run Project Pulse Dashboard` that serves the `app` directory and opens `index.html`.
- Notes: use strict JSON with no comments and keep the `cwd` set to `${workspaceFolder}/app`.

## Designer responsibilities

The Designer should own the user-facing quality of the dashboard, including:

- information hierarchy for project cards and summaries
- accessibility and readable contrast
- responsive layout and spacing decisions
- visual polish through borders, shadows, badges, and consistent card treatment
- ensuring the first load clearly reads as a Project Pulse dashboard rather than a generic page

The Designer should work primarily in `app/styles.css` and review the structure in `app/index.html` to ensure the content and styling align.

## Coder responsibilities

The Coder should own the implementation mechanics and technical correctness, including:

- building the dashboard markup and script-ready structure in `app/index.html`
- wiring the project data file into the page structure
- creating the static asset data model in `app/project-data.json`
- adding `.vscode/launch.json` for running the app in VS Code
- validating file correctness and ensuring the app opens from the proper directory and index page

## Dependencies

1. The data shape in `app/project-data.json` must be defined before the HTML structure is finalized so the project cards can render consistently.
2. The HTML structure in `app/index.html` must be in place before the Designer can tune layout and card styling in `app/styles.css`.
3. The launch configuration in `.vscode/launch.json` depends on the final app structure and should be created once the dashboard files are stable.
4. The final dashboard validation depends on the presence of the HTML, CSS, data file, and launch configuration all being in sync.

## Parallel work decisions

Work can proceed in parallel when the file scopes do not overlap:

- The Designer can begin styling work in `app/styles.css` once the dashboard scaffold exists in `app/index.html`, even while the Coder refines the data model in `app/project-data.json`.
- The Coder can prepare `.vscode/launch.json` after the app files are in a stable state, while the Designer continues styling refinements.

Work must remain sequential when dependencies exist:

- finalize the project data before finalizing the rendered HTML structure
- finalize the HTML structure before finalizing the visual styling pass
- finalize the app files before generating the launch configuration for the dashboard

## Validation expectations

Validation should confirm the following:

- `app/index.html` contains a dashboard structure, project cards, and a `.dashboard` selector.
- `app/styles.css` includes polished styling such as `border-radius`, `box-shadow`, and `.project-card` rules.
- `app/project-data.json` contains a top-level `projects` array with `name`, `owner`, `status`, `recentActivity`, and `priority` values.
- `.vscode/launch.json` is valid JSON, serves from the `app` directory, and opens `index.html`.
- The final app reads as a coherent Project Pulse dashboard rather than a plain file listing or skeletal page.

## Suggested implementation order

1. Confirm data requirements and page structure.
2. Create the project data model in `app/project-data.json`.
3. Build the dashboard shell in `app/index.html`.
4. Style the dashboard in `app/styles.css`.
5. Create the VS Code launch configuration in `.vscode/launch.json`.
6. Validate the visual and technical requirements.

## Open questions

- Are there any specific branding or color preferences for Mona's dashboard?
- Should the dashboard include interactive filtering or remain a static presentation only?
- Are there any required sample project names or statuses that should match a business scenario?

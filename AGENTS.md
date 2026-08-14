# AGENTS.md - Permanent Project Rules

## Product Overview
Single-Page Web Application: **Antigravity IDE** — A modern, browser-based integrated development environment with file explorer, tabbed code editor, interactive terminal console, AI assistant pane, code execution, and file management.

## Hard Constraints
1. **Single File Structure**: All HTML markup, inline CSS (`<style>`), and vanilla JavaScript (`<script>`) MUST reside strictly inside a single `index.html` file.
2. **No External Dependencies**: 
   - No UI frameworks (e.g., React, Vue, Svelte, Tailwind, Bootstrap).
   - No build tools, npm scripts, bundlers, or package managers.
   - No external CDN scripts or stylesheet links.
3. **Execution Environment**: Must run hosted on a local live web server (e.g., Antigravity live preview server), NOT via double-clicking `file://` URLs.
4. **Data Source & Persistence**: Default workspace files hardcoded in initialization data and all user edits/files persisted in browser `localStorage`.
5. **Specification Directory**: All project specification documents MUST be maintained inside the `spec/` directory (`spec/requirements.md`, `spec/design.md`, `spec/tasks.md`).

## Workflow Rules
- Always consult and adhere strictly to `spec/requirements.md`, `spec/design.md`, and `spec/tasks.md`.
- Implementation proceeds strictly in phases as outlined in `spec/tasks.md`.

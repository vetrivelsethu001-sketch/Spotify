# Implementation Tasks Plan — Antigravity IDE

## Phase 1: Visible IDE Layout & File Explorer Scaffold

- [ ] Task 1.1: Build HTML5 IDE skeleton (`index.html`) featuring header toolbar, left file explorer sidebar, central editor container with line numbers and tab bar, bottom terminal panel, right AI assistant panel, and dark VS Code inspired inline CSS styles. (Implements: REQ-01, REQ-05)
- [ ] Task 1.2: Define default in-memory `workspace` JavaScript object containing initial sample files (`main.js`, `styles.css`, `index.html`, `README.md`). (Implements: REQ-01, REQ-15)
- [ ] Task 1.3: Implement dynamic rendering of the file explorer sidebar with extension icons and file selection handlers. (Implements: REQ-01, REQ-02)

*Phase 1 Verifiable Milestone*: Open `index.html` in browser via live server. A fully styled Antigravity IDE interface is visible with header toolbar, populated file explorer sidebar, code editor workspace, bottom terminal console, and AI assistant panel.

---

## Phase 2: Code Editor Engine, Tab Management & Workspace Persistence

- [ ] Task 2.1: Implement tab bar rendering, active tab switching, and tab close (`×`) handlers. (Implements: REQ-02, REQ-05)
- [ ] Task 2.2: Bind editor text input events to update active file content, synchronize line numbers, support `Tab` indenting, and toggle unsaved dirty indicators (`•`). (Implements: REQ-06)
- [ ] Task 2.3: Implement `New File` button logic to create new workspace files and `Delete File` buttons to remove files and update open tabs. (Implements: REQ-03, REQ-04)
- [ ] Task 2.4: Implement file saving (`Ctrl+S` or `Save` button) and `localStorage` serialization & startup deserialization (`"antigravity_ide_workspace_v1"`). (Implements: REQ-07, REQ-14, REQ-15)

*Phase 2 Verifiable Milestone*: Open `index.html`. Select files, edit code with line numbers, create/delete files, open/close tabs, press `Ctrl+S` to save, and refresh browser to confirm all workspace files and open tabs persist via `localStorage`.

---

## Phase 3: Interactive Terminal Code Execution, AI Assistant & Search

- [ ] Task 3.1: Build JavaScript execution engine capturing `console.log`, `console.error`, and evaluation return values, streaming timestamped output entries to the bottom Terminal Console panel. (Implements: REQ-08, REQ-09, REQ-10)
- [ ] Task 3.2: Implement Antigravity AI Assistant panel logic with quick actions ("Explain Code", "Refactor", "Fix Bugs", "Add Tests"), interactive prompt responses, and direct code insertion into active editor. (Implements: REQ-11, REQ-12)
- [ ] Task 3.3: Implement global search input filtering workspace files in real time. (Implements: REQ-13)

*Phase 3 Verifiable Milestone*: Open `index.html`. Click `Run Code` to execute JavaScript in the Terminal console, test REPL input, trigger AI code assistant actions, and use global search to filter files across the IDE workspace.

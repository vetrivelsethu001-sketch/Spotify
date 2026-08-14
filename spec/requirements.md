# Software Requirements Specification — Antigravity IDE

## 1. Overview
This document specifies the functional requirements for **Antigravity IDE**, a single-page web-based integrated development environment, formatted using the EARS (Easy Approach to Requirements Syntax) framework.

---

## 2. Functional Requirements

### 2.1 File Explorer & Workspace Management
- **REQ-01**: WHEN the application initializes, THE SYSTEM SHALL display a file explorer sidebar presenting all files in the virtual workspace with file extension icons.
- **REQ-02**: WHEN a user selects a file from the explorer sidebar, THE SYSTEM SHALL open that file in the editor pane and activate its corresponding tab.
- **REQ-03**: WHEN a user clicks the "New File" button, THE SYSTEM SHALL prompt for a filename, create the file with default boilerplate template, and select it in the file explorer.
- **REQ-04**: WHEN a user clicks the delete button for a workspace file, THE SYSTEM SHALL remove the file from the workspace tree and close any active tab associated with it.

### 2.2 Tabbed Code Editor
- **REQ-05**: WHEN multiple files are opened, THE SYSTEM SHALL display tab controls across the top of the editor pane displaying filenames, file status, and close tab (`×`) controls.
- **REQ-06**: WHEN a user edits text within the code editor textarea/content area, THE SYSTEM SHALL update line numbers, character counts, and mark the file tab with an unsaved indicator.
- **REQ-07**: WHEN a user presses `Ctrl+S` or clicks the "Save" button, THE SYSTEM SHALL save all modified file contents to the in-memory workspace and remove unsaved indicators.

### 2.3 Interactive Terminal Console & Code Execution
- **REQ-08**: WHEN a user clicks the "Run Code" button, THE SYSTEM SHALL evaluate the active file's JavaScript code in a safe evaluation container and capture standard output, errors, and return values.
- **REQ-09**: WHEN code output or execution errors occur, THE SYSTEM SHALL render colored logs with timestamps in the bottom Terminal Console panel.
- **REQ-10**: WHEN a user clicks the "Clear Terminal" button, THE SYSTEM SHALL clear all rendered console output lines.

### 2.4 AI Assistant Panel (Antigravity Assistant)
- **REQ-11**: WHEN a user inputs a prompt or clicks an AI quick-action button ("Explain Code", "Refactor Code", "Fix Bugs"), THE SYSTEM SHALL analyze the active editor file context and generate structured AI code responses and explanations.
- **REQ-12**: WHEN a user clicks "Apply Code Suggestion" in the AI assistant panel, THE SYSTEM SHALL insert or replace the suggested code directly into the active editor file.

### 2.5 Global Search
- **REQ-13**: WHEN a user enters text into the global workspace search bar, THE SYSTEM SHALL highlight search query matches across all workspace files and filter file tree results.

### 2.6 State Persistence
- **REQ-14**: WHEN files are created, edited, saved, or deleted, THE SYSTEM SHALL serialize the entire workspace file tree and active tab states into `localStorage`.
- **REQ-15**: WHEN the application reloads, THE SYSTEM SHALL deserialize workspace state from `localStorage` or populate default sample project files (`main.js`, `styles.css`, `index.html`, `README.md`) if no stored state is present.

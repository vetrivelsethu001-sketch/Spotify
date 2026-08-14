# System Design Specification — Antigravity IDE

## 1. Document Architecture (index.html Structure)

The single `index.html` application is structured into three primary visual columns and a bottom terminal pane:

### 1.1 Document Head
- Standard HTML5 meta tags (`charset`, `viewport`).
- Document title: `Antigravity IDE — Browser Code Studio`.
- Google Fonts embed (`Fira Code` for editor code font & `Outfit` for UI text font).
- Inline `<style>` block containing dark VS Code / Antigravity IDE design system rules, flexbox grid layouts, custom scrollbar styling, tab styles, and line-number code alignment.

### 1.2 Document Layout
- **Top Command Header (`<header>`)**:
  - Logo branding: Antigravity IDE icon with pulsing AI status glow.
  - Action Toolbar: `New File`, `Save (Ctrl+S)`, `Run Code (▶)`, `Clear Terminal`, `Toggle AI Assistant`, and Global Search Bar.
- **Main Workspace Area (`<main>`)**:
  - **Left Sidebar (File Explorer `#sidebar`)**:
    - Section header: `EXPLORER` with `+ New File` button.
    - File tree list (`#file-tree`) displaying file icons, filename labels, dirty state indicators, and delete buttons.
  - **Center Column (Code Studio Pane `#editor-container`)**:
    - **Tab Bar (`#tab-bar`)**: Horizontal list of open file tabs with active state highlighting and close (`×`) buttons.
    - **Editor Wrapper (`#editor-wrapper`)**:
      - Line Numbers Column (`#line-numbers`): Synchronized vertical line numbering.
      - Code Input Area (`#code-editor`): Monospace code editor textarea supporting tab indentation (`Tab`), real-time line count updates, and unsaved status tracking.
    - **Terminal Console Panel (`#terminal-panel`)**:
      - Header: Terminal title, execution status indicator, and `Clear` button.
      - Output Log Stream (`#terminal-logs`): Formatted execution log entries (Info, Success, Error, Output).
      - Interactive Prompt (`#terminal-input`): REPL input line for manual command execution.
  - **Right Sidebar (Antigravity AI Assistant Pane `#ai-panel`)**:
    - Assistant Header: AI Agent status ("Ready", "Analyzing Code").
    - Action Shortcuts: `⚡ Explain Code`, `🛠️ Refactor`, `🐛 Fix Bugs`, `🧪 Add Tests`.
    - AI Chat Stream (`#ai-chat`): Interactive conversation stream displaying assistant suggestions and markdown code blocks.
    - AI Input Box (`#ai-input`) and `Send` button.

---

## 2. Workspace Data Model

Workspace files and active editor session states are managed in global memory:

```javascript
const workspace = {
  files: {
    "main.js": {
      id: "main.js",
      name: "main.js",
      language: "javascript",
      content: "// Welcome to Antigravity IDE\nfunction calculateSum(a, b) {\n  return a + b;\n}\n\nconsole.log('Calculation Result:', calculateSum(42, 58));",
      isModified: false
    },
    "styles.css": {
      id: "styles.css",
      name: "styles.css",
      language: "css",
      content: "/* Custom App Styling */\nbody {\n  background-color: #0d1117;\n  color: #c9d1d9;\n  font-family: 'Fira Code', monospace;\n}",
      isModified: false
    },
    "index.html": {
      id: "index.html",
      name: "index.html",
      language: "html",
      content: "<!DOCTYPE html>\n<html>\n<head>\n  <title>Sample App</title>\n</head>\n<body>\n  <h1>Hello Antigravity</h1>\n</body>\n</html>",
      isModified: false
    },
    "README.md": {
      id: "README.md",
      name: "README.md",
      language: "markdown",
      content: "# Antigravity IDE\n\nModern browser-based IDE with real-time JavaScript code execution, tabbed editor, and AI assistant.",
      isModified: false
    }
  },
  openFileIds: ["main.js", "styles.css"],
  activeFileId: "main.js"
};
```

---

## 3. Storage and Restoration Logic

### 3.1 LocalStorage Key
- Key: `"antigravity_ide_workspace_v1"`

### 3.2 Serialization
- On file create, edit, save, or delete:
  `localStorage.setItem("antigravity_ide_workspace_v1", JSON.stringify(workspace))`

### 3.3 Restoration
- On application boot:
  1. Retrieve `localStorage.getItem("antigravity_ide_workspace_v1")`.
  2. If valid JSON, hydrate `workspace.files`, `workspace.openFileIds`, and `workspace.activeFileId`.
  3. If null or corrupted, initialize with default pre-populated sample files (`main.js`, `styles.css`, `index.html`, `README.md`).
  4. Render file tree, tabs, line numbers, code content, and terminal initial state.

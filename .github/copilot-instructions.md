# Focus Tree
Focus Tree is a zero-dependency vanilla JavaScript web application for task management, action tracking, and habit building. It uses VanillaJS, HTML, CSS, and IndexedDB with custom elements and shadow DOM.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively
- **No build process required** - Focus Tree is a static web application with zero dependencies
- **Running the application:**
  - `cd /path/to/focustree`
  - `python3 -m http.server 8080` - starts HTTP server in under 5 seconds
  - Open browser to `http://localhost:8080`
  - Application loads in under 2 seconds
- **Installing dependencies:**
  - `npm install` - completes instantly (no dependencies to install)
  - **DO NOT RUN** `npm test` - this script has an infinite loop and will hang indefinitely

## Application Architecture
- **Technology Stack:** VanillaJS, HTML, CSS, IndexedDB
- **Zero Dependencies:** No build tools, frameworks, or external libraries
- **File Structure:**
  - `index.html` - Main entry point
  - `script/` - JavaScript modules (main.js, taskBase.js, taskNode.js, taskView.js, consts.js)
  - `style/` - CSS modules with modular imports
  - `assets/` - Images and tutorial data
- **Browser Requirements:** Modern browser with Custom Elements, Shadow DOM, and IndexedDB support

## Validation Scenarios
Always validate changes by running through these complete user scenarios:

### Core Task Management Flow
1. **Create a new task:**
   - Click the "✚" button (top left)
   - Verify new task appears with "[Task]" and "[note]" placeholder text
   - Verify task has state dropdown with options: ready, active, pause, done

2. **Edit task content:**
   - Click "✎" button next to task name, edit the name
   - Click "✎" button next to task note, edit the description
   - Verify changes persist after editing

3. **Task state management:**
   - Change task state using dropdown (ready → active → pause → done)
   - Click "👁" (focus) button to open focus dialog
   - In focus dialog, click "✓" (done) or "⏸" (pause) buttons
   - Verify state changes are reflected in the main view

4. **Subtask management:**
   - Click "+" button in Subtasks section to add child tasks
   - Verify subtasks can be expanded/collapsed
   - Test nested subtask creation (subtasks of subtasks)

### Export/Import Validation
1. **Export functionality:**
   - Click "🡅" (export) button (top right)
   - Verify `tasks.json` file downloads automatically
   - Open downloaded file and verify it contains valid JSON with task data

2. **Focus mode workflow:**
   - Click "👁" (eye) button on any task
   - Verify focus dialog opens with task name as header
   - Test both "✓" (done) and "⏸" (pause) buttons to close dialog
   - Verify task state updates correctly after focus mode

### Browser Data Persistence
1. **Data persistence test:**
   - Create several tasks with different states
   - Refresh browser page (`F5` or `Ctrl+R`)
   - Verify all tasks and their states persist correctly
   - Data is stored in browser's IndexedDB

## Known Issues and Limitations
- **npm test is broken** - DO NOT RUN `npm test` as it creates an infinite loop
- **Import functionality** - Import does not overwrite existing tasks (work in progress)
- **No build tools** - No linting, formatting, or compilation tools configured
- **No CI/CD** - No GitHub Actions or automated testing workflows

## Troubleshooting
- **Application won't load:** Ensure you're serving via HTTP server, not opening file:// directly
- **Tasks not persisting:** Check browser's IndexedDB is enabled and not in private mode
- **Focus dialog not working:** Verify task has proper state configuration
- **Export not downloading:** Check browser's download permissions and popup blockers

## Development Guidelines
- **Code style:** Follow existing vanilla JavaScript patterns with custom elements
- **Testing:** Always run through complete validation scenarios above after making changes
- **File modifications:** Edit source files directly - no build step required
- **Browser testing:** Test in modern browsers (Chrome, Firefox, Safari, Edge)

## Common File Locations
```
Repository root structure:
├── .github/
├── .gitignore
├── LICENSE
├── README.md
├── assets/
│   ├── FocusTree.png
│   ├── FocusTree_screenshot.png
│   └── tutorial.js
├── favicon.ico
├── index.html
├── package.json
├── script/
│   ├── consts.js
│   ├── main.js
│   ├── taskBase.js
│   ├── taskNode.js
│   └── taskView.js
└── style/
    ├── dialog.css
    ├── main.css
    ├── menu.css
    ├── reset.css
    ├── select.css
    ├── shared.css
    ├── task.css
    └── theme.css
```

## Key Constants and Configuration
- **Task States:** ready, active, pause, done (defined in script/consts.js)
- **Custom Elements:** task-node, task-base, task-view (defined in script/)
- **Database:** Uses IndexedDB with store name "taskbase" version 1
- **Tutorial:** Automatically loads on first application run (assets/tutorial.js)
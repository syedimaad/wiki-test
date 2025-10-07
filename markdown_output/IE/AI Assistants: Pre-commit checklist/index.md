### Recommended

- Ask Copilot to **review the diff or files changed**\
  `Does this ViewController contain too much logic?`

  `Can this function be simplified or made more testable?`

  `Is this adhering to SOLID principles?`

  `Suggest improvements based on Clean Architecture.`

- Run `SwiftLint` and `SwiftFormat`

- Ask Copilot to **check for naming consistency**\
  `Are the variable and function names clear, consistent, and self-explanatory?`

- Ask Copilot to check for UI modification on BG thread\
  `Identify any specific instances of UI code running on a background thread?`

### Optional/Good-To-Have

- Add or review documentation for all **public functions**, protocols,
  and classes. Suggest `MARK: -` section headers in large files.

  `Document this function and group this file into MARK: sections for readability.`

- Confirm logic is **testable and not in the UI layer**

- Ensure no TODOs, debug prints, or unnecessary comments

- Ask Copilot to **generate a commit message**\
  `Generate a commit message summary for this diff.`

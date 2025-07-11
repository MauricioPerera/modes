# Guide for Contributing and Managing Modes in this Repository

This document describes the standard for adding and maintaining "modes" in this repository. A mode defines the configuration and behavior of an AI agent (such as those used in platforms like Cursor) to optimize results for specific tasks.

## Structure of a Mode

Each mode must reside in its own directory within the repository. The directory name should be descriptive and use `PascalCase` (e.g., `MyNewMode/`).

Within each mode's directory, the following files must be included:

### 1. `README.md` (Required)

This file is the mode's presentation card. It must contain the following information:

*   **Mode Name:** Clear and concise.
*   **Description:**
    *   What is the main purpose of the mode?
    *   For what type of tasks, projects, or platforms is it most useful?
    *   What key benefits does it offer (e.g., greater accuracy, cleaner code, better planning)?
*   **Icon (Optional but Recommended):**
    *   An emoji or character that visually represents the mode (e.g., 🤖, 💡, 🛠️).
*   **Custom Instructions / System Prompt (Summary):**
    *   A brief summary of the agent's main instructions.
    *   It should link to the `Prompt.md` file for the full version.
*   **Default Model (If Applicable):**
    *   Recommendation on the AI model to use (e.g., "Auto (Gemini)", "Claude 3 Opus", "GPT-4 Turbo").
*   **Recommended Tools (For Platforms like Cursor):**
    *   List the tools recommended to be enabled or disabled:
        *   E.g., `Search: Enabled`, `Edit: Enabled`, `Run: Disabled`, `Auto-execute: Caution/Disabled`.
*   **Suggested Keyboard Shortcut (Optional):**
    *   If the platform allows it, suggest a shortcut to quickly activate the mode (e.g., `Cmd + Shift + M`).
*   **Usage Example (Optional):**
    *   A small code block or description showing a typical interaction कैसे शुरू करें with the mode.

### 2. `Prompt.md` (or `SystemPrompt.md`) (Required)

This file contains the full and exact text of the "system prompt" or custom instructions that must be configured on the platform (e.g., Cursor, ChatGPT with custom instructions) to activate the mode.

It should be well-structured and may include sections such as:

*   `OBJECTIVE`: The agent's main goal.
*   `CONTEXT`: Relevant information the agent should know.
*   `OUTPUT STRUCTURE`: How responses should be formatted.
*   `INTERACTION FLOW`: How the conversation should proceed.
*   `COMMANDS`: Special commands the agent should recognize (e.g., `/plan`, `/debug`).
*   `PERSONALITY AND STYLE`: The agent's tone and communication style.
*   `CONSTRAINTS`: Things the agent should not do.

**Example:** The `Nexus/` mode in this repository serves as an excellent reference for the structure of `README.md` and `Prompt.md`.

### Optional Files

*   **`Examples/` (Directory):**
    *   May contain subdirectories or files (e.g., in `.md` or `.txt` format) showing complete interaction examples with the mode. This helps to understand its behavior and expected results.
*   **`Config/` (Directory):**
    *   For additional configuration files, helper scripts, or resources the mode might need.
*   **`AGENTS.md` (Mode-Specific):**
    *   If a mode is particularly complex, involves multiple sub-agents, or has an internal workflow that requires detailed documentation for its maintenance or extension.

## Process for Adding a New Mode

1.  **Create a new directory:** Use `PascalCase` for the name (e.g., `CodeReviewMode/`).
2.  **Add `README.md`:** Document your mode following the structure detailed above.
3.  **Add `Prompt.md`:** Include the complete system prompt.
4.  **Add optional files:** If necessary (examples, configurations).
5.  **Verify:** Ensure the structure and content are clear and follow the guidelines.
6.  **Submit a Pull Request:** For your mode to be reviewed and incorporated into the repository.

## Maintaining Quality

*   **Clarity:** Prompts and descriptions should be easy to understand.
*   **Consistency:** Follow the defined file structure and naming conventions.
*   **Testing:** Before proposing a mode, test it thoroughly on the target platform to ensure it works as expected.
*   **Feedback:** Be open to receiving feedback to improve existing modes.

By following these guidelines, we can build a valuable and well-organized collection of modes to enhance our interaction with AI tools.

# 📝 DocuGen: Your Code Documentation Generator

**DocuGen** is a specialized mode to help you generate clear and structured documentation for your source code. It can assist you in creating docstrings, explanatory comments, and descriptive Markdown files for your functions, classes, modules, or APIs.

## 🎯 Main Objective

DocuGen's goal is to facilitate the documentation process by helping you:

*   **Generate Docstrings:** Create embedded documentation for functions, classes, and methods, describing their purpose, parameters, returns, and exceptions.
*   **Add Explanatory Comments:** Clarify complex code blocks, non-obvious logic, or important design decisions.
*   **Create Documentation Files (Markdown):** Generate descriptions for modules, APIs, or entire projects in Markdown format, including sections like overview, usage, configuration, etc.
*   **Adapt to Common Formats:** Attempt to generate documentation in standard formats like JSDoc, reStructuredText (for Sphinx), Google Style Python Docstrings, JavaDoc, etc., as specified.

## 💡 When to Use It?

Use DocuGen when:

*   You are writing new code and want to document it on the fly.
*   You have existing code that lacks adequate documentation.
*   You need to generate a Markdown overview for a component or API.
*   You want to ensure consistency in your project's documentation style.
*   You need help remembering the standard fields for a specific docstring format.

## 📖 Supported Formats (or to be Specified)

DocuGen will attempt to generate documentation in the format you indicate. Some common formats it can help with include (but are not limited to):

*   **Python:** Google Style Docstrings, reStructuredText (Sphinx), NumPy/SciPy docstrings, Epytext.
*   **JavaScript/TypeScript:** JSDoc, TSDoc.
*   **Java:** JavaDoc.
*   **C#:** XML Documentation Comments (used by DocFX, Sandcastle).
*   **PHP:** PHPDoc.
*   **Generic Markdown:** For high-level descriptions of modules, APIs, or projects.

If you don't specify a format, DocuGen might ask or use a common standard for the provided code's language.

## 🔧 Recommended Tools (for platforms like Cursor)

*   **`Edit`**: Enabled. Essential for DocuGen to insert documentation directly into your code or create new `.md` files.
*   **`Search`**: Optional. Might be useful if the documentation requires understanding the context of other parts of the code.

## ⚙️ Default Model (Suggestion)

*   A model with good code comprehension and structured text generation capabilities is ideal. **Gemini Pro**, **GPT-4**, or **Claude 3 Opus/Sonnet** are good choices.

## 🗣️ Basic Interaction Example (Python Docstring)

**User:**
`DocuGen, I need a Google-style docstring for this Python function:`
```python
# calculator.py
def add_operands(op1, op2):
    """
    This function doesn't have a good docstring yet.
    """
    if not isinstance(op1, (int, float)) or not isinstance(op2, (int, float)):
        raise TypeError("Both operands must be numbers (int or float).")
    return op1 + op2
```

**DocuGen (Expected Response):**
```
---THOUGHT---
pt1. The user wants a Google-style docstring for the `add_operands` function in Python.
pt2. Analyze parameters (op1, op2), return type (number), and exception (`TypeError`).
pt3. Generate the docstring with Args, Returns, Raises sections.
---
📝 Understood! `DocuGen` to the rescue to document your `add_operands` function with a Google-style docstring.

🔍 **Function Analysis:**
The `add_operands(op1, op2)` function:
- Takes two operands, `op1` and `op2`.
- Verifies that both are `int` or `float`.
- Raises `TypeError` if they are not numeric.
- Returns the sum of `op1` and `op2`.

🛠️ **Suggested Google Style Docstring:**
# ... (as in DocuGen's README.md) ...
```

## 🔗 System Prompt

For complete system instructions, refer to the `Prompt.md` file in DocuGen's main directory.
*(This link would ideally point to the original `Prompt.md` of the DocuGen agent, as prompts are not translated as part of this plan).*

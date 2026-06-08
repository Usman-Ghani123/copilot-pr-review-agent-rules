# Copilot PR Review Agent Rules

This repository defines the coding standards that GitHub Copilot automatically enforces during pull request reviews. When a PR is opened, Copilot reads these rules and flags any violations as review comments — acting as a consistent, automated code reviewer on every PR.

## What Gets Reviewed

Copilot checks every pull request against the following areas:

**Imports**
- Use `import` instead of `require`
- All imports at the top of the file, libraries before local files
- Use package aliases instead of long relative paths (`../../`)
- Single quotes and semicolons on all import statements

**TypeScript Standards**
- Explicit types on variables, function parameters, and return values
- `const` for constants, `let` for mutable variables
- Strict equality (`===`) over loose equality (`==`)
- Boolean values in conditionals, not string comparisons

**Naming & Structure**
- camelCase for variables, functions, files, and folders
- No spelling mistakes in identifiers
- Plural names for arrays
- Short iterator names (`i`, `j`, `k`) in loops

**Code Cleanliness**
- No unused variables or imports
- No unnecessary `console.log` statements
- No template literals unless string interpolation is actually needed
- Separate comma-chained declarations into individual lines
- Max one blank line between code blocks; no trailing whitespace

**Functions & Logic**
- Break long functions into smaller ones
- Arrow functions for one-liners
- No more than 3 lines of logic outside a named function
- Utility functions for repeated logic

**Testing (Playwright / Spec Files)**
- Single quotes in test descriptions
- Max 3 assertions per test block
- Assertions inside `catch` blocks; assertion functions prefixed with `verify`
- Single parameterized assertion function for state variants (visible/hidden, enabled/disabled)
- Follow Page Object Model structure

**Security**
- No credentials, tokens, or secrets for production environments committed
- Test environment credentials under `config/` are permitted

---

## How It Works

The rules live in `.github/copilot-instructions.md`. GitHub Copilot reads this file automatically when reviewing PRs in this repository (or any repository that references these instructions). No extra configuration or workflow setup is needed — Copilot picks up the file by convention.

Each rule includes a brief explanation and, where helpful, a ✅ / ❌ code example so Copilot can give precise, actionable feedback rather than generic warnings.

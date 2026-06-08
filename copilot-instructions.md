# Copilot PR Review Instructions

Use `import` instead of `require`.

Place all import statements at the top of the file.

Libraries should be imported before local files.

Use package/library names in import paths instead of long relative paths like "../../".

```typescript
// ✅ Good
import { Page } from '@playwright/test';
import * as browserActions from '@aiexpert-utilsUI/browser_actions.utils';
import * as browserAssertions from '@aiexpert-utilsUI/browser_assertions.utils';
import { responseActionBarLocators } from '@aiexpert-ui/conversation_flow/response_action_bar/locators';

// ❌ Bad
import { Page } from '@playwright/test';
import * as browserActions from '../../../utils/ui/browser_actions.utils';
import * as browserAssertions from '../../shared/utils/ui/browser_assertions.utils';
import { responseActionBarLocators } from '../../main/ui/conversation_flow/response_action_bar/locators';
```

Use single quotes for import paths and keep quote usage consistent.

Add semicolons to import statements, variable declarations, function calls, and return statements.

Remove Unused variables and imports

Use camelCase for variable, function, file, and folder names.

There should be no spelling mistakes in variable, function, file, and folder names.

Use `const` for constants and `let` for mutable variables.

Add correct TypeScript data types for variables, function parameters, and return types.

```typescript
// ✅ Good
const feedbackText: string = 'Positive feedback added!';
let isVisible: boolean;

async function verifyButtonIsVisible(page: Page, isVisible: boolean): Promise<void> { ... }

// ❌ Bad
const feedbackText = 'Positive feedback added!';
let isVisible;

async function verifyButtonIsVisible(page, isVisible) { ... }
```

Separate comma-separated declarations into individual lines.

```typescript
// ✅ Good
const feedbackText: string = 'Positive feedback added!';
const interactionNumber: number = 1;

// ❌ Bad
const feedbackText: string = 'Positive feedback added!', interactionNumber: number = 1;
```

Remove unnecessary blank lines and whitespace:

- No more than one consecutive blank line between code blocks
- No trailing whitespace at the end of lines
- No extra blank lines at the end of functions or code blocks
- Functions should end with a closing brace immediately followed by one blank line (if there's more code after)
- One blank line between functions or test blocks
- No blank lines immediately after opening braces or before closing braces
- Remove any excessive whitespace or spacing inconsistencies

Use spaces around operators and after commas (for example: `slice(0, 10)`, not `slice(0,10)`).

Use plural naming for arrays.

Separate variables and functions with a blank line.

Use short, common iterator names (i, j, k) in loops.

Declare a variable for array length instead of using array.length in loops.

Break down long functions into smaller ones.

Use arrow functions for one-liners.

```typescript
// ✅ Good
getCopyButton: (page: Page, interactionNumber: number): Locator =>
  page.getByTestId(`interaction__copy-btn--interaction-${interactionNumber - 1}`).locator('button');

// ❌ Bad
function getCopyButton(page: Page, interactionNumber: number): Locator {
  return page.getByTestId(`interaction__copy-btn--interaction-${interactionNumber - 1}`).locator('button');
}
```

Use strict equality (`===`) instead of loose equality (`==`).

```typescript
// ✅ Good
if (type === 'like') { ... }

// ❌ Bad
if (type == 'like') { ... }
```

Do not create separate assertion functions for each element state. Use a single parameterized function (with a boolean or suitable parameter) to assert states such as enabled/disabled, clickable/unclickable, visible/hidden, etc.

Place assertions inside `catch` blocks, and start assertion function names with "verify".

There should be no more than three assertions in a test block in a spec file.

Use single quotes for test descriptions.

```typescript
// ✅ Good
test('Verify that copy button is visible and displays toast message when clicked', async ({ authenticatedPage }) => { ... });

// ❌ Bad
test("Verify that copy button is visible and displays toast message when clicked", async ({ authenticatedPage }) => { ... });
```

Do not use template literals unless string interpolation is needed.

```typescript
// ✅ Good
const errorMessage = 'Feedback submission failed';
const logMessage = `Feedback Button ${index} - ${type}`;

// ❌ Bad
const errorMessage = `Feedback submission failed`;
```

Store lengthy strings in variables for better readability.

Extract parts of URLs into constants for easier maintenance.

Use 2-space indentation across all files.

Use boolean values instead of string matching for conditionals.

```typescript
// ✅ Good
if (isVisible) {
  await browserAssertions.expectVisible(locator, 'Button is visible');
}

// ❌ Bad
if (isVisible === 'true') {
  await browserAssertions.expectVisible(locator, 'Button is visible');
}
```

Do not write more than 3 lines of logic outside a named function or method.

Avoid unnecessary console.log statements.

Do not commit credentials, tokens, or secrets related to production environments.

✅ Credentials for test environments stored under the `config/` folder are allowed.

Use utility functions for repeated logic (e.g., browserActions, browserAssertions).

Follow the Page Object Model structure for UI components and pages.

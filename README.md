# Project Configuration

This document outlines the configuration steps in your project.

## Prettier

[**Prettier**](https://prettier.io/) is an opinionated code formatter that helps maintain consistent code style across
your project.

### Installation

To install Prettier, run the following command:

```bash
  npm install prettier --save-dev
```

### Configuration

Create a Prettier configuration file named `.prettierrc` in the root directory of your project.

```json
{
  "printWidth": 120,
  "singleQuote": true,
  "useTabs": false,
  "tabWidth": 2,
  "semi": true,
  "bracketSpacing": true,
  "quoteProps": "as-needed",
  "bracketSameLine": true,
  "arrowParens": "always",
  "trailingComma": "es5",
  "htmlWhitespaceSensitivity": "ignore"
}
```

### Configuration Properties

Here's a breakdown of each property in the `.prettierrc` file and its purpose:

- ### `printWidth`

  **Value:** `120`.
  ####
  **Description:** Specifies the maximum line width before code is wrapped.
  ####
  **Rationale:** This value helps maintain readability by preventing lines from becoming too long and requiring
  horizontal scrolling.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleFunction = (arg1, arg2, arg3, arg4, arg5, arg6) => {
    // Function body...
  };
  ```

  ```js
  // ✔️ Good
  const exampleFunction = (
    arg1,
    arg2,
    arg3,
    arg4,
    arg5,
    arg6
  ) => {
    // Function body...
  };
  ```

- ### `singleQuote`

  **Value:** `true`.
  ####
  **Description:** Determines whether to use single quotes (`true`) or double quotes (`false`) for string literals.
  ####
  **Rationale:** By choosing single quotes, we adhere to a common convention in JavaScript and maintain consistency
  throughout the codebase.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const greeting = "Hello, world!";
  ```

  ```js
  // ✔️ Good
  const greeting = 'Hello, world!';
  ```

- ### `useTabs`

  **Value:** `false`.
  ####
  **Description:** Specifies whether to use tabs (`true`) or spaces (`false`) for indentation.
  ####
  **Rationale:** Opting for spaces instead of tabs promotes consistent alignment across different editors and platforms.
  ####
  **Example**:
  ```js
  // ❌ Bad
  function exampleFunction() {
    // Indented code with tab
  }
  ```

  ```js
  // ✔️ Good
  function exampleFunction() {
    // Indented code with spaces
  }
  ```

- ### `tabWidth`

  **Value:** `2`.
  ####
  **Description:** Defines the number of spaces or tabs to be used for each indentation level.
  ####
  **Rationale:** A value of `2` spaces strikes a balance between preserving indentation depth and minimizing horizontal
  space usage.
  ####
  **Example**:
  ```js
  // ❌ Bad
  function exampleFunction() {
      // Indented code with tab (4 spaces)
  }
  ```

  ```js
  // ✔️ Good
  function exampleFunction() {
    // Indented code with tab (2 spaces)
  }
  ```

- ### `semi`

  **Value:** `true`.
  ####
  **Description:** Determines whether to add semicolons at the end of statements.
  ####
  **Rationale:** Setting it to true enforces the use of semicolons, which aids in preventing potential issues with
  automatic semicolon insertion.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleVariable = 42
  ```

  ```js
  // ✔️ Good
  const exampleVariable = 42;
  ```

- ### `bracketSpacing`

  **Value:** `true`.
  ####
  **Description:** Specifies whether to add spaces inside object literals.
  ####
  **Rationale:** Enabling this property by setting it to `true` enhances code readability by adding spaces between
  brackets and their contents.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleObject = {key: 'value'};
  ```

  ```js
  // ✔️ Good
  const exampleObject = { key: 'value' };
  ```

- ### `quoteProps`

  **Value:** `"as-needed"`.
  ####
  **Description:** Determines when to quote object literal property names.
  ####
  **Rationale:** The `"as-needed"` setting quotes property names only when necessary, reducing visual clutter and
  improving code readability.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleObject = { 'key': 123, 'another-key': 'value' };
  ```

  ```js
  // ✔️ Good
  const exampleObject = { key: 123, 'another-key': 'value' };
  ```

- ### `bracketSameLine`

  **Value:** `true`.
  ####
  **Description:** Put the `>` of a multi-line HTML element at the end of the last line instead
  of being alone on the next line (does not apply to self-closing elements).
  ####
  **Rationale:** The selected value is **optional**. It depends on the code style of your team.
  ####
  **Example**:
  ```html
  // ✔️ Good
  <button
    class="some-class"
    id="some-id"
    (click)="handleClick($event)"
  >
    Click Here
  </button>
  ```

  ```html
  // ✔️ Also good
  <button
    class="some-class"
    id="some-id"
    (click)="handleClick($event)">
    Click Here
  </button>
  ```

- ### `arrowParens`

  **Value:** `"always"`.
  ####
  **Description:** Controls the use of parentheses around arrow function parameters.
  ####
  **Rationale:** At first glance, avoiding parentheses may look like a better choice because of less visual noise.
  However, when Prettier removes parentheses, it becomes harder to add type annotations, extra arguments or default
  values as well as making other changes. Consistent use of parentheses provides a better developer experience when
  editing real codebases, which justifies the default value for the option.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleFunction = arg => {
    // Function body...
  };
  ```

  ```js
  // ❌ Bad
  exampleArray.forEach(item => /* Some actions */);
  ```

  ```js
  // ✔️ Good
  const exampleFunction = (arg) => {
    // Function body...
  };
  ```

  ```js
  // ✔️ Good
  exampleArray.forEach((item) => /* Some actions */);
  ```

  ####
  **Disadvantages:** The `"arrowParens": "always"` configuration wraps the body of a callback function in parentheses,
  it can be seen as a potential drawback when it comes to the ESLint
  rule [`no-return-assign`](https://eslint.org/docs/rules/no-return-assign).

  The only two options for this rule are to allow when parenthesis are _present_ or _disallow always_.

  ```js
  // 😀 Before formatting
  exampleArray.forEach((item) => this.someField = item);
  ```

  ```js
  // 😒 After formatting
  exampleArray.forEach((item) => (this.someField = item));
  ```

- ### `trailingComma`

  **Value:** `"es5"`.
  ####
  **Description:** Specifies the use of trailing commas in multiline lists.
  ####
  **Rationale:** Including trailing commas in multiline lists offers several benefits. Firstly, it simplifies adding or
  removing items from the list, as each item is followed by a comma, making the version control diffs cleaner and more
  manageable. Secondly, it helps prevent formatting-related merge conflicts when multiple developers work on the same
  codebase concurrently. Finally, it promotes a consistent style and avoids debates over whether to include or omit the
  trailing comma in different scenarios. By adopting the `"es5"` setting, we ensure compatibility with ECMAScript 5 and
  leverage these advantages to enhance the maintainability and collaboration aspects of our codebase.
  ####
  **Example**:
  ```js
  // ❌ Bad
  const exampleArray = [
    'item1',
    'item2',
    'item3'
  ];
  ```

  ```js
  // ✔️ Good
  const exampleArray = [
    'item1',
    'item2',
    'item3',
  ];
  ```

- ### `htmlWhitespaceSensitivity`

  **Value:** `"ignore"`.
  ####
  **Description:** Defines how HTML whitespace is handled.
  ####
  **Rationale:** With "ignore", whitespace in HTML files is disregarded, avoiding unnecessary diffs and promoting
  consistency.
  ####
  **Example**:
  ```html
  // ❌ Bad
  <span class="dolorum atque aspernatur">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci autem eligendi iste iusto necessitatibus non quaerat, quibusdam ratione saepe tenetur!</span>
  ```

  ```html
  // ❌ Bad - When we use the "css" or "strict" values of this property
  <span class="dolorum atque aspernatur"
    >Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci autem eligendi iste iusto necessitatibus non
    quaerat, quibusdam ratione saepe tenetur!</span
  >
  ```

  ```html
  // ❌ Bad
  <span *ngIf="condition" class="dolorum atque aspernatur" [class.some-class]="condition" (click)="someClickAction()">
    Lorem ipsum dolor sit amet
  </span>
  ```

  ```js
  // ✔️ Good
  <span class="dolorum atque aspernatur">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci autem eligendi iste iusto necessitatibus non
    quaerat, quibusdam ratione saepe tenetur!
  </span>
  ```

  ```html
  // ✔️ Good
  <span
    *ngIf="condition"
    class="dolorum atque aspernatur"
    [class.some-class]="condition"
    (click)="someClickAction()">
    Lorem ipsum dolor sit amet
  </span>
  ```

By customizing these properties in the `.prettierrc` file, you establish a consistent code formatting style across
your project, enhancing readability and maintainability. Feel free to modify these settings based on your specific
project requirements and personal preferences.

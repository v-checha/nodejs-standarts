# 📖 Coding Conventions

In our project, we prioritize code quality and consistency by utilizing linters. Specifically, we employ ESLint with the `@typescript-eslint/recommended` and `prettier/recommended` configurations. This setup enforces strict adherence to our coding standards and best practices.

**Benefits:**

* **Consistency**: Ensures uniform code style across the codebase.
* **Error Prevention**: Detects potential issues early in the development process.
* **Readability**: Makes the code easier to read and maintain.
* **Team Collaboration**: Facilitates smoother collaboration by maintaining a consistent code style.

**Implementation:**

* **ESLint**: Configured with `@typescript-eslint/recommended` to enforce TypeScript-specific rules.
* **Prettier**: Integrated with ESLint via `prettier/recommended` to auto-format code according to our style guide.

This approach helps us maintain high-quality, consistent, and error-free code, ensuring our project is robust and maintainable.

Here's how you can configure your project to use `@typescript-eslint/recommended`, `prettier/recommended` for code conventions:

**1. Package Installation:**

*   Install the required packages using npm or yarn:

    ```bash
    npm install --save-dev @typescript-eslint/eslint eslint eslint-plugin-prettier prettier
    ```



**2. ESLint Configuration (.eslintrc.js or .eslintrc.json):**

* Create a file named `.eslintrc.js` (or `.eslintrc.json`) in your project root directory.
*   Add the following configuration to extend the recommended rules from `@typescript-eslint` and `prettier`:

    JavaScript

    ```javascript
    module.exports = {
      extends: [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "prettier",
      ],
      plugins: ["@typescript-eslint", "prettier"],
      rules: {
        // Add any additional ESLint rules you want to customize here
      },
    };
    ```

    Use code with caution.content\_copy
* Explanation:
  * `extends`: This property specifies the ESLint configurations to inherit from.
    * `eslint:recommended`: Includes recommended ESLint rules.
    * `plugin:@typescript-eslint/recommended`: Adds recommended rules for TypeScript.
    * `prettier`: Disables conflicting ESLint formatting rules in favor of Prettier.
  * `plugins`: This property defines the ESLint plugins used in your project.
    * `@typescript-eslint`: Enables TypeScript specific linting rules.
    * `prettier`: Integrates Prettier with ESLint.
  * `rules`: This property allows you to override or customize specific ESLint rules. You can leave it empty initially and add custom rules as needed.

**3. Prettier Configuration (.prettierrc or prettier.config.js):**

* You can optionally create a separate Prettier configuration file named `.prettierrc` (or `prettier.config.js`) in your project root directory.
* Since you're extending `prettier/recommended`, Prettier already has a good default configuration.
* You can customize specific formatting options if needed, following the Prettier documentation: [https://prettier.io/docs/en/](https://prettier.io/docs/en/)

**Running ESLint:**

*   Once configured, you can run ESLint to lint your code:

    ```bash
    npx eslint .  # Lint all files in the current directory
    ```

**Benefits:**

* This setup enforces consistent code style and catches potential issues using ESLint.
* Prettier automatically formats your code based on its configuration, ensuring uniformity.
* The recommended configurations from `@typescript-eslint` and `prettier` provide a solid foundation for well-formatted and type-safe TypeScript code.

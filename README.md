# eslint, prettier and typescript configuration for react projects

These are my personal rules that I use in my projects.

## Usage

1.Install peer dependencies:

```bash
npx install-peerdeps --dev @aelshinawy/eslint-prettier-react
```

2.Tell your project to use @aelshinawy/eslint-prettier-react. For that,

- in `package.json` add or edit (if already exists) `eslintConfig` field:

```json
"eslintConfig": {
    "extends": [
      "@aelshinawy/eslint-prettier-react"
    ]
  }
```

- OR create `.eslintrc` file with the following content:

```json
{
  "extends": ["@aelshinawy/eslint-prettier-react"]
}
```

3.To lint your code run:

```bash
npx eslint .
```

OR if you'd like fixable errors to be fixed automatically, run:

```bash
npx eslint . --fix
```

**NOTE:** This config works only for TypeScript projects, e.g., your project must include `.tsconfig.json` file. If it doesn't, you can easily initialize it by running:

```bash
npx tsc --init
```

## How To Override Default Config

Add your custom ESLint or Prettier rules directly in `.eslintrc` or `package.json` file under `"rules"` (for ESLint) or `"prettier/prettier"` (for Prettier) field:

```json
{
  "extends": ["@aelshinawy/eslint-prettier-react"],
  "rules": {
    "@typescript-eslint/ban-ts-comment": "off",
    "prettier/prettier": [
      "error",
      {
        "endOfLine": "auto"
      }
    ]
  }
}
```

## Integration with VSCode

1. Uninstall or disable any previously installed prettier extensions.

2. Install (if haven't already) [ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

3. Edit VSCode settings by pressing CMD + SHIFT + P on Mac (or Ctrl + SHIFT + P on Windows), type `settings` and choose `Preferences: Open Settings (JSON)`. Edit or add the following settings:

```json
// Format a file on save
"editor.formatOnSave": true,
// show eslint icon at bottom toolbar
"eslint.alwaysShowStatus": true,
// turns on Auto Fix for all providers including ESLint
"editor.codeActionsOnSave": {
  "source.fixAll": true
}
```

Remove `"editor.defaultFormatter": "esbenp.prettier-vscode"` line if you had it before.

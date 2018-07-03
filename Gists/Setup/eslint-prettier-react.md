## Eslint with prettier settings for React apps

- `yarn add -D eslint-plugin-react eslint eslint-config-prettier eslint-plugin-prettier prettier`
- `.eslintrc`

```js
{
  "parserOptions": {
    "ecmaVersion": 6
  },
  "env": {
    "browser": true,
    "node": true
  },
  "parser": "babel-eslint",
  "plugins": ["prettier", "react"],
  "rules": {
    "prettier/prettier": [
      "error",
      {
        "singleQuote": true,
        "semi": true
      }
    ],
    "no-console": "off"
  },
  "extends": ["eslint:recommended", "plugin:react/recommended", "prettier", "prettier/react"]
}
```

- `.prettierrc`

```js
{
  "singleQuote": true
}
```

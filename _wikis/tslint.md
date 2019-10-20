---
title: tslint
---

## Tslint example

```json
{
  "defaultSeverity": "error",
  "extends": [
    "tslint:recommended"
  ],
  "rules": {
    "quotemark": [
      true,
      "single"
    ],
    "object-literal-sort-keys": false,
    "no-console": [
      true,
      "debug",
      "info",
      "time",
      "timeEnd",
      "trace"
    ],
    "object-curly-spacing": [
      true,
      "always"
    ],
    "arrow-return-shorthand": [
      true,
      "multiline"
    ],
    "indent": [
      true,
      "spaces",
      2
    ],
    "no-irregular-whitespace": true
  },
  "rulesDirectory": [
    "node_modules/tslint-eslint-rules/dist/rules"
  ],
  "jsRules": {}
}
```
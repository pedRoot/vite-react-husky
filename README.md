# vite-react-husky

Prueba introductoria sobre el uso de vite, por medio de una aplicación react js a la cual se le aplican test e2e al crear sus commits gracias a husky

## Creación de proyecto react con Vite.

yarn create vite

### Comandos de vite

- Servidor de desarrollo: yarn dev
- Building de la aplicación: yarn build
- Servidor de producción: yarn preview

## Configuración de paquetería

### Editor Config .editorconfig

```yaml
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
max_line_length = 80
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
max_line_length = 0
trim_trailing_whitespace = false

# Matches multiple files with brace expansion notation
# Set default charset
[*.{js,jsx,ts,tsx,py}]
charset = utf-8

[*.py]
indent_style = space
indent_size = 4

# Tab indentation (no size specified)
[Makefile]
indent_style = tab

# Matches the exact files either package.json or .travis.yml
[{package.json,.travis.yml}]
indent_style = space
indent_size = 2
```

### Eslint .eslint.json

```json
{
  "root": true,
  "env": {
    "browser": true,
    "es2021": true,
    "jest/globals": true,
    "node": true
  },
  "plugins": ["react", "jsx-a11y", "jest", "import", "unused-imports"],
  "extends": [
    "airbnb",
    "airbnb/hooks",
    "plugin:import/recommended",
    "plugin:jest/recommended",
    "plugin:jsx-a11y/recommended",
    "prettier"
  ],
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "overrides": [
    {
      "files": ["src/**/*.{js,jsx}"],
      "rules": {
        "import/order": [
          "error",
          {
            "groups": [
              "builtin",
              "external",
              "internal",
              ["parent", "sibling"],
              "index",
              "object",
              "type"
            ],
            "pathGroups": [
              {
                "pattern": "./**/**\\.css",
                "group": "type",
                "position": "after"
              }
            ],
            "pathGroupsExcludedImportTypes": ["builtin"],
            "alphabetize": {
              "order": "asc",
              "caseInsensitive": true
            },
            "newlines-between": "always",
            "warnOnUnassignedImports": true
          }
        ]
      }
    }
  ],
  "rules": {
    "jsx-quotes": ["error", "prefer-double"],
    "no-unused-vars": "warn",
    "react/function-component-definition": "off",
    "react/react-in-jsx-scope": "off",
    "semi": "error"
  }
}
```

### Prettier .prettierrc

```javascript
{
  "arrowParens": "avoid",
  "bracketSameLine": false,
  "bracketSpacing": true,
  "jsxSingleQuote": true,
  "printWidth": 80,
  "quoteProps": "as-needed",
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "none"
}
```

### Cypress cypress.json

Ejecutar yarn cy:r ó yarn cy:o para que sea creada la carpeta de trabajo de cypress

```json
{
  "baseUrl": "http://localhost:3000/",
  "integrationFolder": "cypress/test"
}
```

## Husky

- yarn add husky — save-dev
- npx husky install

### Agrega hook pre-commit

- npx husky add .husky/pre-commit "npm run cy:r"

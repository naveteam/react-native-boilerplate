# Nave React Native template.

## Using

Run `react-native init yourProjectName --template nave`

### Packages already configured

- Styled components
- React Navigation
- Axios
- Reactotron
- Commitlint

## Finishing configuration

Add `.env` to your .gitignore file

You'll also need to manually apply a plugin to your app, from `android/app/build.gradle`:

```
// 2nd line, add a new apply:
apply from: project(':react-native-config').projectDir.getPath() + "/dotenv.gradle"

```

Finally, add this to your `package.json`:

```json
  "scripts": {
    "start": "react-native start",
    "android": "react-native run-android",
    "ios": "react-native run-ios",
    "eslint": "eslint --ignore-path .gitignore .",
    "pretest": "yarn eslint",
    "test": "echo 'start tests'",
    "commit": "npx git-cz",
    "prettier": "prettier --write '**/*.js' --ignore-path .gitignore",
    "pod:install": "cd ios && pod install && cd .."
  },
  "config": {
    "commitizen": {
      "path": "./node_modules/cz-conventional-changelog"
    }
  },
  "lint-staged": {
    "*.{js, jsx}": [
      "prettier --write"
    ]
  }
```

## Code Standard

Além de todos os pontos citadas no [nave guide](https://nave.gitlab.io/guides/nave/code-guide/), como padrão de imports e boas práticas de javascript, existem algumas boas práticas que devem ser usadas, principalmente na criação de componentes e páginas.

1. Evite usar `styleds` desnecessários. Temos componentes de Row, Column e Text para evitar o uso desnecessários de styleds nas páginas. Além disso, estes componentes possuem o [styled-system](https://styled-system.com/getting-started), que permite passar margins, paddings e afins por props;
2. Ao criar um novo componente, sempre cogite a utilização do `styled-system`;
3. Sempre adicione as [prop-types](https://github.com/facebook/prop-types) nos componentes. Além de ajudar outras pessoas que forem usar este componente, serve também como documentação;
4. **NUNCA** repita o mesmo código duas vezes. Não copie e cole. Crie helpers e components. Reutilize código;
5. Se precisar criar um componente com várias variações, dê uma olha no componente de `Text` e utilize a propriedade `variant` do `styled-system`;
6. Siga o padrão de pastas e padrão de código. 

Copyright 2019 nave.rs

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
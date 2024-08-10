[webpack基本設定.md](../README.md)

# ESLint
> 構文チェック

## Webpack の ESLint-plugin
[eslint-webpack-plugin](https://webpack.js.org/plugins/eslint-webpack-plugin/) | webpack  
`webpack.config.js`に設定する。

### ESLint 単体
[ESLint.org](https://eslint.org/docs/latest/use/getting-started#quick-start)  
`eslint.config.js`専用ファイルが作成されそれに設定する。[eslint.config.js の Link](https://eslint.org/docs/latest/use/configure/configuration-files#configuration-file)
```bash
npm init @eslint/config@latest
# or
npm init @eslint/config@latest -- --config eslint-config-standard 
```
Installセットが異なりました。

1. [eslint.config.mjs](https://eslint.org/docs/latest/use/configure/configuration-files#configuration-file) 作成される
   - [eslint-config-standard](https://github.com/standard/eslint-config-standard)の場合
     - "eslint-plugin-import": "^2.29.1",
     - "eslint-plugin-n": "^16.6.2",
     - "eslint-plugin-promise": "^6.6.0",
```js
// eslint.config.mjs
import config from "eslint-config-standard";

export default [
  ...[].concat(config),
  // overrides 
];
```

- @eslit/config@latest コマンドだけの場合は選択できる。
  - eslint@[version] @eslint/js [globals](https://www.npmjs.com/package/globals)
  - `eslint-plugin-react`： React使いますか
  - [typescript-eslint](https://typescript-eslint.io/)： TypeScript使いますか

いろいろなプラグインがある模様。
```js
// eslint.config.mjs
import globals from "globals";
import pluginJs from "@eslint/js";
import tseslint from "typescript-eslint";
import pluginReact from "eslint-plugin-react";

export default [
  {files: ["**/*.{js,mjs,cjs,ts,jsx,tsx}"]},
  {files: ["**/*.js"], languageOptions: {sourceType: "commonjs"}},
  {languageOptions: { globals: globals.browser }},
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  pluginReact.configs.flat.recommended,
];
```


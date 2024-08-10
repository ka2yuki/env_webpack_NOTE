[webpack基本設定.md](../README.md)

# WebpackでReact
- `.jsx` を `.js` にすると直ったエラー
  - `this file type`が **ファイル拡張子** のこと と思われる。
  -  Babelサイトから [@babel/preset-react](https://babeljs.io/docs/babel-preset-react)参照で webpack.config.js の presets。
```bash
ERROR in ./src/index.jsx 15:2
Module parse failed: Unexpected token (15:2)
You may need an appropriate loader to handle this file type, currently no loaders are configured to process this file. See https://webpack.js.org/concepts#loaders
| 
| ReactDOM.render(
>   <h1>Hello, Frontedn Engineer!</h1>,
|   document.getElementById('root')
| );
webpack 5.93.0 compiled with 1 error in 224 ms
```
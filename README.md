# Webpack ENVs 
- たぶん現在react用のwebpack

# Webpack環境の作成
環境：WSL
```bash
nvm -v
> 0.39.7
node -v
> v20.16.0
```

pakege.json作成 ～ 開発サーバーまで
```bash
npm init -y
npm i -D webpack webpack-dev-server webpack-cli @webpack-cli/generators
npm audit fix
npm audit
npx webpack init # webpack.config.js作成
npx webpack serve # open localhost:devserver.
```

# Documentation
- [webpack-cli's init command](https://webpack.js.org/api/cli/#init)
- [Use a different configuration file](https://webpack.js.org/configuration/#use-a-different-configuration-file)
```bash
webpack --config prod.config.js
```
- [plugins](https://webpack.js.org/plugins/)

- ### 気になるAwesome-Webpack/#Loaders
- [Webpack Dashboard](https://github.com/FormidableLabs/webpack-dashboard)
- [etc...  Awesome-Webpack Loaders](https://webpack.js.org/awesome-webpack/)

# Error log
- `--template=default` でエラー on WSL
  - nvmを使用することにしたら解決しました。

# ハマったポイント
webpack5
- 開発サーバーが立ち上がらない: webpack-dev-serverを未インストール。
  - エラーメッセージ：`[webpack-cli] For using 'serve' command you need to install: 'webpack-dev-server' package.` 
- HotReloadされない: [DevServer](https://webpack.js.org/configuration/dev-server/)
  - webpack.config.js の config.entryファイルを watch している。

# points
[webpack.config.js](./webpack.config.js)
```js
const path = require("path");
```
Nodejs.API: path: https://nodejs.org/api/path.html
```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
```
https://webpack.js.org/plugins/html-webpack-plugin/
```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin"); 
// config.plugin.push( new MiniCssExtractPlugin() );
```
https://webpack.js.org/plugins/mini-css-extract-plugin/
```js
const WorkboxWebpackPlugin = require("workbox-webpack-plugin");
// config.plugin.push( new WorkboxWebpackPlugin.GenerateSW() );
```
[workbox-webpack-plugin | google🔍](https://www.google.com/search?q=workbox-webpack-plugin&rlz=1C1TKQJ_jaJP1051JP1051&oq=workbox-webpack-plugin&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQABgeMgYIAhAAGB4yBggDEAAYHjIGCAQQABgeMgYIBRAAGB4yBggGEAAYHjIGCAcQABgeMgYICBAAGB4yBggJEAAYHtIBBzQ3OGowajSoAgCwAgA&sourceid=chrome&ie=UTF-8)  
https://developer.chrome.com/docs/workbox/modules/workbox-webpack-plugin?hl=ja

Bundle画像サイズの制限
```js
  module: {
    rules: [
      {
        parser: {
          dataUrlCondition: {
            maxSize: 4 * 1024,
          }
        }}]}
```
https://webpack.js.org/configuration/module/#ruleparserdataurlcondition
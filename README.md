# ENVs webpack
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
npm i -y
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

## 気になるAwesome-Webpack/#Loaders
- [Webpack Dashboard](https://github.com/FormidableLabs/webpack-dashboard)
- [etc...  Awesome-Webpack Loaders](https://webpack.js.org/awesome-webpack/)

# Error log
- `--template=default` でエラー on WSL
  - nvmを使用することにしたら解決しました。

# ハマったポイント
webpack5
- webpack-dev-serverをインストールしていない為に開発サーバーが立ち上がらない。
  - `[webpack-cli] For using 'serve' command you need to install: 'webpack-dev-server' package.` 
- hotreloadされない: [DevServer](https://webpack.js.org/configuration/dev-server/)
  -   webpack.config.js の config.entryファイルを watch している

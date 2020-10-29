# typescript-cheatsheet
TypeScriptの書き方をメモしたさまざまなサンプル集

# プロジェクト構築メモ

## Gitを入れる

```zsh
git init
```

## プロジェクトを作成する

yarnを使って作成

```zsh
yarn init
```

## 必要なライブラリをインストール

```zsh
yarn add typescript@4.0.5
yarn add react@16.5.2 react-dom@16.5.2 react-hot-loader@4.3.11
yarn add -D css-loader@1.0.0
```

## 必要なディレクトリを作成する

以下の構造になるようにディレクトリを作成

```zsh
rouc@roucnombp typescript-cheatsheet % tree -L 1 .
.
├── README.md
├── node_modules
├── package.json
├── public  <--- 追加
├── src  <--- 追加
└── yarn.lock
```

作成

```zsh
mkdir public
mkdir src
```

## .gitignoreに追加

```text
.DS_STORE
.idea/
.vscode/
```

## Babelをインストール

```zsh
yarn add -D @babel/core@7.1.0 @babel/cli@7.1.0 @babel/preset-env@7.1.0 @babel/preset-react@7.0.0
```

```zsh
vim .babelrc
```

```text
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

## Webpack

```zsh
yarn add -D webpack@4.19.1 webpack-cli@3.1.1 webpack-dev-server@3.1.8 style-loader@0.23.0 css-loader@1.0.0 babel-loader@8.0.2
```

```
vim webpack.config.js
```

```javascript webpack.config.js
const path = require("path");
const webpack = require("webpack");

module.exports = {
  entry: "./src/index.js",
  mode: "development",
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /(node_modules|bower_components)/,
        loader: "babel-loader",
        options: { presets: ["@babel/env"] }
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  resolve: { extensions: ["*", ".js", ".jsx"] },
  output: {
    path: path.resolve(__dirname, "dist/"),
    publicPath: "/dist/",
    filename: "bundle.js"
  },
  devServer: {
    contentBase: path.join(__dirname, "public/"),
    port: 3000,
    publicPath: "http://localhost:3000/dist/",
    hotOnly: true
  },
  plugins: [new webpack.HotModuleReplacementPlugin()]
};
```

## Reactのエントリーポイントを作成

```
vim src/index.js
```

```javascript src/index.js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App.js";
ReactDOM.render(<App />, document.getElementById("root"));
```

```zsh
vim src/App.js
```

```javascript src/App.js
import React, { Component} from "react";
import "./App.css";

class App extends Component{
  render(){
    return(
      <div className="App">
        <h1> Hello, World! </h1>
      </div>
    );
  }
}

export default App;
```

```zsh
vim src/App.css
```

```css src/App.css
.App {
  margin: 1rem;
  font-family: Arial, Helvetica, sans-serif;
}
```

## 状況確認

現在のディレクトリ構成は以下のようになっているはず

```zsh
rouc@roucnombp typescript-cheatsheet % tree -L 2 -I node_modules .
.
├── README.md
├── package.json
├── public
│    └── index.html
├── src
│    ├── App.css
│    ├── App.js
│    └── index.js
├── webpack.config.js
└── yarn.lock
```

## package.jsonにReactプロジェクト起動用のコマンドを追加

package.jsonに以下を追加

```jsons package.json
  "scripts": {
    "start": "webpack-dev-server --mode development"
  },
```

## プロジェクトを起動

```zsh
yarn start
```

http://localhost:3000にアクセスして

```
Hello, World!
```

が出力されることを確認する

## ----------- prettierの追加

# 参考

[Creating a React App… From Scratch.](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658)

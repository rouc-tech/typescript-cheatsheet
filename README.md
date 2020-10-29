# typescript-cheatsheet
TypeScriptの書き方をメモしたさまざまなサンプル集

# プロジェクト構築メモ

## Gitを入れる

```
git init
```

## プロジェクトを作成する

yarnを使って作成

```
yarn init
```

## TypeScriptをインストール

```
yarn add typescript@4.0.5
```

## 必要なディレクトリを作成する

以下の構造になるようにディレクトリを作成

```

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

```
mkdir public
mkdir src
```

## .gitignoreに追加

```
.DS_STORE
.idea/
.vscode/
```

# 参考

[Creating a React App… From Scratch.](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658)

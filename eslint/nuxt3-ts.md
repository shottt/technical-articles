# Nuxt3 + TypeScript環境でESLint導入
## はじめに
Nuxt3+TypeScript環境でESLintを導入する手順を説明します。
※ Nuxt3とTypeScriptはインストール済みの前提です。

## 実行環境
Node.js：18.4.0
npm：8.13.2
Nuxt：3.0.0-rc.10
TypeScript：^4.8.3

## ESLintとは？
JavaScript、TypeScriptの静的解析ツールです。
システム全体のコードの一貫性を維持することを目的とし、ESLintで定義したコーディング規約や、単純な構文エラーをチェックし、指摘したり、修正してくれる仕組みです。

## 手順
### ESLintのインストール
#### ESLint本体のインストール
```
$ npm install --save-dev eslint
```
#### eslint-plugin-vueのインストール
リアルタイムで.vueファイルの構文エラーが検出可能なプラグインです。
```
$ npm install --save-dev eslint-plugin-vue
```
#### TypeScript関連のESLintプラグインのインストール
```
$ npm install --save-dev @typescript-eslint/eslint-plugin @typescript-eslint/parser @nuxtjs/eslint-config-typescript
```

### ESLintの初期化
初期化コマンドを打っていくつかの質問に答えると、回答内容に基づいた`.eslintrc`ファイルが出来上がります。
```
$ npx eslint --init

✔ How would you like to use ESLint? · problems
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · vue
✔ Does your project use TypeScript? · No / Yes
✔ Where does your code run? · browser, node
✔ What format do you want your config file to be in? · YAML
```
上記の回答で以下内容のファイルが出来上がります。
```
env:
  browser: true
  es2021: true
  node: true
extends:
  - eslint:recommended
  - plugin:vue/vue3-essential
  - plugin:@typescript-eslint/recommended
overrides: []
parser: '@typescript-eslint/parser'
parserOptions:
  ecmaVersion: latest
  sourceType: module
plugins:
  - vue
  - '@typescript-eslint'
rules: {}
```
このファイルにプロジェクト独自の設定を書き加えていくことになります。
### おわりに
ESLintをうまく導入することで、チーム開発時のコードがカオスになることを防ぐことができるため、積極的に採用していくべきだと思います。

# 開発用Macのセットアップ
## はじめに
開発用にM1のMacを買ったので、やるべきことをまとめました。
参考に筆者はwebエンジニアで、PHP、JavaScript、Node.js、Python等を使います。

## 実行環境
MacOs：M1チップ Monterey 12.4

## 本体設定
- OSアップデート
- Dockを自動的に表示/非表示のチェックをつける
- Dockをカスタマイズ
- バッテリーの%表示

## 必須アプリケーションのインストール
### ブラウザ
- Google Chrome
https://www.google.com/intl/ja_jp/chrome/

### ターミナル
- iTerm2
https://iterm2.com/
- warp
https://www.warp.dev/

### エディタ
エディタは便利な拡張機能が豊富にあり、カスタマイズ性が十分にあるVSCode一択です。
- VSCode
https://code.visualstudio.com/download

### チャットツール
クライアントやチームメンバーによって使い分けるため、複数インストールします。
- Slack
https://slack.com/intl/ja-jp/downloads/mac
- Discord
https://discord.com/download
- ChatWork
https://go.chatwork.com/ja/download/

### web会議ツール
クライアントやチームメンバーによって使い分けるため、複数インストールします。
- zoom
https://zoom.us/download
- Microsoft Teams
https://www.microsoft.com/ja-jp/microsoft-teams/download-app
- Google Meet
https://meet.google.com/

### SQLクライアント
- TablePlus
https://tableplus.com/

### FTPクライアント
- FileZilla
https://filezilla.jp.uptodown.com/mac

### パッケージマネージャ
- Homebrew
Macのパッケージ管理ツールで、コマンド一つでパッケージを管理できます。
Macで開発するには必須のツールです。
https://brew.sh/index_ja

### その他
- Postman
APIのレスポンスを確認するアプリケーションです。
https://www.postman.com/
- Docker Desktop
今やローカルの開発環境に必須だと思われます。
https://www.docker.com/products/docker-desktop/

## Homebrewでパッケージをインストール
- git
デフォルトでApple gitがインストールされていますが、Homebrewで新しくインストールします。
- Node.js
複数バージョンが管理できるので、nodebrewを用いてインストールします。
- Python
複数バージョンが管理できるので、pyenvを用いてインストールします。


## おわりに
基本的には個人的なメモですが、誰かの参考になれば幸いです。
# Macの開発環境構築
## はじめに
Macを開発用に使うときの本体設定やインストールするアプリケーションをまとめました。
ちなみに筆者はwebエンジニアで、PHP、JavaScript、Node.js、Python等を使います。
実行環境はMacOs：M1チップ Monterey 12.4です。

## 本体設定
- OSアップデート
- 「Dock」を自動的に表示/非表示のチェックをつける

## アプリケーションのインストール
### ブラウザ
- Google Chrome
https://www.google.com/intl/ja_jp/chrome/

### ターミナル
- iTerm2
https://iterm2.com/
- warp
https://www.warp.dev/

### エディタ
- VSCode
https://code.visualstudio.com/download

### チャットツール
#### Slack
https://slack.com/intl/ja-jp/downloads/mac
#### Discord
https://discord.com/download
#### ChatWork
https://go.chatwork.com/ja/download/

### web会議ツール
#### zoom
https://zoom.us/download
#### Microsoft Teams
https://www.microsoft.com/ja-jp/microsoft-teams/download-app
#### Google Meet
https://meet.google.com/

### SQLクライアント
#### TablePlus
https://tableplus.com/

### FTPクライアント
#### FileZilla
https://filezilla.jp.uptodown.com/mac

### パッケージマネージャ
#### Homebrew
https://brew.sh/index_ja

### その他
#### Postman
https://www.postman.com/
#### Docker Desktop
https://www.docker.com/products/docker-desktop/
#### git
デフォルトでApple gitがインストールされていますが、Homebrewで新しくインストールします。
```
brew git install
// シェルを確認
echo $SHELL

// パスを追加する
// /bin/zshの場合
vi ~/.zshrc
// ファイルの一番最後にexport PATH=/usr/local/bin/git:$PATHを記載
source ~/.zshrc

// /bin/bashの場合
vi ~/.bash_profile
// ファイルの一番最後にexport PATH=/usr/local/bin/git:$PATHを記載
source ~/.bash_profile
```

#### Node.js
複数バージョンを管理するために、nodebrewでインストールします。
```
brew install nodebrew 
// nodebrewをセットアップ
nodebrew setup

// パスを追加する
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
// または
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bash_profile

// シェルの設定を反映
source ~/.bash_profile

// Node.jsをインストール
nodebrew install バージョン
// 安定版をインストールする場合
nodebrew install stable

// Node.jsの有効化
nodebrew use バージョン
```

#### yarn
```
brew install yarn
```










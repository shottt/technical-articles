# Node.jsをnodebrewを用いて管理する（Mac向け）
## はじめに
ローカルマシンでバージョンの違う複数のプロジェクトを開発することは往々にしてあると思います。
単一バージョンをインストールしていると、毎回インストールとパスを通す作業が発生しますが、
nodebrewの場合はコマンドだけでNode.jsのバージョンの切り替えが可能です。
（最近はDockerを使うのでホストマシン側のNodeに依存することは少ないかもしれませんが。。）

今回はnodebrewのインストールとバージョン変更手順を説明します。

## Homebrewのインストール
ターミナルを開き、以下のコマンドでMacのパッケージ管理ツールのHomebrewをインストールします。
```
% /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
参考
https://brew.sh/index_ja

## nodebrewのインストール
ターミナルで以下のコマンドを実行します。
```
% brew install nodebrew 
```
## パスを通す
`nodebrew setup`コマンドを叩いて追加するパスを確認します。
```
% nodebrew setup

Fetching nodebrew...
Installed nodebrew in $HOME/.nodebrew

========================================
Export a path to nodebrew:

export PATH=$HOME/.nodebrew/current/bin:$PATH
========================================
```
以下のコマンドを叩いて使っているシェルを確認します。
```
% echo $SHELL
```
#### /bin/zshの場合
以下のコマンドを実行してパスを通します。
```
% echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
```
以下のコマンドでシェルの設定を反映します。
```
% source ~/.zshrc
```

#### /bin/bashの場合
以下のコマンドを実行してパスを通します。
```
% echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bash_profile
```
以下のコマンドでシェルの設定を反映します。

```
% source ~/.bash_profile
```

## Node.jsのインストール
インストール可能なNode.js一覧は以下のコマンドで確認できます。
```
% nodebrew ls-remote
```
以下のコマンドでバージョンを指定してインストールします。
```
% nodebrew install v18.4.0
```
安定版をインストールする場合
```
% nodebrew install stable
```
インストールしたNode.js一覧を確認する場合は`nodebrew ls`を実行します。
```
% nodebrew ls

v18.4.0

current: none

```
`current: none`となっているので、Node.jsを有効にする必要があります。

## Node.jsの有効化
以下のコマンドで使うNode.jsを指定します。
```
nodebrew use v18.4.0
```
再度、`nodebrew ls`を実行します。
```
% nodebrew ls
v18.4.0

current: v18.4.0
```
上記の通り、指定したバージョンが有効になっていることが確認できると思います
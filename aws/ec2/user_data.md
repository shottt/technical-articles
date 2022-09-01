# EC2起動時にgit、docker、docker-composeをインストールする
## はじめに
AWSのEC2をDocker運用で開発webサーバーとして構築する機会があり、最低限、git、docker、docker-composeは必要なので、起動時にインストールするよう設定しました。

今回はその方法を紹介します。

## 手順
EC2のユーザーデータという機能を使えばできます。
EC2起動時のコンソールにユーザーデータというフォームがあるので、そこに以下のシェルスクリプトを入力して起動すればインストールされた状態になっているはずです。
```
#!/bin/bash
sudo yum update -y
sudo yum install -y git
sudo yum install -y docker
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -a -G docker ec2-user
sudo mkdir -p /usr/local/lib/docker/cli-plugins
VER=2.5.1
sudo curl \
-L https://github.com/docker/compose/releases/download/v${VER}/docker-compose-$(uname -s)-$(uname -m) \
-o /usr/local/lib/docker/cli-plugins/docker-compose
sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
sudo ln -s /usr/local/lib/docker/cli-plugins/docker-compose /usr/bin/docker-compose
```
シェルスクリプトの内容を説明します。
### パッケージのアップデート
パッケージを最新にします。
```
sudo yum update -y
```

### gitのインストール
```
sudo yum install -y git
```
### dockerのインストール
dockerをインストールします。
```
sudo yum install -y docker
```
dockerサービスを起動します。
```
sudo systemctl start docker
```
マシンが立ち上がった時にdockerサービスの自動起動を有効にします。
```
sudo systemctl enable docker
```
dockerをインストールするとOSにdockerグループができるため、そこにec2ユーザーを追加します。
これをすることでec2-userは`sudo`なしで`docker`コマンドを実行できるようになります。
```
sudo usermod -a -G docker ec2-user
```

### docker-composeのインストール
docker-composeのバイナリファイル格納用のディレクトリを作ります。
```
sudo mkdir -p /usr/local/lib/docker/cli-plugins
```
インストールするバージョンを変数に格納します。
```
VER=2.5.1
```
GitHubにあるdocker-composeのバイナリファイルを作成したディレクトリにダウンロードします。
```
sudo curl \
-L https://github.com/docker/compose/releases/download/v${VER}/docker-compose-$(uname -s)-$(uname -m) \
-o /usr/local/lib/docker/cli-plugins/docker-compose
```
ダウンロードしたバイナリファイルに実行権限を付与します。
```
sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
```
`/usr/bin/`に`/usr/local/lib/docker/cli-plugins/docker-compose`へのシンボリックリンクを貼ります。
```
sudo ln -s /usr/local/lib/docker/cli-plugins/docker-compose /usr/bin/docker-compose
```

### 確認
起動後にインスタンスにログインし、以下コマンドを実行してバージョンが表示されていれば成功です。
```
git --version
docker -v
docker-compose --version
```

## 参考
EC2のユーザーデータについては以下の公式ドキュメントをご覧ください。
https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/user-data.html#user-data-shell-scripts




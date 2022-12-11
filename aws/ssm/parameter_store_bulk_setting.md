# AWS Copilot CLI を用いて ECS の機密データを SSM に一括設定

## 概要

AWS Copilot CLI を用いて ECS を構築していた場合、
ローカル環境からコマンドを実行するだけで、AWS System Manager（SSM） のパラメータストア（SecureString）に環境変数等の機密データを一括で設定できるので、やり方をご紹介します。

## 事前準備

※ ローカル環境は Mac OS で AWS で IAM アカウント作成済み（ECS 操作権限あり）であることが前提です。

#### AWS Copilot CLI のインストール

以下のコマンドで AWS Copilot CLI をインストールします。

```
$ brew install aws/tap/copilot-cli
```

#### プロファイル設定

.aws/credentials に以下を追記する。

```
[sample]
aws_access_key_id =
aws_secret_access_key =
```

※ aws_access_key_id と aws_secret_access_key は IAM でアカウント単位で作成した値を入力ください。`[]`内は任意の名前を入力ください。

## 手順

#### 設定ファイルの作成

secrets.yaml（ファイル名は任意）に以下のような形式で記述します。
今回は staging 環境と production 環境の DB の情報を一括で設定します。

```
DB_USERNAME:
  staging: hoge
  production: fuga
DB_PASSWORD:
  staging: password
  production: password
```

#### コマンドを実行

Copilot で`my-app`というアプリケーションを作っていた場合、
設定ファイルが配置してあるディレクトリで以下のコマンドを実行すると、パラメータを一括で設定することが可能です。

```
$ AWS_PROFILE=sample copilot secret init --app my-app --cli-input-yaml secrets.yaml
```

上記を実行すると、SSM パラメータストアでは以下のようなパスで保存されます。
`/copilot/my-app/{環境名}/secrets/{変数名}`

Service の Manifest ファイルで呼び出す場合は以下のように記述します。

```
environments:
    staging:
      secrets:
        DB_USERNAME: /copilot/my-app/staging/secrets/db_username
        DB_PASSWORD: /copilot/my-app/staging/secrets/db_password
    production:
      secrets:
        DB_USERNAME: /copilot/my-app/production/secrets/db_username
        DB_PASSWORD: /copilot/my-app/production/secrets/db_password
```

## おわりに

Copilot コマンドを用いることで、AWS のマネジメントコンソールで 1 パラメータずつ入力しなくて良いので、手間が省けます。また、同じ設定でコマンドを実行すると値を上書きしてくれるので、更新も同じコマンドでできます。本記事がお役に立てば幸いです。

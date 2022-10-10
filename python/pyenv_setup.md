# Pythonをpyenvを用いて管理する（Mac向け）
## はじめに
ローカルマシンで複数のプロジェクトを開発する時にバージョンの異なるPythonを使うことは往々にしてあると思います。
単一バージョンをインストールしていると、毎回インストールとパスを通す作業が発生しますが、
pyenvの場合はコマンドだけでPythonのバージョンの切り替えが可能です。
（最近はDockerを使うのでホストマシン側のPythonに依存することは少ないかもしれませんが。。）

今回はpyenvのインストールとバージョン変更手順を説明します。

## Homebrewのインストール
ターミナルを開き、以下のコマンドでMacのパッケージ管理ツールのHomebrewをインストールします。
```
% /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
参考
https://brew.sh/index_ja

## pyenvのインストール
ターミナルで以下のコマンドを実行します。
```
% brew install pyenv 
```
以下のコマンドを実行してバージョンが表示されれば成功です。
```
$ pyenv -v

pyenv 2.3.5
```

## パスを通す

#### /bin/zshの場合
以下のコマンドを実行してパスを通します。
```
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
```
```
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
```
```
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```
上記のパスが.zshrcに追記されているか確認します。
```
$ cat ~/.zshrc
```
追記されていることを確認したら、以下のコマンドでシェルの設定を反映します。
```
$ source ~/.zshrc
```

#### /bin/bashの場合
以下のコマンドを実行してパスを通します。
```
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
```
```
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
```
```
$ echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```
上記のパスが.zshrcに追記されているか確認します。
```
$ cat ~/.zshrc
```
追記されていることを確認したら、以下のコマンドでシェルの設定を反映します。

```
$ source ~/.bash_profile
```

## Pythonのインストール
以下のコマンドでインストール可能なPythonのバージョン一覧を表示できます。
```
$ pyenv install --list
```
現時点（2022/10/10）で最新版をインストールします。
```
$ pyenv install 3.10.7
```
インストール済みのバージョンを確認する。
```
$ pyenv versions
* system (set by /Users/user/.pyenv/version)
  3.10.7
```
または、
```
$ pyenv global
system
```

## バージョンの切り替え
以下のコマンドを用いてインストールしたバージョンの切り替えます。
```
$ pyenv global 3.10.7
```
バージョンが切り替わっているか確認します。
```
$ pyenv versions
  system
* 3.10.7 (set by /Users/shsh/.pyenv/version)
```
上記の通り、指定したバージョンに切り替わっていることが確認できます。
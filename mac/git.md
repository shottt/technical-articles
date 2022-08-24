# MacデフォルトのApple GitからHomebrewのGitに切り替える
## はじめに
MacにはApple GitというGitがデフォルトで入っていますが、
開発用のパッケージはHomebrewで管理することが多いと思うので、
Homebrewでの管理に切り替えます。

## 手順
### Gitのバージョン確認
ターミナルで以下のコマンドを打った時にバージョンの末尾に（Apple Git-xxx）とつくものが表示される場合は、MacデフォルトのGitが参照されてます。
```
git --version
```
### Homebrew経由でGitをインストール
ターミナルで以下のコマンドを実行します。
```
brew git install
```

### パスの変更
ターミナルで以下のコマンドを実行して、使用しているシェルを確認します。
```
echo $SHELL
```

#### /bin/zshの場合
.zshrcファイルを開く。
```
vi ~/.zshrc
```
ファイルに以下の記述を追記する。
```
export PATH=/usr/local/bin/git:$PATH
```
変更内容を反映する。
```
source ~/.zshrc
```
#### /bin/bashの場合
.bash_profileファイルを開く。
```
vi ~/.bash_profile
```
ファイルに以下の記述を追記する。
```
export PATH=/usr/local/bin/git:$PATH
```
変更内容を反映する。
```
source ~/.bash_profile
```
変更が反映されていることを確認する。
```
git --version
```
Appleの表記が消えていれば完了です。
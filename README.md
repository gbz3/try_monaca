# try_monaca

## 環境構築 - WSL
- WSL インストール
- Ubuntu 18.4 LTS インストール
- VS Code に 'Remote - WSL', 'Remote - Development' インストール
- 左下の「><」リモートウインドウを開く
  - 初回はインストール終了を少し待つ
- ホームディレクトリを開く
- 'Ctrl + Shift + @' でターミナルを開く
- ~/.ssh に SSH鍵を配置
  - 0755 ~/.ssh
  - 0600 ~/.ssh/id_rsa
  - 0644 ~/.ssh/id_rsa.pub
- git 初期設定
```
$ git config --global user.name '<username>'
$ git config --global user.email '<email-address>'
$ git config --global code.editor 'code --wait'
$ git config --global merge.tool 'code --wait "$MERGED"'
$ git config --global push.default simple
```
- clone
```
$ mkdir git_repos
$ cd git_repos
$ git clone '<SSH version URL>'
```

## 環境構築 - Node.js @WSL
- nodebrew インストール
```
$ curl -L git.io/nodebrew | perl - setup
```
- パス設定 以下を ~/.bashrc に追記して反映
```
export PATH="$HOME/.nodebrew/current/bin:$PATH"
```
- Node.js インストール
```
$ nodebrew install-binary latest
$ nodebrew ls
v13.9.0

current: none
$ nodebrew use latest
use v13.9.0
$ nodebrew ls
v13.9.0

current: v13.9.0
$ node -v
v13.9.0
$ npm -v
6.13.7
```

## 環境構築 - Monoca CLI @WSL
- Monaca CLI インストール
```
$ npm install -g monaca
$ type monaca
monaca is $HOME/.nodebrew/current/bin/monaca
$ monaca login
Successfully signed in as ***.
$ mkdir ~/monaca_projects
$ cd ~/monaca_projects
$ monaca clone
Fetching project list...
? Which project would you like to synchronize? <プロジェクト名>
? Destination directory: <ディレクトリ名>
Cloning '<プロジェクト名>' to $HOME/monaca_projects/<ディレクトリ名>
～省略～
Project is successfully cloned from Monaca Cloud!

Type "cd <ディレクトリ名>" and run monaca command again.
  > monaca preview      => Run app in the browser
  > monaca debug        => Run app in the device using Monaca Debugger
  > monaca remote build => Start remote build for iOS/Android/Windows
  > monaca upload       => Upload this project to Monaca Cloud IDE
$ cd <ディレクトリ名>/
```
- VS Code でフォルダを開く
- Monaca デバッガ動作環境構築
```
$ npm install nw@0.26.6
```

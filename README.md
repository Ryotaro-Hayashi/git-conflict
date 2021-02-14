# git-command

## 基本的な使い方

```
作業ディレクトリとステージングの状態を確認
git status
```

```
指定したファイル(フォルダ)をステージングに追加
git add ファイル(フォルダ)名
全てステージングに追加
git add -A
```

```
ステージングに登録した内容を取り消す
git reset
git reset ファイル名
```

```
コミットする
git commit -m "commit message"
```

```
コミットログを出力する
git log -n <表示上限> --oneline --graph
```

```
最近実行したコミットログを出力する
git reflog
```

```
プッシュする
git push origin <ブランチ名>
git push
```

```
プルする
git pull origin <ブランチ名>
```

```
変更内容の差分を表示
git diff
```

```
ブランチを作成
git branch <ブランチ名>
```

```
存在するブランチを確認
git branch
```

```
ブランチを切り替える
git checkout <ブランチ名>
```

## 先にローカルがあるとき（要確認）

```
カレントフォルダを Git のリポジトリにする
git init
```

## 特定のリビジョンに戻る（要確認）

```
git checkout <コミットハッシュ>
コミットハッシュは「git log」で確認
```

```
ファイルを指定して特定のリビジョンに戻る
git checkout <コミットハッシュ> <ファイル>
```

## 現在の変更内容を取り消す（要確認）

```
ファイル指定

git checkout HEAD <ファイルパス>
```

```
全ファイル一括
git reset --hard
```

```
git checkout HEAD <ファイルパス>
```

## git rebase
### 状況
develop から feature/two というブランチを切って開発している間に、develop が更新されてしまった

### 手順

```
developを最新にする
$ git checkout develop
$ git pull origin develop
```

```
開発中のブランチに移動して最新のdevelopと接続
$ git checkout feature/two
$ git rebase develop
```

```
コンフリクトが発生した場合
コンフリクトを解消
$ git add ファイル名
$ git rebase --continue
```

## git stash
### 状況
develop から feature/two というブランチで開発を行いプルリクを出してマージ待ちのとき、feature/two の実装内容を踏まえて開発をしたい

### 手順

```
そのまま feature/twoでコミットせずに開発を続ける
feature/twoがマージされたら、実装の差分を退避させる
$ git stash
```

```
developを最新にする
$ git checkout develop
$ git pull origin develop
```

```
新しくブランチを切って、差分を復活させる
$ git checkout -b feature/three
$ git stash pop
```

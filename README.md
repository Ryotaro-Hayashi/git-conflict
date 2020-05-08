# git-command

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

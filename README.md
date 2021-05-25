# git-command

## 基本的な使い方

作業ディレクトリとステージングの状態を確認
```
git status
```
指定したファイル(フォルダ)をステージングに追加
```
git add ファイル(フォルダ)名
```
全てステージングに追加
```
git add -A
```
ステージングに登録した内容を取り消す
```
git reset ファイル名
```
指定したファイルをワーキングツリーに復元
```
git restore ファイル名
```
コミットする
```
git commit -m "commit message"
```
空コミットする
```
git commit --allow-empty -m "empty commit message"
```
ステージングされているファイルを直前のコミットに取り入れる（`--no-edit`がないとエディタが立ち上がる）
```
git commit —-amend —-no-edit
```
コミットログを出力する
```
git log --oneline --graph --all -n <表示させたい件数>
```
参照ログ(HEADやブランチ先端の動き)を出力する
```
git reflog
```
プッシュする
```
git push origin HEAD
```
安全にフォースプッシュする
```
git push origin <ブランチ名> —force-with-lease
```
プルする
```
git pull origin <ブランチ名>
```
別のブランチの変更をマージコミットをせずに取り入れる
```
git pull --rebase origin <ブランチ名>
```
リモートリポジトリをリモート追跡ブランチに反映し、リモートで存在しないブランチをローカルから削除
```
git fetch --prune
```
変更内容の差分を表示
```
git diff
```
コミット間の差分を表示
```
git diff <コミットID> <コミットID>
```
コミット間で差分のあるファイル一覧を表示
```
git diff --name-only <コミットID> <コミットID>
```
ファイルを指定してコミット間の差分を表示
```
git diff <コミットID> <コミットID> <ファイル名>
```
リモートブランチとの差分を表示する
```
git diff <リモートブランチ(ex: origin/master)>
```
ブランチを作成
```
git branch <ブランチ名>
```
リモートブランチをもとに同名のブランチを作成
```
git branch　<ブランチ名> origin/<ブランチ名>
```
存在するブランチを確認
```
git branch
```
ブランチを切り替える
```
git checkout <ブランチ名>
```
ブランチを作成して切り替える
```
git checkout -b <ブランチ名>
```
リモートブランチに切り替える
```
git switch <リモートブランチ名（originはいらない）>
```
リモートブランチに切り替える
```
git switch <リモートブランチ名（originはいらない）>
```

## config
`git pull`で毎回`git pull –rebase`をするようにする
```
git config —grobal pull.rebase true
```

## 先にローカルがあるとき

カレントディレクトリをGitのリポジトリにする
```
git init
```
リモートリポジトリを登録する
```
git remote add <リモートリポジトリ名(ex: origin)> <リモートリポジトリのURL>
```

## 特定のリビジョンに戻る

```
git checkout <コミットID>
```

## 派生先のブランチを更新する
### 状況
develop から feature/two というブランチを切って開発している間に、develop が更新されてしまった

### 手順
developを最新にする
```
git checkout develop
```
```
git pull origin develop
```
開発中のブランチに移動して最新のdevelopと接続
```
git checkout feature/two
```
```
git rebase develop
```
コンフリクトが発生した場合、解消→以下のコマンドの実行を繰り返す
```
git add ファイル名
```
```
git rebase --continue
```

## 変更差分を退避させる
実装の差分を退避させる
```
git stash
```
差分を復活させる
```
git stash pop
```

## コミットをまとめる
修正する範囲のコミットを指定してrebase
```
git rebase -i <コミット範囲（ex: HEAD~4）>
```
まとめたいコミットのpickをsquash(または s)に修正する

コミットメッセージを編集する（まとめたいコミットを削除する）

## コミットメッセージを修正する
使用する流れは「**コミットをまとめる**」と同じ

reword: コミットメッセージを修正する

## コミットを分割する
修正する範囲のコミットを指定してrebase
```
git rebase -i <コミット範囲（ex: HEAD~4）>
```
まとめたいコミットのpickをeditに修正する

指定したコミットでリベースが止まる

コミットを取り消す
```
git reset --soft HEAD~1
```
分割してコミットする

rebaseを再開させる
```
git rebase --continue
```

## コミットを入れ替える・削除する
修正する範囲のコミットを指定してrebase
```
git rebase -i <コミット範囲（ex: HEAD~4）>
```
コミットを入れ替えたり削除するだけ

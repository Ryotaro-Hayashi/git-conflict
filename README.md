# git-command

## git rebase
### 状況
develop から feature/two というブランチを切って開発している間に、develop が更新されてしまった

### 手順

```
$ git checkout develop
```

```
$ git pull origin develop
```

```
$ git checkout feature/two
```

```
$ git rebase develop
```

```
コンフリクトを解消
```

```
$ git add ファイル名
```

```
$git rebase --continue
```


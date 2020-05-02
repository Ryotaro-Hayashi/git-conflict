# git-rebase

<h3>状況</h3>
develop から feature/two というブランチを切って開発している間に、develop が更新されてしまった

<h3>手順</h3>

'$git checkout develop'

'$git pull origin develop'

'$git checkout feature/two'

'$git rebase develop'

コンフリクトを解消

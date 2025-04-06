```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

Versuchen Sie einen automatischen Merge-Rebase des aktuellen Branches, von `upstream`, falls angegeben, oder andernfalls vom Upstream-Tracking-Branch. `newbase` ist der Branch, auf den rebased werden soll. Standardmäßig ist dies `upstream`.

Wenn Konflikte auftreten, die nicht automatisch gelöst werden können, wird der Rebase abgebrochen, und das Repository sowie der Arbeitsbaum bleiben in ihrem ursprünglichen Zustand, und die Funktion wirft einen `GitError`. Dies entspricht ungefähr der folgenden Befehlszeile:

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```

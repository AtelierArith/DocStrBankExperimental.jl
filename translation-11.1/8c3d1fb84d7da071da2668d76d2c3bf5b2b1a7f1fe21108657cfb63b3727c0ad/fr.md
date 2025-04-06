```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

Tentez un rebase de fusion automatique de la branche actuelle, à partir de `upstream` si fourni, ou sinon à partir de la branche de suivi en amont. `newbase` est la branche sur laquelle faire le rebase. Par défaut, c'est `upstream`.

Si des conflits surviennent qui ne peuvent pas être résolus automatiquement, le rebase sera annulé, laissant le dépôt et l'arbre de travail dans leur état d'origine, et la fonction lancera une `GitError`. Cela équivaut à peu près à l'instruction de ligne de commande suivante :

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```

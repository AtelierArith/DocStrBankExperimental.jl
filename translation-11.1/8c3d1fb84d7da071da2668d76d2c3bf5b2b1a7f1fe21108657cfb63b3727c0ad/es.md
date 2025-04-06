```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

Intenta un rebase de fusión automático de la rama actual, desde `upstream` si se proporciona, o de lo contrario desde la rama de seguimiento upstream. `newbase` es la rama a la que se va a rebasear. Por defecto, esto es `upstream`.

Si surgen conflictos que no se pueden resolver automáticamente, el rebase se abortará, dejando el repositorio y el árbol de trabajo en su estado original, y la función lanzará un `GitError`. Esto es aproximadamente equivalente a la siguiente declaración de línea de comandos:

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```

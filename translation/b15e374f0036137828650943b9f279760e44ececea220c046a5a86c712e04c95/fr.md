# Reporting and analyzing crashes (segfaults)

Alors vous avez réussi à casser Julia. Félicitations ! Voici quelques procédures générales que vous pouvez suivre pour des symptômes courants rencontrés lorsque quelque chose ne va pas. Inclure les informations de ces étapes de débogage peut grandement aider les mainteneurs à identifier un segfault ou à comprendre pourquoi votre script s'exécute plus lentement que prévu.

Si vous avez été dirigé vers cette page, trouvez le symptôme qui correspond le mieux à ce que vous ressentez et suivez les instructions pour générer les informations de débogage demandées.  Tableau des symptômes :

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

Peu importe l'erreur, nous aurons toujours besoin de savoir quelle version de Julia vous utilisez. Lorsque Julia démarre pour la première fois, un en-tête est imprimé avec un numéro de version et une date. Veuillez également inclure la sortie de `versioninfo()` (exporté de la bibliothèque standard [`InteractiveUtils`](@ref InteractiveUtils.versioninfo)) dans tout rapport que vous créez :

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

Les segfaults vers la fin du processus `make` de construction de Julia sont un symptôme courant de quelque chose qui ne va pas pendant que Julia pré-analyse le corpus de code dans le dossier `base/`. De nombreux facteurs peuvent contribuer à ce que ce processus meure de manière inattendue, cependant, il s'agit aussi souvent d'une erreur dans la partie C du code de Julia, et doit donc généralement être débogué avec une construction de débogage à l'intérieur de `gdb`. Explicitement :

Créer une build de débogage de Julia :

```
$ cd <julia_root>
$ make debug
```

Notez que ce processus échouera probablement avec la même erreur qu'une invocation normale de `make`, cependant cela créera un exécutable de débogage qui offrira à `gdb` les symboles de débogage nécessaires pour obtenir des backtraces précises. Ensuite, exécutez manuellement le processus de bootstrap à l'intérieur de `gdb` :

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

Cela va démarrer `gdb`, tenter d'exécuter le processus de bootstrap en utilisant la version de débogage de Julia, et imprimer une trace de pile si (quand) cela provoque un segfault. Vous devrez peut-être appuyer sur `<enter>` quelques fois pour obtenir la trace de pile complète. Créez un [gist](https://gist.github.com) avec la trace de pile, le [version info](@ref dev-version-info), et toute autre information pertinente que vous pouvez penser et ouvrez un nouveau [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) sur Github avec un lien vers le gist.

## Segfaults when running a script

La procédure est très similaire à [Segfaults during bootstrap (`sysimg.jl`)](@ref). Créez une version de débogage de Julia et exécutez votre script à l'intérieur d'un processus Julia débogué :

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

Notez que `gdb` restera là, attendant des instructions. Tapez `r` pour exécuter le processus, et `bt` pour générer une trace de pile une fois qu'il a provoqué une erreur de segmentation :

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

Créer un [gist](https://gist.github.com) avec la trace de retour, le [version info](@ref dev-version-info), et toute autre information pertinente que vous pouvez penser et ouvrir un nouveau [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) sur Github avec un lien vers le gist.

## Errors during Julia startup

Occasionnellement, des erreurs se produisent lors du processus de démarrage de Julia (en particulier lors de l'utilisation de distributions binaires, par opposition à la compilation à partir du code source) telles que les suivantes :

```julia
$ julia
exec: error -5
```

Ces erreurs indiquent généralement que quelque chose ne se charge pas correctement très tôt dans la phase de démarrage, et notre meilleur moyen de déterminer ce qui ne va pas est d'utiliser des outils externes pour auditer l'activité disque du processus `julia` :

  * Sur Linux, utilisez `strace` :

    ```
    $ strace julia
    ```
  * Sur OSX, utilisez `dtruss` :

    ```
    $ dtruss -f julia
    ```

Créer un [gist](https://gist.github.com) avec la sortie `strace`/ `dtruss`, le [version info](@ref dev-version-info), et toute autre information pertinente et ouvrir un nouveau [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) sur Github avec un lien vers le gist.

## Other generic segfaults or unreachables reached

Comme mentionné ailleurs, `julia` a une bonne intégration avec `rr` pour générer des traces ; cela inclut, sous Linux, la capacité d'exécuter automatiquement `julia` sous `rr` et de partager la trace après un crash. Cela peut être extrêmement utile lors du débogage de tels crashes et est fortement recommandé lors de la signalisation de problèmes de crash au dépôt JuliaLang/julia. Pour exécuter `julia` automatiquement sous `rr`, faites :

```julia
julia --bug-report=rr
```

Pour générer la trace `rr` localement, mais ne pas la partager, vous pouvez faire :

```julia
julia --bug-report=rr-local
```

Notez que cela ne fonctionne que sur Linux. Le billet de blog sur [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/) contient beaucoup plus de détails.

## Glossary

Quelques termes ont été utilisés comme abréviations dans ce guide :

  * `<julia_root>` fait référence au répertoire racine de l'arborescence source de Julia ; par exemple, il devrait contenir des dossiers tels que `base`, `deps`, `src`, `test`, etc.....

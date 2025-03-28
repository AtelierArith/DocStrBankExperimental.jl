```
try/catch
```

Une instruction `try`/`catch` permet d'intercepter les erreurs (exceptions) lancées par [`throw`](@ref) afin que l'exécution du programme puisse se poursuivre. Par exemple, le code suivant tente d'écrire un fichier, mais avertit l'utilisateur et continue au lieu de terminer l'exécution si le fichier ne peut pas être écrit :

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "Could not write file."
end
```

ou, lorsque le fichier ne peut pas être lu dans une variable :

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "File not found."
end
```

La syntaxe `catch e` (où `e` est n'importe quelle variable) assigne l'objet d'exception lancé à la variable donnée dans le bloc `catch`.

La puissance de la construction `try`/`catch` réside dans la capacité de défaire immédiatement un calcul profondément imbriqué à un niveau beaucoup plus élevé dans la pile des fonctions appelantes.

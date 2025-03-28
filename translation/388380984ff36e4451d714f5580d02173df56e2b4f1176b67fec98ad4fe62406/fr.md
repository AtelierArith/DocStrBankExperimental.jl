```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## configuration avant le test ##
    @arg_test arg begin
        arg :: ArgWrite
        ## test utilisant `arg` ##
    end
    ## nettoyage après le test ##
end
```

La fonction `arg_writers` prend un bloc do, qui est invoqué une fois pour chaque type d'écrivain de test que `arg_write` peut gérer avec un `path` temporaire (inexistant) et `arg` qui peut être converti en divers types d'arguments écrits qui écrivent dans `path`. Si l'argument optionnel `type` est donné, alors le bloc do n'est invoqué que pour les écrivains qui produisent des arguments de ce type.

L'`arg` passé au bloc do n'est pas la valeur de l'argument elle-même, car certains types d'arguments de test doivent être initialisés et finalisés pour chaque cas de test. Considérez un argument de gestionnaire de fichier ouvert : une fois que vous l'avez utilisé pour un test, vous ne pouvez pas l'utiliser à nouveau ; vous devez le fermer et ouvrir le fichier à nouveau pour le test suivant. Cette fonction `arg` peut être convertie en une instance `ArgWrite` en utilisant `@arg_test arg begin ... end`.

Il existe également une méthode `arg_writers` qui prend un nom de chemin comme `arg_readers` :

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## configuration avant le test ##
    @arg_test arg begin
        # ici `arg :: ArgWrite`
        ## test utilisant `arg` ##
    end
    ## nettoyage après le test ##
end
```

Cette méthode est utile si vous devez spécifier `path` au lieu d'utiliser un nom de chemin généré par `tempname()`. Puisque `path` est passé de l'extérieur de `arg_writers`, le chemin n'est pas un argument du bloc do dans cette forme.

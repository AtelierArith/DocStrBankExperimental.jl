```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## configuration avant le test ##
    @arg_test arg begin
        arg :: ArgRead
        ## test utilisant `arg` ##
    end
    ## nettoyage après le test ##
end
```

La fonction `arg_readers` prend un chemin à lire et un bloc do à un argument, qui est invoqué une fois pour chaque type de lecteur de test que `arg_read` peut gérer. Si l'argument optionnel `type` est donné, alors le bloc do n'est invoqué que pour les lecteurs qui produisent des arguments de ce type.

L'`arg` passé au bloc do n'est pas la valeur de l'argument elle-même, car certains types d'arguments de test doivent être initialisés et finalisés pour chaque cas de test. Considérez un argument de gestionnaire de fichier ouvert : une fois que vous l'avez utilisé pour un test, vous ne pouvez pas l'utiliser à nouveau ; vous devez le fermer et ouvrir le fichier à nouveau pour le test suivant. Cette fonction `arg` peut être convertie en une instance `ArgRead` en utilisant `@arg_test arg begin ... end`.

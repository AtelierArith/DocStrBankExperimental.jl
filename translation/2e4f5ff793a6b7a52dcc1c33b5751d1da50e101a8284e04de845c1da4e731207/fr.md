```
edit(function, [types])
edit(module)
```

Modifiez la définition d'une fonction, en spécifiant éventuellement un tuple de types pour indiquer quelle méthode modifier. Pour les modules, ouvrez le fichier source principal. Le module doit d'abord être chargé avec `using` ou `import`.

!!! compat "Julia 1.1"
    `edit` sur les modules nécessite au moins Julia 1.1.


Pour vous assurer que le fichier peut être ouvert à la ligne donnée, vous devrez peut-être appeler `InteractiveUtils.define_editor` d'abord.

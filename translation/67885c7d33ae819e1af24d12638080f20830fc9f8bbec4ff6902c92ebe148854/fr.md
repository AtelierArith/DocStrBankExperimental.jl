```
LibGit2.DescribeFormatOptions
```

Correspond à la structure [`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `abbreviated_size` : limite inférieure sur la taille du `GitHash` abrégé à utiliser, par défaut `7`.
  * `always_use_long_format` : défini sur `1` pour utiliser le format long pour les chaînes même si un format court peut être utilisé.
  * `dirty_suffix` : s'il est défini, cela sera ajouté à la fin de la chaîne de description si le [`workdir`](@ref) est sale.

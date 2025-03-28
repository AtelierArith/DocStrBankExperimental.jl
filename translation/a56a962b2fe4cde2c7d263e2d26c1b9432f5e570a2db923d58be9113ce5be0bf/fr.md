```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

Retourne un tableau markdown donnant des informations sur les variables globales publiques dans un module, éventuellement restreintes à celles correspondant à `pattern`.

L'estimation de la consommation mémoire est une limite inférieure approximative de la taille de la structure interne de l'objet.

  * `all` : liste également les objets non publics définis dans le module, les objets obsolètes et les objets générés par le compilateur.
  * `imported` : liste également les objets explicitement importés d'autres modules.
  * `recursive` : inclut récursivement les objets dans les sous-modules, en respectant les mêmes paramètres dans chaque.
  * `sortby` : la colonne par laquelle trier les résultats. Les options sont `:name` (par défaut), `:size` et `:summary`.
  * `minsize` : inclut uniquement les objets d'une taille d'au moins `minsize` octets. Par défaut, c'est `0`.

La sortie de `varinfo` est destinée à des fins d'affichage uniquement. Voir aussi [`names`](@ref) pour obtenir un tableau de symboles définis dans un module, qui est adapté à des manipulations plus générales.

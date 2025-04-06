```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

Logger avec un formatage optimisé pour la lisibilité dans une console texte, par exemple pour un travail interactif avec le REPL Julia.

Les niveaux de journalisation inférieurs à `min_level` sont filtrés.

Le formatage des messages peut être contrôlé en définissant des arguments de mot-clé :

  * `meta_formatter` est une fonction qui prend les métadonnées de l'événement de journalisation `(level, _module, group, id, file, line)` et retourne une couleur (comme serait passé à printstyled), un préfixe et un suffixe pour le message de journalisation.  La valeur par défaut est de préfixer avec le niveau de journalisation et un suffixe contenant le module, le fichier et la ligne.
  * `show_limited` limite l'impression des grandes structures de données à quelque chose qui peut tenir sur l'écran en définissant la clé `:limit` `IOContext` lors du formatage.
  * `right_justify` est la colonne entière à laquelle les métadonnées de journalisation sont justifiées à droite. La valeur par défaut est zéro (les métadonnées vont sur leur propre ligne).

```
LOAD_PATH
```

Un tableau de chemins pour les instructions `using` et `import` à considérer comme des environnements de projet ou des répertoires de paquets lors du chargement de code. Il est peuplé en fonction de la variable d'environnement [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) si elle est définie ; sinon, il par défaut à `["@", "@v#.#", "@stdlib"]`. Les entrées commençant par `@` ont des significations spéciales :

  * `@` fait référence à "l'environnement actif actuel", dont la valeur initiale est déterminée par la variable d'environnement [`JULIA_PROJECT`](@ref JULIA_PROJECT) ou l'option de ligne de commande `--project`.
  * `@stdlib` s'étend au chemin absolu du répertoire de la bibliothèque standard de l'installation actuelle de Julia.
  * `@name` fait référence à un environnement nommé, qui est stocké dans des dépôts (voir [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)) sous le sous-répertoire `environments`. Les environnements nommés de l'utilisateur sont stockés dans `~/.julia/environments`, donc `@name` ferait référence à l'environnement dans `~/.julia/environments/name` s'il existe et contient un fichier `Project.toml`. Si `name` contient des caractères `#`, alors ils sont remplacés par les composants majeur, mineur et correctif du numéro de version de Julia. Par exemple, si vous exécutez Julia 1.2, alors `@v#.#` s'étend à `@v1.2` et cherchera un environnement par ce nom, généralement à `~/.julia/environments/v1.2`.

La valeur entièrement étendue de `LOAD_PATH` qui est recherchée pour les projets et les paquets peut être vue en appelant la fonction `Base.load_path()`.

Voir aussi [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), [`JULIA_PROJECT`](@ref JULIA_PROJECT), [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), et [Chargement de code](@ref code-loading).

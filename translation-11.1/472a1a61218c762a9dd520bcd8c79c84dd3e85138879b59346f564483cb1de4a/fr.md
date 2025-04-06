```
require(into::Module, module::Symbol)
```

Cette fonction fait partie de l'implémentation de [`using`](@ref) / [`import`](@ref), si un module n'est pas déjà défini dans `Main`. Elle peut également être appelée directement pour forcer le rechargement d'un module, peu importe s'il a été chargé auparavant (par exemple, lors du développement interactif de bibliothèques).

Charge un fichier source, dans le contexte du module `Main`, sur chaque nœud actif, en recherchant des emplacements standards pour les fichiers. `require` est considérée comme une opération de haut niveau, donc elle définit le chemin `include` actuel mais ne l'utilise pas pour rechercher des fichiers (voir l'aide pour [`include`](@ref)). Cette fonction est généralement utilisée pour charger du code de bibliothèque, et est appelée implicitement par `using` pour charger des paquets.

Lors de la recherche de fichiers, `require` commence par chercher du code de paquet dans le tableau global [`LOAD_PATH`](@ref). `require` est sensible à la casse sur toutes les plateformes, y compris celles avec des systèmes de fichiers insensibles à la casse comme macOS et Windows.

Pour plus de détails concernant le chargement de code, voir les sections du manuel sur [modules](@ref modules) et [calcul parallèle](@ref code-availability).

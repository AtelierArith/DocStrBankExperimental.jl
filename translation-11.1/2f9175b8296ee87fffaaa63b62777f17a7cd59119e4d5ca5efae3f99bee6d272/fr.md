```
DEPOT_PATH
```

Une pile de lieux "depot" où le gestionnaire de paquets, ainsi que les mécanismes de chargement de code de Julia, recherchent des registres de paquets, des paquets installés, des environnements nommés, des clones de dépôts, des images de paquets compilés mises en cache et des fichiers de configuration. Par défaut, cela inclut :

1. `~/.julia` où `~` est le répertoire personnel de l'utilisateur selon le système ;
2. un répertoire système partagé spécifique à l'architecture, par exemple `/usr/local/share/julia` ;
3. un répertoire système partagé indépendant de l'architecture, par exemple `/usr/share/julia`.

Ainsi, `DEPOT_PATH` pourrait être :

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

La première entrée est le "depot utilisateur" et doit être accessible en écriture et appartenir à l'utilisateur actuel. Le depot utilisateur est l'endroit où : les registres sont clonés, de nouvelles versions de paquets sont installées, des environnements nommés sont créés et mis à jour, des dépôts de paquets sont clonés, de nouveaux fichiers d'images de paquets compilés sont enregistrés, des fichiers journaux sont écrits, des paquets de développement sont vérifiés par défaut, et des données de configuration globales sont enregistrées. Les entrées ultérieures dans le chemin du depot sont considérées comme en lecture seule et sont appropriées pour les registres, les paquets, etc. installés et gérés par les administrateurs système.

`DEPOT_PATH` est peuplé en fonction de la variable d'environnement [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) si elle est définie.

## Contenu de DEPOT_PATH

Chaque entrée dans `DEPOT_PATH` est un chemin vers un répertoire qui contient des sous-répertoires utilisés par Julia à diverses fins. Voici un aperçu de certains des sous-répertoires qui peuvent exister dans un depot :

  * `artifacts` : Contient le contenu que les paquets utilisent pour lequel Pkg gère l'installation.
  * `clones` : Contient des clones complets de dépôts de paquets. Maintenu par `Pkg.jl` et utilisé comme cache.
  * `config` : Contient la configuration au niveau de Julia, comme un `startup.jl`.
  * `compiled` : Contient des fichiers `*.ji` précompilés pour les paquets. Maintenu par Julia.
  * `dev` : Répertoire par défaut pour `Pkg.develop`. Maintenu par `Pkg.jl` et l'utilisateur.
  * `environments` : Environnements de paquets par défaut. Par exemple, l'environnement global pour une version spécifique de Julia. Maintenu par `Pkg.jl`.
  * `logs` : Contient des journaux des opérations `Pkg` et `REPL`. Maintenu par `Pkg.jl` et `Julia`.
  * `packages` : Contient des paquets, dont certains ont été explicitement installés et d'autres qui sont des dépendances implicites. Maintenu par `Pkg.jl`.
  * `registries` : Contient des registres de paquets. Par défaut, seulement `General`. Maintenu par `Pkg.jl`.
  * `scratchspaces` : Contient le contenu qu'un paquet lui-même installe via le paquet [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl). `Pkg.gc()` supprimera le contenu qui est connu pour être inutilisé.

!!! note
    Les paquets qui souhaitent stocker du contenu doivent utiliser le sous-répertoire `scratchspaces` via [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) au lieu de créer de nouveaux sous-répertoires dans la racine du depot.


Voir aussi [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), et [Chargement de Code](@ref code-loading).

```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> collection
```

Transformez la collection `c` en appliquant `f` à chaque élément en utilisant les travailleurs et tâches disponibles.

Pour plusieurs arguments de collection, appliquez `f` élément par élément.

Notez que `f` doit être rendu disponible à tous les processus de travailleur ; voir [Code Availability and Loading Packages](@ref code-availability) pour plus de détails.

Si un pool de travailleurs n'est pas spécifié, tous les travailleurs disponibles seront utilisés via un [`CachingPool`](@ref).

Par défaut, `pmap` distribue le calcul sur tous les travailleurs spécifiés. Pour utiliser uniquement le processus local et distribuer sur les tâches, spécifiez `distributed=false`. Cela équivaut à utiliser [`asyncmap`](@ref). Par exemple, `pmap(f, c; distributed=false)` est équivalent à `asyncmap(f,c; ntasks=()->nworkers())`

`pmap` peut également utiliser un mélange de processus et de tâches via l'argument `batch_size`. Pour des tailles de lot supérieures à 1, la collection est traitée en plusieurs lots, chacun d'une longueur de `batch_size` ou moins. Un lot est envoyé comme une seule demande à un travailleur libre, où un [`asyncmap`](@ref) local traite les éléments du lot en utilisant plusieurs tâches concurrentes.

Toute erreur empêche `pmap` de traiter le reste de la collection. Pour remplacer ce comportement, vous pouvez spécifier une fonction de gestion des erreurs via l'argument `on_error` qui prend un seul argument, c'est-à-dire l'exception. La fonction peut arrêter le traitement en relançant l'erreur, ou, pour continuer, retourner toute valeur qui est ensuite renvoyée en ligne avec les résultats à l'appelant.

Considérez les deux exemples suivants. Le premier renvoie l'objet d'exception en ligne, le second un 0 à la place de toute exception :

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

Les erreurs peuvent également être gérées en réessayant les calculs échoués. Les arguments de mot-clé `retry_delays` et `retry_check` sont transmis à [`retry`](@ref) en tant qu'arguments de mot-clé `delays` et `check` respectivement. Si le regroupement est spécifié, et qu'un lot entier échoue, tous les éléments du lot sont réessayés.

Notez que si à la fois `on_error` et `retry_delays` sont spécifiés, le crochet `on_error` est appelé avant de réessayer. Si `on_error` ne lance pas (ou ne relance pas) une exception, l'élément ne sera pas réessayé.

Exemple : En cas d'erreurs, réessayez `f` sur un élément un maximum de 3 fois sans aucun délai entre les réessais.

```julia
pmap(f, c; retry_delays = zeros(3))
```

Exemple : Réessayez `f` uniquement si l'exception n'est pas de type [`InexactError`](@ref), avec des délais augmentant de manière exponentielle jusqu'à 3 fois. Retournez un `NaN` à la place de toutes les occurrences de `InexactError`.

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```

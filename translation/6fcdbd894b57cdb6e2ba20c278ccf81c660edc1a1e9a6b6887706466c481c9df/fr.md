```
rand([rng=default_rng()], [S], [dims...])
```

Choisissez un élément aléatoire ou un tableau d'éléments aléatoires à partir de l'ensemble de valeurs spécifié par `S` ; `S` peut être

  * une collection indexable (par exemple `1:9` ou `('x', "y", :z)`)
  * un objet `AbstractDict` ou `AbstractSet`
  * une chaîne de caractères (considérée comme une collection de caractères), ou
  * un type de la liste ci-dessous, correspondant à l'ensemble de valeurs spécifié

      * les types entiers concrets échantillonnent de `typemin(S):typemax(S)` (à l'exception de [`BigInt`](@ref) qui n'est pas supporté)
      * les types de nombres à virgule flottante concrets échantillonnent de `[0, 1)`
      * les types complexes concrets `Complex{T}` si `T` est un type échantillonnable prennent leurs composants réels et imaginaires indépendamment de l'ensemble de valeurs correspondant à `T`, mais ne sont pas supportés si `T` n'est pas échantillonnable.
      * tous les types `<:AbstractChar` échantillonnent de l'ensemble des scalaires Unicode valides
      * un type défini par l'utilisateur et un ensemble de valeurs ; pour des conseils de mise en œuvre, veuillez consulter [Hooking into the `Random` API](@ref rand-api-hook)
      * un type de tuple de taille connue et où chaque paramètre de `S` est lui-même un type échantillonnable ; renvoie une valeur de type `S`. Notez que les types de tuple tels que `Tuple{Vararg{T}}` (taille inconnue) et `Tuple{1:2}` (paramétré avec une valeur) ne sont pas supportés
      * un type `Pair`, par exemple `Pair{X, Y}` tel que `rand` est défini pour `X` et `Y`, auquel cas des paires aléatoires sont produites.

`S` par défaut à [`Float64`](@ref). Lorsque seul un argument est passé en plus de l'optionnel `rng` et est un `Tuple`, il est interprété comme une collection de valeurs (`S`) et non comme `dims`.

Voir aussi [`randn`](@ref) pour des nombres distribués normalement, et [`rand!`](@ref) et [`randn!`](@ref) pour les équivalents en place.

!!! compat "Julia 1.1"
    Le support de `S` en tant que tuple nécessite au moins Julia 1.1.


!!! compat "Julia 1.11"
    Le support de `S` en tant que type `Tuple` nécessite au moins Julia 1.11.


# Exemples

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    La complexité de `rand(rng, s::Union{AbstractDict,AbstractSet})` est linéaire par rapport à la longueur de `s`, sauf si une méthode optimisée avec une complexité constante est disponible, ce qui est le cas pour `Dict`, `Set` et les `BitSet`s denses. Pour plus de quelques appels, utilisez `rand(rng, collect(s))` à la place, ou soit `rand(rng, Dict(s))` ou `rand(rng, Set(s))` selon le cas.


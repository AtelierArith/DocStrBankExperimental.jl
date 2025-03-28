# Sorting and Related Functions

Julia dispose d'une API étendue et flexible pour trier et interagir avec des tableaux de valeurs déjà triés. Par défaut, Julia choisit des algorithmes raisonnables et trie par ordre croissant :

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

Vous pouvez trier dans l'ordre inverse également :

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort` construit une copie triée sans modifier son entrée. Utilisez la version "bang" de la fonction de tri pour muter un tableau existant :

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

Au lieu de trier directement un tableau, vous pouvez calculer une permutation des indices du tableau qui met le tableau dans l'ordre trié :

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Les tableaux peuvent être triés selon une transformation arbitraire de leurs valeurs :

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

Ou dans l'ordre inverse par une transformation :

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

Si nécessaire, l'algorithme de tri peut être choisi :

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Toutes les fonctions liées au tri et à l'ordre reposent sur une relation "inférieure à" définissant un [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) sur les valeurs à manipuler. La fonction `isless` est invoquée par défaut, mais la relation peut être spécifiée via le mot-clé `lt`, une fonction qui prend deux éléments de tableau et retourne `true` si et seulement si le premier argument est "inférieur à" le second. Voir [`sort!`](@ref) et [Alternate Orderings](@ref) pour plus d'informations.

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

Il existe actuellement quatre algorithmes de tri disponibles publiquement dans Julia de base :

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

Par défaut, la famille de fonctions `sort` utilise des algorithmes de tri stables qui sont rapides sur la plupart des entrées. Le choix exact de l'algorithme est un détail d'implémentation pour permettre de futures améliorations de performance. Actuellement, un hybride de `RadixSort`, `ScratchQuickSort`, `InsertionSort` et `CountingSort` est utilisé en fonction du type, de la taille et de la composition des entrées. Les détails d'implémentation sont susceptibles de changer mais sont actuellement disponibles dans l'aide étendue de `??Base.DEFAULT_STABLE` et les docstrings des algorithmes de tri internes qui y sont listés.

Vous pouvez spécifier explicitement votre algorithme préféré avec le mot-clé `alg` (par exemple, `sort!(v, alg=PartialQuickSort(10:20))`) ou reconfigurer l'algorithme de tri par défaut pour les types personnalisés en ajoutant une méthode spécialisée à la fonction `Base.Sort.defalg`. Par exemple, [InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903) définit la méthode suivante :

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    L'algorithme de tri par défaut (retourné par `Base.Sort.defalg`) est garanti d'être stable depuis Julia 1.9. Les versions précédentes avaient des cas limites instables lors du tri des tableaux numériques.


## Alternate Orderings

Par défaut, `sort`, `searchsorted` et les fonctions connexes utilisent [`isless`](@ref) pour comparer deux éléments afin de déterminer lequel doit venir en premier. Le type abstrait [`Base.Order.Ordering`](@ref) fournit un mécanisme pour définir des ordres alternatifs sur le même ensemble d'éléments : lors de l'appel d'une fonction de tri comme `sort!`, une instance de `Ordering` peut être fournie avec l'argument clé `order`.

Les instances de `Ordering` définissent un ordre à travers la fonction [`Base.Order.lt`](@ref), qui fonctionne comme une généralisation de `isless`. Le comportement de cette fonction sur des `Ordering`s personnalisés doit satisfaire toutes les conditions d'un [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings). Voir [`sort!`](@ref) pour des détails et des exemples de fonctions `lt` valides et invalides.

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```

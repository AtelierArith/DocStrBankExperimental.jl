# Interfaces

Une grande partie de la puissance et de l'extensibilité de Julia provient d'une collection d'interfaces informelles. En étendant quelques méthodes spécifiques pour fonctionner avec un type personnalisé, les objets de ce type non seulement reçoivent ces fonctionnalités, mais ils peuvent également être utilisés dans d'autres méthodes qui sont écrites pour s'appuyer de manière générique sur ces comportements.

## [Iteration](@id man-interface-iteration)

Il y a deux méthodes qui sont toujours requises :

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

Il existe plusieurs autres méthodes qui devraient être définies dans certaines circonstances. Veuillez noter que vous devez toujours définir au moins l'une des méthodes `Base.IteratorSize(IterType)` et `length(iter)` car la définition par défaut de `Base.IteratorSize(IterType)` est `Base.HasLength()`.

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

L'itération séquentielle est implémentée par la fonction [`iterate`](@ref). Au lieu de muter les objets au fur et à mesure qu'ils sont itérés, les itérateurs Julia peuvent suivre l'état d'itération en dehors de l'objet. La valeur de retour de l'itération est toujours soit un tuple d'une valeur et d'un état, soit `nothing` s'il n'y a plus d'éléments. L'objet d'état sera renvoyé à la fonction d'itération lors de la prochaine itération et est généralement considéré comme un détail d'implémentation privé à l'objet itérable.

Tout objet qui définit cette fonction est itérable et peut être utilisé dans le [many functions that rely upon iteration](@ref lib-collections-iteration). Il peut également être utilisé directement dans une boucle [`for`](@ref) puisque la syntaxe :

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

est traduit en :

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

Un exemple simple est une séquence itérable de nombres carrés avec une longueur définie :

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

Avec seulement [`iterate`](@ref) définition, le type `Squares` est déjà assez puissant. Nous pouvons itérer sur tous les éléments :

```jldoctest squaretype
julia> for item in Squares(7)
           println(item)
       end
1
4
9
16
25
36
49
```

Nous pouvons utiliser de nombreuses méthodes intégrées qui fonctionnent avec des itérables, comme [`in`](@ref) ou [`sum`](@ref) :

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

Il existe quelques autres méthodes que nous pouvons étendre pour donner à Julia plus d'informations sur cette collection itérable. Nous savons que les éléments d'une séquence `Squares` seront toujours des `Int`. En étendant la méthode [`eltype`](@ref), nous pouvons donner cette information à Julia et l'aider à générer un code plus spécialisé dans les méthodes plus compliquées. Nous savons également le nombre d'éléments dans notre séquence, donc nous pouvons également étendre [`length`](@ref).

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

Maintenant, lorsque nous demandons à Julia de [`collect`](@ref) tous les éléments dans un tableau, elle peut préallouer un `Vector{Int}` de la bonne taille au lieu de naïvement [`push!`](@ref) chaque élément dans un `Vector{Any}` :

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

Bien que nous puissions nous fier à des implémentations génériques, nous pouvons également étendre des méthodes spécifiques lorsque nous savons qu'il existe un algorithme plus simple. Par exemple, il existe une formule pour calculer la somme des carrés, nous pouvons donc remplacer la version itérative générique par une solution plus performante :

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

C'est un modèle très courant dans Julia Base : un petit ensemble de méthodes requises définit une interface informelle qui permet de nombreux comportements plus sophistiqués. Dans certains cas, les types voudront également spécialiser ces comportements supplémentaires lorsqu'ils savent qu'un algorithme plus efficace peut être utilisé dans leur cas spécifique.

Il est également souvent utile de permettre l'itération sur une collection dans *l'ordre inverse* en itérant sur [`Iterators.reverse(iterator)`](@ref). Pour réellement prendre en charge l'itération dans l'ordre inverse, cependant, un type d'itérateur `T` doit implémenter `iterate` pour `Iterators.Reverse{T}`. (Étant donné `r::Iterators.Reverse{T}`, l'itérateur sous-jacent de type `T` est `r.itr`.) Dans notre exemple `Squares`, nous implémenterions les méthodes `Iterators.Reverse{Squares}` :

```jldoctest squaretype
julia> Base.iterate(rS::Iterators.Reverse{Squares}, state=rS.itr.count) = state < 1 ? nothing : (state*state, state-1)

julia> collect(Iterators.reverse(Squares(4)))
4-element Vector{Int64}:
 16
  9
  4
  1
```

## Indexing

| Methods to implement | Brief description                                             |
|:-------------------- |:------------------------------------------------------------- |
| `getindex(X, i)`     | `X[i]`, indexed access, non-scalar `i` should allocate a copy |
| `setindex!(X, v, i)` | `X[i] = v`, indexed assignment                                |
| `firstindex(X)`      | The first index, used in `X[begin]`                           |
| `lastindex(X)`       | The last index, used in `X[end]`                              |

Pour l'itérable `Squares` ci-dessus, nous pouvons facilement calculer le `i`ème élément de la séquence en le mettant au carré. Nous pouvons exposer cela comme une expression d'indexation `S[i]`. Pour opter pour ce comportement, `Squares` doit simplement définir [`getindex`](@ref) :

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

De plus, pour prendre en charge la syntaxe `S[begin]` et `S[end]`, nous devons définir [`firstindex`](@ref) et [`lastindex`](@ref) pour spécifier les premiers et derniers indices valides, respectivement :

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

Pour l'indexation multi-dimensionnelle `begin`/`end` comme dans `a[3, begin, 7]`, par exemple, vous devez définir `firstindex(a, dim)` et `lastindex(a, dim)` (qui appellent par défaut `first` et `last` sur `axes(a, dim)`, respectivement).

Notez cependant que ce qui précède *définit uniquement* [`getindex`](@ref) avec un seul index entier. L'indexation avec autre chose qu'un `Int` générera un [`MethodError`](@ref) indiquant qu'il n'y avait pas de méthode correspondante. Afin de prendre en charge l'indexation avec des plages ou des vecteurs d'`Int`, des méthodes séparées doivent être écrites :

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

Bien que cela commence à prendre en charge davantage de [indexing operations supported by some of the builtin types](@ref man-array-indexing), il reste encore un certain nombre de comportements manquants. Cette séquence `Squares` commence à ressembler de plus en plus à un vecteur à mesure que nous y ajoutons des comportements. Au lieu de définir tous ces comportements nous-mêmes, nous pouvons officiellement le définir comme un sous-type de [`AbstractArray`](@ref).

## [Abstract Arrays](@id man-interface-array)

| Methods to implement                     |                                        | Brief description                                                                                                                                                |
|:---------------------------------------- |:-------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `size(A)`                                |                                        | Returns a tuple containing the dimensions of `A`                                                                                                                 |
| `getindex(A, i::Int)`                    |                                        | (if `IndexLinear`) Linear scalar indexing                                                                                                                        |
| `getindex(A, I::Vararg{Int, N})`         |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexing                                                                                        |
| **Optional methods**                     | **Default definition**                 | **Brief description**                                                                                                                                            |
| `IndexStyle(::Type)`                     | `IndexCartesian()`                     | Returns either `IndexLinear()` or `IndexCartesian()`. See the description below.                                                                                 |
| `setindex!(A, v, i::Int)`                |                                        | (if `IndexLinear`) Scalar indexed assignment                                                                                                                     |
| `setindex!(A, v, I::Vararg{Int, N})`     |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexed assignment                                                                              |
| `getindex(A, I...)`                      | defined in terms of scalar `getindex`  | [Multidimensional and nonscalar indexing](@ref man-array-indexing)                                                                                               |
| `setindex!(A, X, I...)`                  | defined in terms of scalar `setindex!` | [Multidimensional and nonscalar indexed assignment](@ref man-array-indexing)                                                                                     |
| `iterate`                                | defined in terms of scalar `getindex`  | Iteration                                                                                                                                                        |
| `length(A)`                              | `prod(size(A))`                        | Number of elements                                                                                                                                               |
| `similar(A)`                             | `similar(A, eltype(A), size(A))`       | Return a mutable array with the same shape and element type                                                                                                      |
| `similar(A, ::Type{S})`                  | `similar(A, S, size(A))`               | Return a mutable array with the same shape and the specified element type                                                                                        |
| `similar(A, dims::Dims)`                 | `similar(A, eltype(A), dims)`          | Return a mutable array with the same element type and size *dims*                                                                                                |
| `similar(A, ::Type{S}, dims::Dims)`      | `Array{S}(undef, dims)`                | Return a mutable array with the specified element type and size                                                                                                  |
| **Non-traditional indices**              | **Default definition**                 | **Brief description**                                                                                                                                            |
| `axes(A)`                                | `map(OneTo, size(A))`                  | Return a tuple of `AbstractUnitRange{<:Integer}` of valid indices. The axes should be their own axes, that is `axes.(axes(A),1) == axes(A)` should be satisfied. |
| `similar(A, ::Type{S}, inds)`            | `similar(A, S, Base.to_shape(inds))`   | Return a mutable array with the specified indices `inds` (see below)                                                                                             |
| `similar(T::Union{Type,Function}, inds)` | `T(Base.to_shape(inds))`               | Return an array similar to `T` with the specified indices `inds` (see below)                                                                                     |

Si un type est défini comme un sous-type de `AbstractArray`, il hérite d'un très grand ensemble de comportements riches, y compris l'itération et l'indexation multidimensionnelle, basés sur l'accès à un seul élément. Voir le [arrays manual page](@ref man-multi-dim-arrays) et le [Julia Base section](@ref lib-arrays) pour d'autres méthodes prises en charge.

Une partie clé dans la définition d'un sous-type `AbstractArray` est [`IndexStyle`](@ref). Étant donné que l'indexation est une partie si importante d'un tableau et se produit souvent dans des boucles critiques, il est important de rendre à la fois l'indexation et l'assignation indexée aussi efficaces que possible. Les structures de données de tableau sont généralement définies de l'une des deux manières suivantes : soit elles accèdent à leurs éléments de manière la plus efficace en utilisant un seul index (indexation linéaire), soit elles accèdent intrinsèquement aux éléments avec des indices spécifiés pour chaque dimension. Ces deux modalités sont identifiées par Julia comme `IndexLinear()` et `IndexCartesian()`. La conversion d'un index linéaire en plusieurs sous-indices d'indexation est généralement très coûteuse, donc cela fournit un mécanisme basé sur des traits pour permettre un code générique efficace pour tous les types de tableaux.

Cette distinction détermine quels méthodes d'indexation scalaire le type doit définir. Les tableaux `IndexLinear()` sont simples : il suffit de définir `getindex(A::ArrayType, i::Int)`. Lorsque le tableau est ensuite indexé avec un ensemble multidimensionnel d'indices, le `getindex(A::AbstractArray, I...)` de secours convertit efficacement les indices en un seul indice linéaire, puis appelle la méthode ci-dessus. Les tableaux `IndexCartesian()`, en revanche, nécessitent que des méthodes soient définies pour chaque dimensionnalité prise en charge avec des indices `Int` `ndims(A)`. Par exemple, [`SparseMatrixCSC`](@ref) du module de bibliothèque standard `SparseArrays`, ne prend en charge que deux dimensions, donc il définit simplement `getindex(A::SparseMatrixCSC, i::Int, j::Int)`. Il en va de même pour [`setindex!`](@ref).

En revenant à la séquence de carrés ci-dessus, nous pourrions plutôt la définir comme un sous-type de `AbstractArray{Int, 1}` :

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

Notez qu'il est très important de spécifier les deux paramètres de l'`AbstractArray` ; le premier définit le [`eltype`](@ref), et le second définit le [`ndims`](@ref). Ce supertype et ces trois méthodes suffisent pour que `SquaresVector` soit un tableau itérable, indexable et complètement fonctionnel :

```jldoctest squarevectype
julia> s = SquaresVector(4)
4-element SquaresVector:
  1
  4
  9
 16

julia> s[s .> 8]
2-element Vector{Int64}:
  9
 16

julia> s + s
4-element Vector{Int64}:
  2
  8
 18
 32

julia> sin.(s)
4-element Vector{Float64}:
  0.8414709848078965
 -0.7568024953079282
  0.4121184852417566
 -0.2879033166650653
```

En tant qu'exemple plus compliqué, définissons notre propre type de tableau sparse-like N-dimensionnel construit sur [`Dict`](@ref) :

```jldoctest squarevectype
julia> struct SparseArray{T,N} <: AbstractArray{T,N}
           data::Dict{NTuple{N,Int}, T}
           dims::NTuple{N,Int}
       end

julia> SparseArray(::Type{T}, dims::Int...) where {T} = SparseArray(T, dims);

julia> SparseArray(::Type{T}, dims::NTuple{N,Int}) where {T,N} = SparseArray{T,N}(Dict{NTuple{N,Int}, T}(), dims);

julia> Base.size(A::SparseArray) = A.dims

julia> Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where {T} = SparseArray(T, dims)

julia> Base.getindex(A::SparseArray{T,N}, I::Vararg{Int,N}) where {T,N} = get(A.data, I, zero(T))

julia> Base.setindex!(A::SparseArray{T,N}, v, I::Vararg{Int,N}) where {T,N} = (A.data[I] = v)
```

Remarquez qu'il s'agit d'un tableau `IndexCartesian`, donc nous devons définir manuellement [`getindex`](@ref) et [`setindex!`](@ref) à la dimensionnalité du tableau. Contrairement au `SquaresVector`, nous pouvons définir `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566`, et nous pouvons donc muter le tableau :

```jldoctest squarevectype
julia> A = SparseArray(Float64, 3, 3)
3×3 SparseArray{Float64, 2}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2)
3×3 SparseArray{Float64, 2}:
 2.0  2.0  2.0
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> A[:] = 1:length(A); A
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

The result of indexing an `AbstractArray` can itself be an array (for instance when indexing by an `AbstractRange`). The `AbstractArray` fallback methods use [`similar`](@ref) to allocate an `Array` of the appropriate size and element type, which is filled in using the basic indexing method described above. However, when implementing an array wrapper you often want the result to be wrapped as well:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

Dans cet exemple, cela est accompli en définissant `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where T` pour créer le tableau enveloppé approprié. (Notez que bien que `similar` prenne en charge les formes à 1 et 2 arguments, dans la plupart des cas, vous n'avez besoin de spécialiser que la forme à 3 arguments.) Pour que cela fonctionne, il est important que `SparseArray` soit mutable (prenne en charge `setindex!`). Définir `similar`, `getindex` et `setindex!` pour `SparseArray` rend également possible de [`copy`](@ref) le tableau :

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

En plus de toutes les méthodes itérables et indexables mentionnées ci-dessus, ces types peuvent également interagir entre eux et utiliser la plupart des méthodes définies dans Julia Base pour `AbstractArrays` :

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

Si vous définissez un type de tableau qui permet un indexage non traditionnel (indices commençant par autre chose que 1), vous devez spécialiser [`axes`](@ref). Vous devez également spécialiser [`similar`](@ref) afin que l'argument `dims` (ordinairement un tuple de taille `Dims`) puisse accepter des objets `AbstractUnitRange`, peut-être des types de plage `Ind` de votre propre conception. Pour plus d'informations, voir [Arrays with custom indices](@ref man-custom-indices).

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

Un tableau stridé est un sous-type de `AbstractArray` dont les entrées sont stockées en mémoire avec des pas fixes. Étant donné que le type d'élément du tableau est compatible avec BLAS, un tableau stridé peut utiliser les routines BLAS et LAPACK pour des routines d'algèbre linéaire plus efficaces. Un exemple typique d'un tableau stridé défini par l'utilisateur est celui qui enveloppe un `Array` standard avec une structure supplémentaire.

Avertissement : ne mettez pas en œuvre ces méthodes si le stockage sous-jacent n'est pas réellement en pas, car cela peut entraîner des résultats incorrects ou des fautes de segmentation.

Voici quelques exemples pour démontrer quels types de tableaux sont espacés et lesquels ne le sont pas :

```julia
1:5   # not strided (there is no storage associated with this array.)
Vector(1:5)  # is strided with strides (1,)
A = [1 5; 2 6; 3 7; 4 8]  # is strided with strides (1,4)
V = view(A, 1:2, :)   # is strided with strides (1,4)
V = view(A, 1:2:3, 1:2)   # is strided with strides (2,4)
V = view(A, [1,2,4], :)   # is not strided, as the spacing between rows is not fixed.
```

## [Customizing broadcasting](@id man-interfaces-broadcasting)

| Methods to implement                                       | Brief description                                                  |
|:---------------------------------------------------------- |:------------------------------------------------------------------ |
| `Base.BroadcastStyle(::Type{SrcType}) = SrcStyle()`        | Broadcasting behavior of `SrcType`                                 |
| `Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})` | Allocation of output container                                     |
| **Optional methods**                                       |                                                                    |
| `Base.BroadcastStyle(::Style1, ::Style2) = Style12()`      | Precedence rules for mixing styles                                 |
| `Base.axes(x)`                                             | Declaration of the indices of `x`, as per [`axes(x)`](@ref).       |
| `Base.broadcastable(x)`                                    | Convert `x` to an object that has `axes` and supports indexing     |
| **Bypassing default machinery**                            |                                                                    |
| `Base.copy(bc::Broadcasted{DestStyle})`                    | Custom implementation of `broadcast`                               |
| `Base.copyto!(dest, bc::Broadcasted{DestStyle})`           | Custom implementation of `broadcast!`, specializing on `DestStyle` |
| `Base.copyto!(dest::DestType, bc::Broadcasted{Nothing})`   | Custom implementation of `broadcast!`, specializing on `DestType`  |
| `Base.Broadcast.broadcasted(f, args...)`                   | Override the default lazy behavior within a fused expression       |
| `Base.Broadcast.instantiate(bc::Broadcasted{DestStyle})`   | Override the computation of the lazy broadcast's axes              |

[Broadcasting](@ref) est déclenché par un appel explicite à `broadcast` ou `broadcast!`, ou implicitement par des opérations "point" comme `A .+ b` ou `f.(x, y)`. Tout objet qui a [`axes`](@ref) et qui prend en charge l'indexation peut participer en tant qu'argument dans le broadcasting, et par défaut, le résultat est stocké dans un `Array`. Ce cadre de base est extensible de trois manières principales :

  * Assurer que tous les arguments prennent en charge la diffusion
  * Sélection d'un tableau de sortie approprié pour l'ensemble d'arguments donné
  * Sélection d'une implémentation efficace pour l'ensemble d'arguments donné

Tous les types ne prennent pas en charge `axes` et l'indexation, mais beaucoup sont pratiques à autoriser dans le cadre de la diffusion. La fonction [`Base.broadcastable`](@ref) est appelée sur chaque argument à diffuser, permettant de retourner quelque chose de différent qui prend en charge `axes` et l'indexation. Par défaut, il s'agit de la fonction identité pour tous les `AbstractArray`s et `Number`s — ils prennent déjà en charge `axes` et l'indexation.

Si un type est destiné à agir comme un "scalaire 0-dimensionnel" (un seul objet) plutôt que comme un conteneur pour le broadcasting, alors la méthode suivante devrait être définie :

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

cela renvoie l'argument enveloppé dans un conteneur [`Ref`](@ref) de dimension 0. Par exemple, une telle méthode d'enveloppement est définie pour les types eux-mêmes, les fonctions, des singletons spéciaux comme [`missing`](@ref) et [`nothing`](@ref), et les dates.

Les types personnalisés similaires à des tableaux peuvent spécialiser `Base.broadcastable` pour définir leur forme, mais ils doivent suivre la convention selon laquelle `collect(Base.broadcastable(x)) == collect(x)`. Une exception notable est `AbstractString` ; les chaînes de caractères sont traitées de manière spéciale pour se comporter comme des scalaires aux fins de diffusion, même si elles sont des collections itérables de leurs caractères (voir [Strings](@ref) pour plus d'informations).

Les deux étapes suivantes (sélection du tableau de sortie et mise en œuvre) dépendent de la détermination d'une seule réponse pour un ensemble donné d'arguments. Le broadcast doit prendre tous les types variés de ses arguments et les réduire à un seul tableau de sortie et une seule mise en œuvre. Le broadcast appelle cette réponse unique un "style". Chaque objet diffusé a son propre style préféré, et un système de promotion est utilisé pour combiner ces styles en une seule réponse — le "style de destination".

### Broadcast Styles

`Base.BroadcastStyle` est le type abstrait à partir duquel tous les styles de diffusion sont dérivés. Lorsqu'il est utilisé comme une fonction, il a deux formes possibles, unaires (à un seul argument) et binaires. La variante uniaire indique que vous avez l'intention d'implémenter un comportement de diffusion spécifique et/ou un type de sortie, et que vous ne souhaitez pas vous fier à la valeur par défaut [`Broadcast.DefaultArrayStyle`](@ref).

Pour remplacer ces valeurs par défaut, vous pouvez définir un `BroadcastStyle` personnalisé pour votre objet :

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

Dans certains cas, il peut être pratique de ne pas avoir à définir `MyStyle`, auquel cas vous pouvez tirer parti de l'un des wrappers de diffusion généraux :

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()` peut être utilisé pour des types arbitraires.
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()` est préféré si `MyType` est un `AbstractArray`.
  * Pour `AbstractArrays` qui ne supportent qu'une certaine dimensionnalité, créez un sous-type de `Broadcast.AbstractArrayStyle{N}` (voir ci-dessous).

Lorsque votre opération de diffusion implique plusieurs arguments, les styles d'arguments individuels sont combinés pour déterminer un seul `DestStyle` qui contrôle le type du conteneur de sortie. Pour plus de détails, voir [below](@ref writing-binary-broadcasting-rules).

### Selecting an appropriate output array

Le style de diffusion est calculé pour chaque opération de diffusion afin de permettre l'envoi et la spécialisation. L'allocation réelle du tableau de résultats est gérée par `similar`, en utilisant l'objet Broadcasted comme premier argument.

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

La définition de secours est

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

Cependant, si nécessaire, vous pouvez vous spécialiser sur l'un ou l'ensemble de ces arguments. Le dernier argument `bc` est une représentation paresseuse d'une opération de diffusion (potentiellement fusionnée), un objet `Broadcasted`. À ces fins, les champs les plus importants de l'enveloppe sont `f` et `args`, décrivant respectivement la fonction et la liste des arguments. Notez que la liste des arguments peut — et inclut souvent — d'autres enveloppes `Broadcasted` imbriquées.

Pour un exemple complet, disons que vous avez créé un type, `ArrayAndChar`, qui stocke un tableau et un seul caractère :

```jldoctest ArrayAndChar; output = false
struct ArrayAndChar{T,N} <: AbstractArray{T,N}
    data::Array{T,N}
    char::Char
end
Base.size(A::ArrayAndChar) = size(A.data)
Base.getindex(A::ArrayAndChar{T,N}, inds::Vararg{Int,N}) where {T,N} = A.data[inds...]
Base.setindex!(A::ArrayAndChar{T,N}, val, inds::Vararg{Int,N}) where {T,N} = A.data[inds...] = val
Base.showarg(io::IO, A::ArrayAndChar, toplevel) = print(io, typeof(A), " with char '", A.char, "'")
# output

```

Vous voudrez peut-être que la diffusion préserve les `char` "métadonnées". D'abord, nous définissons

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

Cela signifie que nous devons également définir une méthode `similar` correspondante :

```jldoctest ArrayAndChar; output = false
function Base.similar(bc::Broadcast.Broadcasted{Broadcast.ArrayStyle{ArrayAndChar}}, ::Type{ElType}) where ElType
    # Scan the inputs for the ArrayAndChar:
    A = find_aac(bc)
    # Use the char field of A to create the output
    ArrayAndChar(similar(Array{ElType}, axes(bc)), A.char)
end

"`A = find_aac(As)` returns the first ArrayAndChar among the arguments."
find_aac(bc::Base.Broadcast.Broadcasted) = find_aac(bc.args)
find_aac(args::Tuple) = find_aac(find_aac(args[1]), Base.tail(args))
find_aac(x) = x
find_aac(::Tuple{}) = nothing
find_aac(a::ArrayAndChar, rest) = a
find_aac(::Any, rest) = find_aac(rest)
# output
find_aac (generic function with 6 methods)
```

À partir de ces définitions, on obtient le comportement suivant :

```jldoctest ArrayAndChar
julia> a = ArrayAndChar([1 2; 3 4], 'x')
2×2 ArrayAndChar{Int64, 2} with char 'x':
 1  2
 3  4

julia> a .+ 1
2×2 ArrayAndChar{Int64, 2} with char 'x':
 2  3
 4  5

julia> a .+ [5,10]
2×2 ArrayAndChar{Int64, 2} with char 'x':
  6   7
 13  14
```

### [Extending broadcast with custom implementations](@id extending-in-place-broadcast)

En général, une opération de diffusion est représentée par un conteneur `Broadcasted` paresseux qui conserve la fonction à appliquer ainsi que ses arguments. Ces arguments peuvent eux-mêmes être des conteneurs `Broadcasted` plus imbriqués, formant un grand arbre d'expressions à évaluer. Un arbre imbriqué de conteneurs `Broadcasted` est directement construit par la syntaxe implicite des points ; `5 .+ 2.*x` est temporairement représenté par `Broadcasted(+, 5, Broadcasted(*, 2, x))`, par exemple. Cela est invisible pour les utilisateurs car il est immédiatement réalisé par un appel à `copy`, mais c'est ce conteneur qui fournit la base pour l'extensibilité de la diffusion pour les auteurs de types personnalisés. La machinerie de diffusion intégrée déterminera ensuite le type et la taille du résultat en fonction des arguments, l'allouera, puis copiera enfin la réalisation de l'objet `Broadcasted` à l'intérieur avec une méthode par défaut `copyto!(::AbstractArray, ::Broadcasted)`. Les méthodes de secours intégrées `broadcast` et `broadcast!` construisent également une représentation `Broadcasted` temporaire de l'opération afin qu'elles puissent suivre le même chemin de code. Cela permet aux implémentations de tableaux personnalisés de fournir leur propre spécialisation `copyto!` pour personnaliser et optimiser la diffusion. Cela est encore déterminé par le style de diffusion calculé. C'est une partie si importante de l'opération qu'elle est stockée comme le premier paramètre de type du type `Broadcasted`, permettant ainsi le dispatch et la spécialisation.

Pour certains types, la machinerie pour "fusionner" les opérations à travers des niveaux imbriqués de diffusion n'est pas disponible ou pourrait être effectuée plus efficacement de manière incrémentale. Dans de tels cas, vous pourriez avoir besoin ou vouloir évaluer `x .* (x .+ 1)` comme s'il avait été écrit `broadcast(*, x, broadcast(+, x, 1))`, où l'opération intérieure est évaluée avant de s'attaquer à l'opération extérieure. Ce type d'opération avide est directement pris en charge par un peu d'indirection ; au lieu de construire directement des objets `Broadcasted`, Julia abaisse l'expression fusionnée `x .* (x .+ 1)` à `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))`. Maintenant, par défaut, `broadcasted` appelle simplement le constructeur `Broadcasted` pour créer la représentation paresseuse de l'arbre d'expression fusionnée, mais vous pouvez choisir de le remplacer pour une combinaison particulière de fonction et d'arguments.

En tant qu'exemple, les objets `AbstractRange` intégrés utilisent cette mécanique pour optimiser des morceaux d'expressions diffusées qui peuvent être évaluées de manière anticipée uniquement en termes de début, d'étape et de longueur (ou d'arrêt) au lieu de calculer chaque élément. Tout comme toute la autre mécanique, `broadcasted` calcule et expose également le style de diffusion combiné de ses arguments, donc au lieu de se spécialiser sur `broadcasted(f, args...)`, vous pouvez vous spécialiser sur `broadcasted(::DestStyle, f, args...)` pour toute combinaison de style, de fonction et d'arguments.

Par exemple, la définition suivante prend en charge la négation des plages :

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

Le broadcasting en place peut être pris en charge en définissant la méthode appropriée `copyto!(dest, bc::Broadcasted)`. Comme vous pourriez vouloir vous spécialiser soit sur `dest`, soit sur le sous-type spécifique de `bc`, pour éviter les ambiguïtés entre les packages, nous recommandons la convention suivante.

Si vous souhaitez vous spécialiser dans un style particulier `DestStyle`, définissez une méthode pour

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

Optionnellement, avec ce formulaire, vous pouvez également vous spécialiser sur le type de `dest`.

Si vous souhaitez plutôt vous spécialiser sur le type de destination `DestType` sans vous spécialiser sur `DestStyle`, vous devez définir une méthode avec la signature suivante :

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

Cela tire parti d'une implémentation de secours de `copyto!` qui convertit le wrapper en un `Broadcasted{Nothing}`. Par conséquent, la spécialisation sur `DestType` a une priorité inférieure à celle des méthodes qui se spécialisent sur `DestStyle`.

De la même manière, vous pouvez complètement remplacer le broadcasting hors de propos avec une méthode `copy(::Broadcasted)`.

#### Working with `Broadcasted` objects

Pour implémenter une méthode `copy` ou `copyto!`, bien sûr, vous devez travailler avec l'enveloppe `Broadcasted` pour calculer chaque élément. Il existe deux principales façons de le faire :

  * `Broadcast.flatten` recompute les opérations potentiellement imbriquées en une seule fonction et une liste d'arguments à plat. Vous êtes responsable de la mise en œuvre des règles de forme de diffusion vous-même, mais cela peut être utile dans des situations limitées.
  * Itérer sur les `CartesianIndices` des `axes(::Broadcasted)` et utiliser l'indexation avec l'objet `CartesianIndex` résultant pour calculer le résultat.

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

Les règles de priorité sont définies par des appels `BroadcastStyle` binaires :

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

où `Style12` est le `BroadcastStyle` que vous souhaitez choisir pour les sorties impliquant des arguments de `Style1` et `Style2`. Par exemple,

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

indique que `Tuple` "gagne" sur les tableaux à zéro dimension (le conteneur de sortie sera un tuple). Il convient de noter que vous n'avez pas besoin de (et ne devez pas) définir les deux ordres d'arguments de cet appel ; en définir un est suffisant peu importe l'ordre dans lequel l'utilisateur fournit les arguments.

Pour les types `AbstractArray`, définir un `BroadcastStyle` remplace le choix par défaut, [`Broadcast.DefaultArrayStyle`](@ref). `DefaultArrayStyle` et le supertype abstrait, `AbstractArrayStyle`, stockent la dimensionnalité en tant que paramètre de type pour prendre en charge les types de tableaux spécialisés qui ont des exigences de dimensionnalité fixes.

`DefaultArrayStyle` "perd" face à tout autre `AbstractArrayStyle` qui a été défini en raison des méthodes suivantes :

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

Vous n'avez pas besoin d'écrire des règles `BroadcastStyle` binaires à moins que vous ne souhaitiez établir une priorité pour deux ou plusieurs types non `DefaultArrayStyle`.

Si votre type de tableau a des exigences de dimensionnalité fixe, vous devez sous-classer `AbstractArrayStyle`. Par exemple, le code du tableau creux a les définitions suivantes :

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

Chaque fois que vous sous-classez `AbstractArrayStyle`, vous devez également définir des règles pour combiner les dimensions, en créant un constructeur pour votre style qui prend un argument `Val(N)`. Par exemple :

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

Ces règles indiquent que la combinaison d'un `SparseVecStyle` avec des tableaux de 0 ou 1 dimension produit un autre `SparseVecStyle`, que sa combinaison avec un tableau de 2 dimensions produit un `SparseMatStyle`, et que toute autre dimension supérieure revient au cadre dense à dimensions arbitraires. Ces règles permettent à la diffusion de conserver la représentation sparse pour les opérations qui résultent en sorties d'une ou deux dimensions, mais produisent un `Array` pour toute autre dimensionnalité.

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

Parfois, il est souhaitable de modifier la façon dont l'utilisateur final interagit avec les champs d'un objet. Au lieu d'accorder un accès direct aux champs de type, une couche supplémentaire d'abstraction entre l'utilisateur et le code peut être fournie en surchargeant `object.field`. Les propriétés sont ce que l'utilisateur *voit de* l'objet, les champs ce que l'objet *est réellement*.

Par défaut, les propriétés et les champs sont les mêmes. Cependant, ce comportement peut être modifié. Par exemple, prenons cette représentation d'un point dans un plan en [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system) :

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

Comme décrit dans le tableau ci-dessus, l'accès par point `p.r` est le même que `getproperty(p, :r)` qui est par défaut le même que `getfield(p, :r)` :

```jldoctest polartype
julia> propertynames(p)
(:r, :ϕ)

julia> getproperty(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)

julia> p.r, p.ϕ
(7.0, 0.7853981633974483)

julia> getfield(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)
```

Cependant, nous pouvons vouloir que les utilisateurs ne soient pas au courant que `Point` stocke les coordonnées sous forme de `r` et `ϕ` (champs), et interagissent plutôt avec `x` et `y` (propriétés). Les méthodes dans la première colonne peuvent être définies pour ajouter de nouvelles fonctionnalités :

```jldoctest polartype
julia> Base.propertynames(::Point, private::Bool=false) = private ? (:x, :y, :r, :ϕ) : (:x, :y)

julia> function Base.getproperty(p::Point, s::Symbol)
           if s === :x
               return getfield(p, :r) * cos(getfield(p, :ϕ))
           elseif s === :y
               return getfield(p, :r) * sin(getfield(p, :ϕ))
           else
               # This allows accessing fields with p.r and p.ϕ
               return getfield(p, s)
           end
       end

julia> function Base.setproperty!(p::Point, s::Symbol, f)
           if s === :x
               y = p.y
               setfield!(p, :r, sqrt(f^2 + y^2))
               setfield!(p, :ϕ, atan(y, f))
               return f
           elseif s === :y
               x = p.x
               setfield!(p, :r, sqrt(x^2 + f^2))
               setfield!(p, :ϕ, atan(f, x))
               return f
           else
               # This allow modifying fields with p.r and p.ϕ
               return setfield!(p, s, f)
           end
       end
```

Il est important que `getfield` et `setfield` soient utilisés à l'intérieur de `getproperty` et `setproperty!` au lieu de la syntaxe par point, car la syntaxe par point rendrait les fonctions récursives, ce qui peut entraîner des problèmes d'inférence de type. Nous pouvons maintenant essayer la nouvelle fonctionnalité :

```jldoctest polartype
julia> propertynames(p)
(:x, :y)

julia> p.x
4.949747468305833

julia> p.y = 4.0
4.0

julia> p.r
6.363961030678928
```

Enfin, il convient de noter que l'ajout de propriétés d'instance de cette manière est assez rarement fait en Julia et ne devrait en général être effectué que s'il y a une bonne raison de le faire.

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

Pour prendre en charge l'arrondi sur un nouveau type, il suffit généralement de définir la méthode unique `round(x::ObjType, r::RoundingMode)`. Le mode d'arrondi passé détermine dans quelle direction la valeur doit être arrondie. Les modes d'arrondi les plus couramment utilisés sont `RoundNearest`, `RoundToZero`, `RoundDown` et `RoundUp`, car ces modes d'arrondi sont utilisés dans les définitions de la méthode `round` à un argument, ainsi que `trunc`, `floor` et `ceil`, respectivement.

Dans certains cas, il est possible de définir une méthode `round` à trois arguments qui est plus précise ou performante que la méthode à deux arguments suivie d'une conversion. Dans ce cas, il est acceptable de définir la méthode à trois arguments en plus de la méthode à deux arguments. S'il est impossible de représenter le résultat arrondi comme un objet du type `T`, alors la méthode à trois arguments doit lancer une `InexactError`.

Par exemple, si nous avons un type `Interval` qui représente une plage de valeurs possibles similaire à https://github.com/JuliaPhysics/Measurements.jl, nous pouvons définir l'arrondi sur ce type avec ce qui suit

```jldoctest
julia> struct Interval{T}
           min::T
           max::T
       end

julia> Base.round(x::Interval, r::RoundingMode) = Interval(round(x.min, r), round(x.max, r))

julia> x = Interval(1.7, 2.2)
Interval{Float64}(1.7, 2.2)

julia> round(x)
Interval{Float64}(2.0, 2.0)

julia> floor(x)
Interval{Float64}(1.0, 2.0)

julia> ceil(x)
Interval{Float64}(2.0, 3.0)

julia> trunc(x)
Interval{Float64}(1.0, 2.0)
```

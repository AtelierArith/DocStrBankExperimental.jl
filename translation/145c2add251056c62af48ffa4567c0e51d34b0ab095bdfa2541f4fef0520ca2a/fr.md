# [Arrays with custom indices](@id man-custom-indices)

Conventionnellement, les tableaux de Julia sont indexés à partir de 1, tandis que certains autres langages commencent la numérotation à 0, et d'autres encore (par exemple, Fortran) vous permettent de spécifier des indices de départ arbitraires. Bien qu'il y ait beaucoup de mérite à choisir une norme (c'est-à-dire 1 pour Julia), il existe certains algorithmes qui se simplifient considérablement si vous pouvez indexer en dehors de la plage `1:size(A,d)` (et pas seulement `0:size(A,d)-1`, non plus). Pour faciliter de tels calculs, Julia prend en charge des tableaux avec des indices arbitraires.

L'objectif de cette page est de répondre à la question : "que dois-je faire pour prendre en charge de tels tableaux dans mon propre code ?" Tout d'abord, abordons le cas le plus simple : si vous savez que votre code n'aura jamais besoin de gérer des tableaux avec un indexage non conventionnel, espérons que la réponse est "rien." L'ancien code, sur des tableaux conventionnels, devrait fonctionner essentiellement sans modification tant qu'il utilisait les interfaces exportées de Julia. Si vous trouvez plus pratique de forcer vos utilisateurs à fournir des tableaux traditionnels où l'indexation commence à un, vous pouvez ajouter

```julia
Base.require_one_based_indexing(arrays...)
```

où `arrays...` est une liste des objets de tableau que vous souhaitez vérifier pour tout ce qui viole l'indexation à base 1.

## Generalizing existing code

En résumé, les étapes sont :

  * Sure! Please provide the Markdown content or text you'd like me to translate.
  * remplacer `1:length(A)` par `eachindex(A)`, ou dans certains cas `LinearIndices(A)`
  * remplacer les allocations explicites comme `Array{Int}(undef, size(B))` par `similar(Array{Int}, axes(B))`

Ceci est décrit plus en détail ci-dessous.

### Things to watch out for

Parce que l'indexation non conventionnelle brise les hypothèses de nombreuses personnes selon lesquelles tous les tableaux commencent l'indexation à 1, il y a toujours un risque que l'utilisation de tels tableaux déclenche des erreurs. Les bogues les plus frustrants seraient des résultats incorrects ou des segfaults (crashes totaux de Julia). Par exemple, considérons la fonction suivante :

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

Ce code suppose implicitement que les vecteurs sont indexés à partir de 1 ; si `dest` commence à un index différent de `src`, il y a une chance que ce code déclenche une erreur de segmentation. (Si vous obtenez des erreurs de segmentation, pour aider à localiser la cause, essayez d'exécuter julia avec l'option `--check-bounds=yes`.)

### Using `axes` for bounds checks and loop iteration

`axes(A)` (évoquant `size(A)`) renvoie un tuple d'objets `AbstractUnitRange{<:Integer}`, spécifiant la plage des indices valides le long de chaque dimension de `A`. Lorsque `A` a un indexage non conventionnel, les plages peuvent ne pas commencer à 1. Si vous souhaitez simplement la plage pour une dimension particulière `d`, il existe `axes(A, d)`.

Base implémente un type de plage personnalisé, `OneTo`, où `OneTo(n)` signifie la même chose que `1:n` mais dans une forme qui garantit (via le système de types) que l'index inférieur est 1. Pour tout nouveau type [`AbstractArray`](@ref), c'est celui qui est retourné par défaut par `axes`, et cela indique que ce type de tableau utilise un indexage "conventionnel" basé sur 1.

Pour la vérification des limites, notez qu'il existe des fonctions dédiées `checkbounds` et `checkindex` qui peuvent parfois simplifier de tels tests.

### Linear indexing (`LinearIndices`)

Certains algorithmes sont le plus souvent écrits de manière pratique (ou efficace) en termes d'un seul index linéaire, `A[i]`, même si `A` est multidimensionnel. Quelle que soit l'origine des indices du tableau, les indices linéaires vont toujours de `1:length(A)`. Cependant, cela soulève une ambiguïté pour les tableaux unidimensionnels (a.k.a., [`AbstractVector`](@ref)) : est-ce que `v[i]` signifie un index linéaire, ou un index cartésien avec les indices natifs du tableau ?

Pour cette raison, votre meilleure option peut être de parcourir le tableau avec `eachindex(A)`, ou, si vous avez besoin que les indices soient des entiers séquentiels, d'obtenir la plage d'indices en appelant `LinearIndices(A)`. Cela renverra `axes(A, 1)` si A est un AbstractVector, et l'équivalent de `1:length(A)` sinon.

Par cette définition, les tableaux unidimensionnels utilisent toujours l'indexation cartésienne avec les indices natifs du tableau. Pour aider à faire respecter cela, il convient de noter que les fonctions de conversion d'index lanceront une erreur si la forme indique un tableau unidimensionnel avec une indexation non conventionnelle (c'est-à-dire, est un `Tuple{UnitRange}` plutôt qu'un tuple de `OneTo`). Pour les tableaux avec une indexation conventionnelle, ces fonctions continuent de fonctionner comme toujours.

En utilisant `axes` et `LinearIndices`, voici une façon de réécrire `mycopy!` :

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

Le stockage est souvent alloué avec `Array{Int}(undef, dims)` ou `similar(A, args...)`. Lorsque le résultat doit correspondre aux indices d'un autre tableau, cela peut ne pas toujours suffire. Le remplacement générique pour de tels motifs est d'utiliser `similar(storagetype, shape)`. `storagetype` indique le type de comportement "conventionnel" sous-jacent que vous souhaitez, par exemple, `Array{Int}` ou `BitArray` ou même `dims->zeros(Float32, dims)` (qui allouerait un tableau rempli de zéros). `shape` est un tuple de [`Integer`](@ref) ou de valeurs `AbstractUnitRange`, spécifiant les indices que vous souhaitez que le résultat utilise. Notez qu'un moyen pratique de produire un tableau rempli de zéros qui correspond aux indices de A est simplement `zeros(A)`.

Voyons quelques exemples explicites. Tout d'abord, si `A` a des indices conventionnels, alors `similar(Array{Int}, axes(A))` finirait par appeler `Array{Int}(undef, size(A))`, et retournerait donc un tableau. Si `A` est un type `AbstractArray` avec un indexage non conventionnel, alors `similar(Array{Int}, axes(A))` devrait retourner quelque chose qui "se comporte comme" un `Array{Int}` mais avec une forme (y compris les indices) qui correspond à `A`. (L'implémentation la plus évidente consiste à allouer un `Array{Int}(undef, size(A))` et ensuite à le "wrapper" dans un type qui déplace les indices.)

Notez également que `similar(Array{Int}, (axes(A, 2),))` allouerait un `AbstractVector{Int}` (c'est-à-dire, un tableau 1-dimensionnel) qui correspond aux indices des colonnes de `A`.

## Writing custom array types with non-1 indexing

La plupart des méthodes que vous devrez définir sont standard pour tout type `AbstractArray`, voir [Abstract Arrays](@ref man-interface-array). Cette page se concentre sur les étapes nécessaires pour définir un indexage non conventionnel.

### Custom `AbstractUnitRange` types

Si vous écrivez un type de tableau non indexé à partir de 1, vous voudrez spécialiser `axes` afin qu'il renvoie un `UnitRange`, ou (peut-être mieux) un `AbstractUnitRange` personnalisé. L'avantage d'un type personnalisé est qu'il "signale" le type d'allocation pour des fonctions comme `similar`. Si nous écrivons un type de tableau pour lequel l'indexation commencera à 0, nous voulons probablement commencer par créer un nouvel `AbstractUnitRange`, `ZeroRange`, où `ZeroRange(n)` est équivalent à `0:n-1`.

En général, vous ne devriez probablement *pas* exporter `ZeroRange` de votre package : il peut y avoir d'autres packages qui implémentent leur propre `ZeroRange`, et avoir plusieurs types distincts de `ZeroRange` est (peut-être contre-intuitivement) un avantage : `ModuleA.ZeroRange` indique que `similar` devrait créer un type `ModuleA.ZeroArray`, tandis que `ModuleB.ZeroRange` indique un type `ModuleB.ZeroArray`. Ce design permet une coexistence pacifique entre de nombreux types de tableaux personnalisés différents.

Notez que le paquet Julia [CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl) peut parfois être utilisé pour éviter d'avoir à écrire votre propre type `ZeroRange`.

### Specializing `axes`

Une fois que vous avez votre type `AbstractUnitRange`, spécialisez ensuite `axes` :

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

où ici nous imaginons que `ZeroArray` a un champ appelé `size` (il y aurait d'autres façons de l'implémenter).

Dans certains cas, la définition de secours pour `axes(A, d)` :

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

peut ne pas être ce que vous voulez : vous devrez peut-être le spécialiser pour renvoyer autre chose que `OneTo(1)` lorsque `d > ndims(A)`. De même, dans `Base`, il existe une fonction dédiée `axes1` qui est équivalente à `axes(A, 1)` mais qui évite de vérifier (au moment de l'exécution) si `ndims(A) > 0`. (C'est purement une optimisation de performance.) Elle est définie comme :

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

Si le premier de ces cas (le cas zéro-dimensionnel) pose problème pour votre type de tableau personnalisé, assurez-vous de le spécialiser de manière appropriée.

### Specializing `similar`

Étant donné votre type personnalisé `ZeroRange`, vous devez également ajouter les deux spécialisations suivantes pour `similar` :

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

Les deux devraient allouer votre type de tableau personnalisé.

### Specializing `reshape`

Optionnellement, définissez une méthode

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

et vous pouvez `reshape` un tableau de sorte que le résultat ait des indices personnalisés.

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes` dépend de la définition de `axes` pour les objets sur lesquels vous l'appelez. S'il y a une raison pour laquelle vous n'avez pas de méthode `axes` définie pour votre objet, envisagez de définir une méthode.

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

Cela permettra au code qui suppose un indexage basé sur 1 de détecter un problème et de lancer une erreur utile, plutôt que de renvoyer des résultats incorrects ou de provoquer un segfault en julia.

### Catching errors

Si votre nouveau type de tableau déclenche des erreurs dans d'autres codes, une étape de débogage utile peut consister à commenter `@boundscheck` dans votre implémentation de `getindex` et `setindex!`. Cela garantira que chaque accès aux éléments vérifie les limites. Ou, redémarrez julia avec `--check-bounds=yes`.

Dans certains cas, il peut également être utile de désactiver temporairement `size` et `length` pour votre nouveau type de tableau, car le code qui fait des hypothèses incorrectes utilise souvent ces fonctions.

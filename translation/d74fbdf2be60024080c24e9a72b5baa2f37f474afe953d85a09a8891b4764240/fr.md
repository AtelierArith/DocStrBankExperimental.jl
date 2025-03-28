# SubArrays

Le type `SubArray` de Julia est un conteneur encodant une "vue" d'un parent [`AbstractArray`](@ref). Cette page documente certains des principes de conception et de mise en œuvre des `SubArray`.

Un des principaux objectifs de conception est d'assurer une haute performance pour les vues des tableaux [`IndexLinear`](@ref) et [`IndexCartesian`](@ref). De plus, les vues des tableaux `IndexLinear` devraient elles-mêmes être `IndexLinear` dans la mesure du possible.

## Index replacement

Considérez la création de tranches 2D d'un tableau 3D :

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view` supprime les dimensions "singleton" (celles qui sont spécifiées par un `Int`), donc à la fois `S1` et `S2` sont des `SubArray`s à deux dimensions. Par conséquent, la manière naturelle de les indexer est avec `S1[i,j]`. Pour extraire la valeur du tableau parent `A`, l'approche naturelle consiste à remplacer `S1[i,j]` par `A[i,1,(2:3)[j]]` et `S2[i,j]` par `A[1,i,(2:3)[j]]`.

La caractéristique clé de la conception des Sous-Tableaux est que ce remplacement d'index peut être effectué sans aucun coût d'exécution.

## SubArray design

### Type parameters and fields

La stratégie adoptée s'exprime avant tout dans la définition du type :

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray` a 5 paramètres de type. Les deux premiers sont le type d'élément standard et la dimensionnalité. Le suivant est le type du parent `AbstractArray`. Le paramètre le plus utilisé est le quatrième, un `Tuple` des types des indices pour chaque dimension. Le dernier, `L`, est fourni uniquement par commodité pour le dispatch ; c'est un booléen qui représente si les types d'indices supportent un indexation linéaire rapide. Plus d'informations à ce sujet plus tard.

Si dans notre exemple ci-dessus `A` est un `Array{Float64, 3}`, notre cas `S1` ci-dessus serait un `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}`. Notez en particulier le paramètre tuple, qui stocke les types des indices utilisés pour créer `S1`. De même,

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

Stocker ces valeurs permet le remplacement d'index, et avoir les types encodés en tant que paramètres permet de dispatcher vers des algorithmes efficaces.

### Index translation

La traduction des indices nécessite de faire différentes choses pour différents types concrets de `SubArray`. Par exemple, pour `S1`, il faut appliquer les indices `i,j` aux première et troisième dimensions du tableau parent, tandis que pour `S2`, il faut les appliquer à la deuxième et à la troisième. L'approche la plus simple pour l'indexation consisterait à effectuer l'analyse de type à l'exécution :

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

Malheureusement, cela serait désastreux en termes de performance : chaque accès à un élément allouerait de la mémoire et impliquerait l'exécution d'un grand nombre de codes mal typés.

La meilleure approche consiste à dispatcher vers des méthodes spécifiques pour gérer chaque type d'index stocké. C'est ce que fait `reindex` : il dispatch sur le type du premier index stocké et consomme le nombre approprié d'indices d'entrée, puis il se récursive sur les indices restants. Dans le cas de `S1`, cela s'étend à

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

pour toute paire d'indices `(i,j)` (sauf [`CartesianIndex`](@ref) et les tableaux de ceux-ci, voir ci-dessous).

C'est le cœur d'un `SubArray` ; les méthodes d'indexation dépendent de `reindex` pour effectuer cette traduction d'index. Parfois, cependant, nous pouvons éviter l'indirection et rendre cela encore plus rapide.

### Linear indexing

L'indexation linéaire peut être mise en œuvre de manière efficace lorsque l'ensemble du tableau a un seul pas qui sépare les éléments successifs, à partir d'un certain décalage. Cela signifie que nous pouvons pré-calculer ces valeurs et représenter l'indexation linéaire simplement comme une addition et une multiplication, évitant ainsi l'indirection de `reindex` et (plus important encore) le calcul lent des coordonnées cartésiennes dans son ensemble.

Pour les types `SubArray`, la disponibilité d'un indexage linéaire efficace dépend uniquement des types des indices et ne dépend pas de valeurs comme la taille du tableau parent. Vous pouvez demander si un ensemble donné d'indices prend en charge un indexage linéaire rapide avec la fonction interne `Base.viewindexing` :

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

Cela est calculé lors de la construction du `SubArray` et stocké dans le paramètre de type `L` en tant que booléen qui encode le support d'indexation linéaire rapide. Bien que cela ne soit pas strictement nécessaire, cela signifie que nous pouvons définir le dispatch directement sur `SubArray{T,N,A,I,true}` sans intermédiaires.

Puisque ce calcul ne dépend pas des valeurs d'exécution, il peut manquer certains cas où le pas s'avère uniforme :

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

Une vue construite comme `view(A, 2:2:4, :)` a une démarche uniforme, et par conséquent, l'indexation linéaire pourrait effectivement être effectuée de manière efficace. Cependant, le succès dans ce cas dépend de la taille du tableau : si la première dimension était plutôt impair,

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

alors `A[2:2:4,:]` n'a pas de pas uniforme, donc nous ne pouvons pas garantir un indexage linéaire efficace. Puisque nous devons baser cette décision uniquement sur les types encodés dans les paramètres du `SubArray`, `S = view(A, 2:2:4, :)` ne peut pas mettre en œuvre un indexage linéaire efficace.

### A few details

  * Notez que la fonction `Base.reindex` est indifférente aux types des indices d'entrée ; elle détermine simplement comment et où les indices stockés doivent être réindexés. Elle prend non seulement en charge les indices entiers, mais elle prend également en charge l'indexation non scalaire. Cela signifie que les vues de vues n'ont pas besoin de deux niveaux d'indirection ; elles peuvent simplement recalculer les indices dans le tableau parent d'origine !
  * Espérons qu'à ce stade, il soit assez clair que le support des tranches signifie que la dimensionnalité, donnée par le paramètre `N`, n'est pas nécessairement égale à la dimensionnalité du tableau parent ou à la longueur du tuple `indices`. De même, les indices fournis par l'utilisateur ne s'alignent pas nécessairement avec les entrées du tuple `indices` (par exemple, le deuxième indice fourni par l'utilisateur pourrait correspondre à la troisième dimension du tableau parent, et le troisième élément du tuple `indices`).

    Ce qui peut être moins évident, c'est que la dimensionnalité du tableau parent stocké doit être égale au nombre d'indices effectifs dans le tuple `indices`. Voici quelques exemples :

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    Naïvement, on pourrait penser qu'il suffirait de définir `S.parent = A` et `S.indices = (:,:,1:1)`, mais soutenir cela complique considérablement le processus de réindexation, en particulier pour les vues de vues. Non seulement vous devez dispatcher sur les types des indices stockés, mais vous devez également examiner si un indice donné est le dernier et "fusionner" tous les indices stockés restants. Ce n'est pas une tâche facile, et encore pire : c'est lent car cela dépend implicitement de l'indexation linéaire.

    Heureusement, c'est précisément le calcul que `ReshapedArray` effectue, et il le fait de manière linéaire si possible. Par conséquent, `view` s'assure que le tableau parent a la dimension appropriée pour les indices donnés en le remodelant si nécessaire. Le constructeur interne `SubArray` garantit que cette invariant est respecté.
  * [`CartesianIndex`](@ref) et les tableaux de ce type jettent une clé dans le schéma `reindex`. Rappelons que `reindex` se base simplement sur le type des indices stockés pour déterminer combien d'indices passés doivent être utilisés et où ils doivent aller. Mais avec `CartesianIndex`, il n'y a plus de correspondance un à un entre le nombre d'arguments passés et le nombre de dimensions dans lesquelles ils indexent. Si nous revenons à l'exemple ci-dessus de `Base.reindex(S1, S1.indices, (i, j))`, vous pouvez voir que l'expansion est incorrecte pour `i, j = CartesianIndex(), CartesianIndex(2,1)`. Elle devrait *sauter* complètement le `CartesianIndex()` et retourner :

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    Au lieu de cela, nous obtenons :

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    Faire cela correctement nécessiterait un dispatch *combiné* sur les indices stockés et passés à travers toutes les combinaisons de dimensions de manière inextricable. En tant que tel, `reindex` ne doit jamais être appelé avec des indices `CartesianIndex`. Heureusement, le cas scalaire est facilement géré en aplatissant d'abord les arguments `CartesianIndex` en entiers simples. Les tableaux de `CartesianIndex`, cependant, ne peuvent pas être séparés en morceaux orthogonaux si facilement. Avant d'essayer d'utiliser `reindex`, `view` doit s'assurer qu'il n'y a pas de tableaux de `CartesianIndex` dans la liste des arguments. S'il y en a, il peut simplement "laisser tomber" en évitant complètement le calcul de `reindex`, en construisant un `SubArray` imbriqué avec deux niveaux d'indirection à la place.

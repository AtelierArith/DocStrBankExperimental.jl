# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

Julia, comme la plupart des langages de calcul technique, offre une implémentation de tableau de première classe. La plupart des langages de calcul technique accordent beaucoup d'attention à leur implémentation de tableau au détriment d'autres conteneurs. Julia ne traite pas les tableaux de manière spéciale. La bibliothèque de tableaux est presque entièrement implémentée en Julia elle-même et tire ses performances du compilateur, tout comme tout autre code écrit en Julia. En tant que tel, il est également possible de définir des types de tableaux personnalisés en héritant de [`AbstractArray`](@ref). Consultez le [manual section on the AbstractArray interface](@ref man-interface-array) pour plus de détails sur l'implémentation d'un type de tableau personnalisé.

Un tableau est une collection d'objets stockés dans une grille multidimensionnelle. Les tableaux à zéro dimension sont autorisés, voir [this FAQ entry](@ref faq-array-0dim). Dans le cas le plus général, un tableau peut contenir des objets de type [`Any`](@ref). Pour la plupart des besoins computationnels, les tableaux devraient contenir des objets d'un type plus spécifique, tel que [`Float64`](@ref) ou [`Int32`](@ref).

En général, contrairement à de nombreux autres langages de calcul technique, Julia ne s'attend pas à ce que les programmes soient écrits dans un style vectorisé pour des performances optimales. Le compilateur de Julia utilise l'inférence de type et génère du code optimisé pour l'indexation des tableaux scalaires, permettant d'écrire des programmes dans un style qui est pratique et lisible, sans sacrifier les performances, et en utilisant parfois moins de mémoire.

En Julia, tous les arguments des fonctions sont [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing) (c'est-à-dire par pointeurs). Certains langages de calcul technique passent les tableaux par valeur, et bien que cela empêche la modification accidentelle par les appelés d'une valeur dans l'appelant, cela rend difficile l'évitement de la copie indésirable des tableaux. Par convention, un nom de fonction se terminant par un `!` indique qu'il va muter ou détruire la valeur d'un ou plusieurs de ses arguments (comparez, par exemple, [`sort`](@ref) et [`sort!`](@ref)). Les appelés doivent faire des copies explicites pour s'assurer qu'ils ne modifient pas les entrées qu'ils n'ont pas l'intention de changer. De nombreuses fonctions non mutantes sont mises en œuvre en appelant une fonction du même nom avec un `!` ajouté à la fin sur une copie explicite de l'entrée, et en retournant cette copie.

## Basic Functions

| Function               | Description                                                                      |
|:---------------------- |:-------------------------------------------------------------------------------- |
| [`eltype(A)`](@ref)    | the type of the elements contained in `A`                                        |
| [`length(A)`](@ref)    | the number of elements in `A`                                                    |
| [`ndims(A)`](@ref)     | the number of dimensions of `A`                                                  |
| [`size(A)`](@ref)      | a tuple containing the dimensions of `A`                                         |
| [`size(A,n)`](@ref)    | the size of `A` along dimension `n`                                              |
| [`axes(A)`](@ref)      | a tuple containing the valid indices of `A`                                      |
| [`axes(A,n)`](@ref)    | a range expressing the valid indices along dimension `n`                         |
| [`eachindex(A)`](@ref) | an efficient iterator for visiting each position in `A`                          |
| [`stride(A,k)`](@ref)  | the stride (linear index distance between adjacent elements) along dimension `k` |
| [`strides(A)`](@ref)   | a tuple of the strides in each dimension                                         |

## Construction and Initialization

De nombreuses fonctions pour construire et initialiser des tableaux sont fournies. Dans la liste suivante de ces fonctions, les appels avec un argument `dims...` peuvent soit prendre un seul tuple de tailles de dimension, soit une série de tailles de dimension passées en tant qu'arguments de nombre variable. La plupart de ces fonctions acceptent également un premier input `T`, qui est le type d'élément du tableau. Si le type `T` est omis, il sera par défaut [`Float64`](@ref).

| Function                           | Description                                                                                                                                                                                                                                  |
|:---------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Array{T}(undef, dims...)`](@ref) | an uninitialized dense [`Array`](@ref)                                                                                                                                                                                                       |
| [`zeros(T, dims...)`](@ref)        | an `Array` of all zeros                                                                                                                                                                                                                      |
| [`ones(T, dims...)`](@ref)         | an `Array` of all ones                                                                                                                                                                                                                       |
| [`trues(dims...)`](@ref)           | a [`BitArray`](@ref) with all values `true`                                                                                                                                                                                                  |
| [`falses(dims...)`](@ref)          | a `BitArray` with all values `false`                                                                                                                                                                                                         |
| [`reshape(A, dims...)`](@ref)      | an array containing the same data as `A`, but with different dimensions                                                                                                                                                                      |
| [`copy(A)`](@ref)                  | copy `A`                                                                                                                                                                                                                                     |
| [`deepcopy(A)`](@ref)              | copy `A`, recursively copying its elements                                                                                                                                                                                                   |
| [`similar(A, T, dims...)`](@ref)   | an uninitialized array of the same type as `A` (dense, sparse, etc.), but with the specified element type and dimensions. The second and third arguments are both optional, defaulting to the element type and dimensions of `A` if omitted. |
| [`reinterpret(T, A)`](@ref)        | an array with the same binary data as `A`, but with element type `T`                                                                                                                                                                         |
| [`rand(T, dims...)`](@ref)         | an `Array` with random, iid [^1] and uniformly distributed values. For floating point types `T`, the values lie in the half-open interval $[0, 1)$.                                                                                          |
| [`randn(T, dims...)`](@ref)        | an `Array` with random, iid and standard normally distributed values                                                                                                                                                                         |
| [`Matrix{T}(I, m, n)`](@ref)       | `m`-by-`n` identity matrix. Requires `using LinearAlgebra` for [`I`](@ref).                                                                                                                                                                  |
| [`range(start, stop, n)`](@ref)    | a range of `n` linearly spaced elements from `start` to `stop`                                                                                                                                                                               |
| [`fill!(A, x)`](@ref)              | fill the array `A` with the value `x`                                                                                                                                                                                                        |
| [`fill(x, dims...)`](@ref)         | an `Array` filled with the value `x`. In particular, `fill(x)` constructs a zero-dimensional `Array` containing `x`.                                                                                                                         |

[^1]: *iid*, independently and identically distributed.

Pour voir les différentes manières de passer des dimensions à ces fonctions, considérez les exemples suivants :

```jldoctest
julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros(Int8, (2, 3))
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros((2, 3))
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
```

Ici, `(2, 3)` est un [`Tuple`](@ref) et le premier argument — le type d'élément — est optionnel, par défaut `Float64`.

## [Array literals](@id man-array-literals)

Les tableaux peuvent également être construits directement avec des crochets ; la syntaxe `[A, B, C, ...]` crée un tableau unidimensionnel (c'est-à-dire un vecteur) contenant les arguments séparés par des virgules comme ses éléments. Le type d'élément ([`eltype`](@ref)) du tableau résultant est automatiquement déterminé par les types des arguments à l'intérieur des crochets. Si tous les arguments sont du même type, alors c'est son `eltype`. S'ils ont tous un [promotion type](@ref conversion-and-promotion) commun, alors ils sont convertis en ce type en utilisant [`convert`](@ref) et ce type est l'`eltype` du tableau. Sinon, un tableau hétérogène qui peut contenir n'importe quoi — un `Vector{Any}` — est construit ; cela inclut le littéral `[]` où aucun argument n'est donné. [Array literal can be typed](@ref man-array-typed-literal) avec la syntaxe `T[A, B, C, ...]` où `T` est un type.

```jldoctest
julia> [1, 2, 3] # An array of `Int`s
3-element Vector{Int64}:
 1
 2
 3

julia> promote(1, 2.3, 4//5) # This combination of Int, Float64 and Rational promotes to Float64
(1.0, 2.3, 0.8)

julia> [1, 2.3, 4//5] # Thus that's the element type of this Array
3-element Vector{Float64}:
 1.0
 2.3
 0.8

julia> Float32[1, 2.3, 4//5] # Specify element type manually
3-element Vector{Float32}:
 1.0
 2.3
 0.8

julia> []
Any[]
```

### [Concatenation](@id man-array-concatenation)

Si les arguments à l'intérieur des crochets sont séparés par des points-virgules simples (`;`) ou des sauts de ligne au lieu de virgules, alors leur contenu est *concaténé verticalement* ensemble au lieu que les arguments soient utilisés comme des éléments eux-mêmes.

```jldoctest
julia> [1:2, 4:5] # Has a comma, so no concatenation occurs. The ranges are themselves the elements
2-element Vector{UnitRange{Int64}}:
 1:2
 4:5

julia> [1:2; 4:5]
4-element Vector{Int64}:
 1
 2
 4
 5

julia> [1:2
        4:5
        6]
5-element Vector{Int64}:
 1
 2
 4
 5
 6
```

De même, si les arguments sont séparés par des tabulations, des espaces ou des doubles points-virgules, alors leur contenu est *concaténé horizontalement* ensemble.

```jldoctest
julia> [1:2  4:5  7:8]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [[1,2]  [4,5]  [7,8]]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [1 2 3] # Numbers can also be horizontally concatenated
1×3 Matrix{Int64}:
 1  2  3

julia> [1;; 2;; 3;; 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Des points-virgules simples (ou des sauts de ligne) et des espaces (ou des tabulations) peuvent être combinés pour concaténer à la fois horizontalement et verticalement en même temps.

```jldoctest
julia> [1 2
        3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [zeros(Int, 2, 2) [1; 2]
        [3 4]            5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [[1 1]; 2 3; [4 4]]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Les espaces (et les tabulations) ont une priorité plus élevée que les points-virgules, effectuant d'abord toutes les concaténations horizontales puis concaténant le résultat. L'utilisation de doubles points-virgules pour la concaténation horizontale, en revanche, effectue toutes les concaténations verticales avant de concaténer horizontalement le résultat.

```jldoctest
julia> [zeros(Int, 2, 2) ; [3 4] ;; [1; 2] ; 5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [1:2; 4;; 1; 3:4]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Tout comme `;` et `;;` se concatènent dans la première et la deuxième dimension, l'utilisation de plus de points-virgules prolonge ce même schéma général. Le nombre de points-virgules dans le séparateur spécifie la dimension particulière, donc `;;;` se concatène dans la troisième dimension, `;;;;` dans la quatrième, et ainsi de suite. Moins de points-virgules ont la priorité, donc les dimensions inférieures sont généralement concaténées en premier.

```jldoctest
julia> [1; 2;; 3; 4;; 5; 6;;;
        7; 8;; 9; 10;; 11; 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

Comme auparavant, les espaces (et les tabulations) pour la concaténation horizontale ont une priorité plus élevée que n'importe quel nombre de points-virgules. Ainsi, les tableaux de dimensions supérieures peuvent également être écrits en spécifiant d'abord leurs lignes, avec leurs éléments disposés textuellement de manière similaire à leur agencement :

```jldoctest
julia> [1 3 5
        2 4 6;;;
        7 9 11
        8 10 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> [1 2;;; 3 4;;;; 5 6;;; 7 8]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8

julia> [[1 2;;; 3 4];;;; [5 6];;; [7 8]]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8
```

Bien qu'ils signifient tous deux la concaténation dans la deuxième dimension, les espaces (ou les tabulations) et `;;` ne peuvent pas apparaître dans la même expression de tableau, à moins que le double point-virgule ne serve simplement de caractère de "continuation de ligne". Cela permet à une seule concaténation horizontale de s'étendre sur plusieurs lignes (sans que le saut de ligne ne soit interprété comme une concaténation verticale).

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Les points-virgules de terminaison peuvent également être utilisés pour ajouter des dimensions de longueur 1 en suffixe.

```jldoctest
julia> [1;;]
1×1 Matrix{Int64}:
 1

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3
```

Plus généralement, la concaténation peut être réalisée à travers la fonction [`cat`](@ref). Ces syntaxes sont des abréviations pour des appels de fonction qui sont elles-mêmes des fonctions de commodité :

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

Un tableau avec un type d'élément spécifique peut être construit en utilisant la syntaxe `T[A, B, C, ...]`. Cela construira un tableau 1-d avec le type d'élément `T`, initialisé pour contenir les éléments `A`, `B`, `C`, etc. Par exemple, `Any[x, y, z]` construit un tableau hétérogène qui peut contenir n'importe quelles valeurs.

La syntaxe de concaténation peut également être préfixée par un type pour spécifier le type d'élément du résultat.

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

Les compréhensions offrent un moyen général et puissant de construire des tableaux. La syntaxe des compréhensions est similaire à la notation de construction d'ensembles en mathématiques :

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

La signification de cette forme est que `F(x,y,...)` est évalué avec les variables `x`, `y`, etc. prenant chacune les valeurs de leur liste de valeurs donnée. Les valeurs peuvent être spécifiées comme tout objet itérable, mais seront couramment des plages comme `1:n` ou `2:(n-1)`, ou des tableaux explicites de valeurs comme `[1.2, 3.4, 5.7]`. Le résultat est un tableau dense N-d avec des dimensions qui sont la concaténation des dimensions des plages de variables `rx`, `ry`, etc. et chaque évaluation de `F(x,y,...)` renvoie un scalaire.

L'exemple suivant calcule une moyenne pondérée de l'élément actuel et de ses voisins gauche et droit le long d'une grille 1-d. :

```julia-repl
julia> x = rand(8)
8-element Array{Float64,1}:
 0.843025
 0.869052
 0.365105
 0.699456
 0.977653
 0.994953
 0.41084
 0.809411

julia> [ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
6-element Array{Float64,1}:
 0.736559
 0.57468
 0.685417
 0.912429
 0.8446
 0.656511
```

Le type du tableau résultant dépend des types des éléments calculés tout comme [array literals](@ref man-array-literals) le fait. Afin de contrôler le type explicitement, un type peut être préfixé à la compréhension. Par exemple, nous aurions pu demander le résultat en précision simple en écrivant :

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

Les compréhensions peuvent également être écrites sans les crochets, produisant un objet connu sous le nom de générateur. Cet objet peut être itéré pour produire des valeurs à la demande, au lieu d'allouer un tableau et de les stocker à l'avance (voir [Iteration](@ref)). Par exemple, l'expression suivante somme une série sans allouer de mémoire :

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

Lors de l'écriture d'une expression génératrice avec plusieurs dimensions à l'intérieur d'une liste d'arguments, des parenthèses sont nécessaires pour séparer le générateur des arguments suivants :

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

Toutes les expressions séparées par des virgules après `for` sont interprétées comme des plages. Ajouter des parenthèses nous permet d'ajouter un troisième argument à [`map`](@ref) :

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

Les générateurs sont implémentés via des fonctions internes. Tout comme les fonctions internes utilisées ailleurs dans le langage, les variables de la portée englobante peuvent être "capturées" dans la fonction interne. Par exemple, `sum(p[i] - q[i] for i=1:n)` capture les trois variables `p`, `q` et `n` de la portée englobante. Les variables capturées peuvent poser des défis de performance ; voir [performance tips](@ref man-performance-captured).

Les plages dans les générateurs et les compréhensions peuvent dépendre de plages précédentes en écrivant plusieurs mots-clés `for` :

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i]
6-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)
 (3, 1)
 (3, 2)
 (3, 3)
```

Dans de tels cas, le résultat est toujours 1-d.

Les valeurs générées peuvent être filtrées en utilisant le mot-clé `if` :

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

La syntaxe générale pour indexer un tableau n-dimensionnel `A` est :

```
X = A[I_1, I_2, ..., I_n]
```

où chaque `I_k` peut être un entier scalaire, un tableau d'entiers, ou tout autre [supported index](@ref man-supported-index-types). Cela inclut [`Colon`](@ref) (`:`) pour sélectionner tous les indices dans l'ensemble de la dimension, des plages de la forme `a:c` ou `a:b:c` pour sélectionner des sous-sections contiguës ou espacées, et des tableaux de booléens pour sélectionner des éléments à leurs indices `true`.

Si tous les indices sont des scalaires, alors le résultat `X` est un seul élément du tableau `A`. Sinon, `X` est un tableau ayant le même nombre de dimensions que la somme des dimensions de tous les indices.

Si tous les indices `I_k` sont des vecteurs, par exemple, alors la forme de `X` serait `(length(I_1), length(I_2), ..., length(I_n))`, avec la position `i_1, i_2, ..., i_n` de `X` contenant la valeur `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]`.

Exemple :

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[1, 2, 1, 1] # all scalar indices
3

julia> A[[1, 2], [1], [1, 2], [1]] # all vector indices
2×1×2×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1
 2

[:, :, 2, 1] =
 5
 6

julia> A[[1, 2], [1], [1, 2], 1] # a mix of index types
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 5
 6
```

Notez comment la taille du tableau résultant est différente dans les deux derniers cas.

Si `I_1` est changé en une matrice à deux dimensions, alors `X` devient un tableau de `n+1` dimensions de forme `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))`. La matrice ajoute une dimension.

Exemple :

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2));

julia> A[[1 2; 1 2]]
2×2 Matrix{Int64}:
 1  2
 1  2

julia> A[[1 2; 1 2], 1, 2, 1]
2×2 Matrix{Int64}:
 5  6
 5  6
```

L'emplacement `i_1, i_2, i_3, ..., i_{n+1}` contient la valeur à `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]`. Toutes les dimensions indexées par des scalaires sont supprimées. Par exemple, si `J` est un tableau d'indices, alors le résultat de `A[2, J, 3]` est un tableau de taille `size(J)`. Son élément `j` est peuplé par `A[2, J[j], 3]`.

En tant que partie spéciale de cette syntaxe, le mot-clé `end` peut être utilisé pour représenter le dernier index de chaque dimension dans les crochets d'indexation, tel que déterminé par la taille du tableau le plus interne étant indexé. La syntaxe d'indexation sans le mot-clé `end` est équivalente à un appel à [`getindex`](@ref) :

```
X = getindex(A, I_1, I_2, ..., I_n)
```

Exemple :

```jldoctest
julia> x = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> x[2:3, 2:end-1]
2×2 Matrix{Int64}:
 6  10
 7  11

julia> x[1, [2 3; 4 1]]
2×2 Matrix{Int64}:
  5  9
 13  1
```

## [Indexed Assignment](@id man-indexed-assignment)

La syntaxe générale pour assigner des valeurs dans un tableau n-dimensionnel `A` est :

```
A[I_1, I_2, ..., I_n] = X
```

où chaque `I_k` peut être un entier scalaire, un tableau d'entiers, ou tout autre [supported index](@ref man-supported-index-types). Cela inclut [`Colon`](@ref) (`:`) pour sélectionner tous les indices dans l'ensemble de la dimension, des plages de la forme `a:c` ou `a:b:c` pour sélectionner des sous-sections contiguës ou espacées, et des tableaux de booléens pour sélectionner des éléments à leurs indices `true`.

Si tous les indices `I_k` sont des entiers, alors la valeur à l'emplacement `I_1, I_2, ..., I_n` de `A` est écrasée par la valeur de `X`, [`convert`](@ref) en fonction du [`eltype`](@ref) de `A` si nécessaire.

Si un index `I_k` est lui-même un tableau, alors le côté droit `X` doit également être un tableau ayant la même forme que le résultat de l'indexation `A[I_1, I_2, ..., I_n]` ou un vecteur avec le même nombre d'éléments. La valeur à l'emplacement `I_1[i_1], I_2[i_2], ..., I_n[i_n]` de `A` est écrasée par la valeur `X[i_1, i_2, ..., i_n]`, en convertissant si nécessaire. L'opérateur d'assignation élément par élément `.=` peut être utilisé pour [broadcast](@ref Broadcasting) `X` à travers les emplacements sélectionnés :

```
A[I_1, I_2, ..., I_n] .= X
```

Tout comme dans [Indexing](@ref man-array-indexing), le mot-clé `end` peut être utilisé pour représenter le dernier index de chaque dimension dans les crochets d'indexation, tel que déterminé par la taille du tableau dans lequel on assigne. La syntaxe d'assignation indexée sans le mot-clé `end` est équivalente à un appel à [`setindex!`](@ref) :

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

Exemple :

```jldoctest
julia> x = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> x[3, 3] = -9;

julia> x[1:2, 1:2] = [-1 -4; -2 -5];

julia> x
3×3 Matrix{Int64}:
 -1  -4   7
 -2  -5   8
  3   6  -9
```

## [Supported index types](@id man-supported-index-types)

Dans l'expression `A[I_1, I_2, ..., I_n]`, chaque `I_k` peut être un indice scalaire, un tableau d'indices scalaires, ou un objet qui représente un tableau d'indices scalaires et peut être converti en tel par [`to_indices`](@ref) :

1. Un index scalaire. Par défaut, cela inclut :

      * Entiers non booléens
      * [`CartesianIndex{N}`](@ref)s, qui se comportent comme un `N`-tuple d'entiers s'étendant sur plusieurs dimensions (voir ci-dessous pour plus de détails)
2. Un tableau d'indices scalaires. Cela inclut :

      * Vecteurs et tableaux multidimensionnels d'entiers
      * Des tableaux vides comme `[]`, qui ne sélectionnent aucun élément par exemple `A[[]]` (à ne pas confondre avec `A[]`)
      * Des plages comme `a:c` ou `a:b:c`, qui sélectionnent des sous-sections contiguës ou espacées de `a` à `c` (inclus)
      * Tout tableau personnalisé d'indices scalaires qui est un sous-type de `AbstractArray`
      * Tableaux de `CartesianIndex{N}` (voir ci-dessous pour plus de détails)
3. Un objet qui représente un tableau d'indices scalaires et peut être converti en tel par [`to_indices`](@ref). Par défaut, cela inclut :

      * [`Colon()`](@ref) (`:`), qui représente tous les indices dans une dimension entière ou à travers l'ensemble du tableau
      * Tableaux de booléens, qui sélectionnent des éléments à leurs indices `true` (voir ci-dessous pour plus de détails)

Quelques exemples :

```jldoctest
julia> A = reshape(collect(1:2:18), (3, 3))
3×3 Matrix{Int64}:
 1   7  13
 3   9  15
 5  11  17

julia> A[4]
7

julia> A[[2, 5, 8]]
3-element Vector{Int64}:
  3
  9
 15

julia> A[[1 4; 3 8]]
2×2 Matrix{Int64}:
 1   7
 5  15

julia> A[[]]
Int64[]

julia> A[1:2:5]
3-element Vector{Int64}:
 1
 5
 9

julia> A[2, :]
3-element Vector{Int64}:
  3
  9
 15

julia> A[:, 3]
3-element Vector{Int64}:
 13
 15
 17

julia> A[:, 3:3]
3×1 Matrix{Int64}:
 13
 15
 17
```

### Cartesian indices

L'objet spécial `CartesianIndex{N}` représente un index scalaire qui se comporte comme un `N`-uplet d'entiers s'étendant sur plusieurs dimensions. Par exemple :

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

Considéré seul, cela peut sembler relativement trivial ; `CartesianIndex` rassemble simplement plusieurs entiers en un seul objet qui représente un index multidimensionnel. Cependant, lorsqu'il est combiné avec d'autres formes d'indexation et des itérateurs qui produisent des `CartesianIndex`, cela peut produire un code très élégant et efficace. Voir [Iteration](@ref) ci-dessous, et pour quelques exemples plus avancés, voir [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration).

Les tableaux de `CartesianIndex{N}` sont également pris en charge. Ils représentent une collection d'indices scalaires qui s'étendent chacun sur `N` dimensions, permettant une forme d'indexation parfois appelée indexation par points. Par exemple, cela permet d'accéder aux éléments diagonaux de la première "page" de `A` ci-dessus :

```jldoctest cartesianindex
julia> page = A[:, :, 1]
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> page[[CartesianIndex(1, 1),
             CartesianIndex(2, 2),
             CartesianIndex(3, 3),
             CartesianIndex(4, 4)]]
4-element Vector{Int64}:
  1
  6
 11
 16
```

Cela peut être exprimé de manière beaucoup plus simple avec [dot broadcasting](@ref man-vectorized) et en le combinant avec un index entier normal (au lieu d'extraire la première `page` de `A` comme une étape séparée). Il peut même être combiné avec un `:` pour extraire les deux diagonales des deux pages en même temps :

```jldoctest cartesianindex
julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), 1]
4-element Vector{Int64}:
  1
  6
 11
 16

julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), :]
4×2 Matrix{Int64}:
  1  17
  6  22
 11  27
 16  32
```

!!! warning
    `CartesianIndex` et les tableaux de `CartesianIndex` ne sont pas compatibles avec le mot-clé `end` pour représenter le dernier index d'une dimension. Ne pas utiliser `end` dans les expressions d'indexation qui peuvent contenir soit `CartesianIndex`, soit des tableaux de celui-ci.


### Logical indexing

Souvent appelé indexation logique ou indexation avec un masque logique, l'indexation par un tableau booléen sélectionne les éléments aux indices où ses valeurs sont `true`. L'indexation par un vecteur booléen `B` est effectivement la même que l'indexation par le vecteur d'entiers qui est renvoyé par [`findall(B)`](@ref). De même, l'indexation par un tableau booléen de dimension `N` est effectivement la même que l'indexation par le vecteur de `CartesianIndex{N}` où ses valeurs sont `true`. Un index logique doit être un tableau de la même forme que la ou les dimensions dans lesquelles il s'indexe, ou il doit être le seul index fourni et correspondre à la forme de la vue remodelée unidimensionnelle du tableau dans lequel il s'indexe. Il est généralement plus efficace d'utiliser des tableaux booléens comme indices directement au lieu d'appeler d'abord [`findall`](@ref).

```jldoctest
julia> x = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> x[:, [true false; false true; true false]]
2×3 Matrix{Int64}:
 1  5   9
 2  6  10

julia> mask = map(ispow2, x)
2×3×2 Array{Bool, 3}:
[:, :, 1] =
 1  0  0
 1  1  0

[:, :, 2] =
 0  0  0
 1  0  0

julia> x[mask]
4-element Vector{Int64}:
 1
 2
 4
 8

julia> x[vec(mask)] == x[mask] # we can also index with a single Boolean vector
true
```

### Number of indices

#### Cartesian indexing

La manière ordinaire d'indexer un tableau `N`-dimensionnel est d'utiliser exactement `N` indices ; chaque indice sélectionne la ou les positions dans sa dimension particulière. Par exemple, dans le tableau tridimensionnel `A = rand(4, 3, 2)`, `A[2, 3, 1]` sélectionnera le nombre dans la deuxième ligne de la troisième colonne dans la première "page" du tableau. Cela est souvent appelé *indexation cartésienne*.

#### Linear indexing

Lorsque exactement un index `i` est fourni, cet index ne représente plus un emplacement dans une dimension particulière du tableau. Au lieu de cela, il sélectionne le `i`ème élément en utilisant l'ordre d'itération en colonne qui couvre linéairement l'ensemble du tableau. Cela est connu sous le nom de *indexation linéaire*. Cela traite essentiellement le tableau comme s'il avait été remodelé en un vecteur unidimensionnel avec [`vec`](@ref).

```jldoctest linindexing
julia> A = [2 6; 4 7; 3 1]
3×2 Matrix{Int64}:
 2  6
 4  7
 3  1

julia> A[5]
7

julia> vec(A)[5]
7
```

Un index linéaire dans le tableau `A` peut être converti en un `CartesianIndex` pour l'indexation cartésienne avec `CartesianIndices(A)[i]` (voir [`CartesianIndices`](@ref)), et un ensemble de `N` indices cartésiens peut être converti en un index linéaire avec `LinearIndices(A)[i_1, i_2, ..., i_N]` (voir [`LinearIndices`](@ref)).

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

Il est important de noter qu'il existe une très grande asymétrie dans la performance de ces conversions. La conversion d'un index linéaire en un ensemble d'indices cartésiens nécessite de diviser et de prendre le reste, tandis que l'inverse se fait simplement par multiplication et addition. Dans les processeurs modernes, la division entière peut être de 10 à 50 fois plus lente que la multiplication. Bien que certains tableaux — comme [`Array`](@ref) lui-même — soient implémentés en utilisant un morceau de mémoire linéaire et utilisent directement un index linéaire dans leurs implémentations, d'autres tableaux — comme [`Diagonal`](@ref) — ont besoin de l'ensemble complet des indices cartésiens pour effectuer leur recherche (voir [`IndexStyle`](@ref) pour introspecter lequel est lequel).

!!! warning
    Lors de l'itération sur tous les indices d'un tableau, il est préférable d'itérer sur [`eachindex(A)`](@ref) au lieu de `1:length(A)`. Non seulement cela sera plus rapide dans les cas où `A` est `IndexCartesian`, mais cela prendra également en charge les tableaux avec un index personnalisé, comme [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl). Si seules les valeurs sont nécessaires, il est alors préférable d'itérer directement sur le tableau, c'est-à-dire `for a in A`.


#### Omitted and extra indices

En plus de l'indexation linéaire, un tableau à `N` dimensions peut être indexé avec moins ou plus de `N` indices dans certaines situations.

Les indices peuvent être omis si les dimensions finales qui ne sont pas indexées ont toutes une longueur de un. En d'autres termes, les indices finaux ne peuvent être omis que s'il n'y a qu'une seule valeur possible que ces indices omis pourraient avoir pour une expression d'indexation dans les limites. Par exemple, un tableau à quatre dimensions de taille `(3, 4, 2, 1)` peut être indexé avec seulement trois indices, car la dimension qui est sautée (la quatrième dimension) a une longueur de un. Notez que l'indexation linéaire a la priorité sur cette règle.

```jldoctest
julia> A = reshape(1:24, 3, 4, 2, 1)
3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64:
[:, :, 1, 1] =
 1  4  7  10
 2  5  8  11
 3  6  9  12

[:, :, 2, 1] =
 13  16  19  22
 14  17  20  23
 15  18  21  24

julia> A[1, 3, 2] # Omits the fourth dimension (length 1)
19

julia> A[1, 3] # Attempts to omit dimensions 3 & 4 (lengths 2 and 1)
ERROR: BoundsError: attempt to access 3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64 at index [1, 3]

julia> A[19] # Linear indexing
19
```

Lorsqu'on omet *tous* les indices avec `A[]`, cette sémantique fournit un idiome simple pour récupérer le seul élément d'un tableau et s'assurer simultanément qu'il n'y avait qu'un seul élément.

De même, plus de `N` indices peuvent être fournis si tous les indices au-delà de la dimensionnalité du tableau sont `1` (ou plus généralement sont le premier et le seul élément de `axes(A, d)` où `d` est ce numéro de dimension particulier). Cela permet d'indexer des vecteurs comme des matrices à une colonne, par exemple :

```jldoctest
julia> A = [8, 6, 7]
3-element Vector{Int64}:
 8
 6
 7

julia> A[2, 1]
6
```

## Iteration

Les façons recommandées d'itérer sur un tableau entier sont

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

Le premier construct est utilisé lorsque vous avez besoin de la valeur, mais pas de l'index, de chaque élément. Dans le deuxième construct, `i` sera un `Int` si `A` est un type de tableau avec un indexation linéaire rapide ; sinon, ce sera un `CartesianIndex` :

```jldoctest
julia> A = rand(4, 3);

julia> B = view(A, 1:3, 2:3);

julia> for i in eachindex(B)
           @show i
       end
i = CartesianIndex(1, 1)
i = CartesianIndex(2, 1)
i = CartesianIndex(3, 1)
i = CartesianIndex(1, 2)
i = CartesianIndex(2, 2)
i = CartesianIndex(3, 2)
```

!!! note
    En contraste avec `for i = 1:length(A)`, itérer avec [`eachindex`](@ref) fournit un moyen efficace d'itérer sur tout type de tableau. De plus, cela prend également en charge les tableaux génériques avec un index personnalisé tel que [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl).


## Array traits

Si vous écrivez un type personnalisé [`AbstractArray`](@ref), vous pouvez spécifier qu'il a un indexage linéaire rapide en utilisant

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Ce paramètre fera en sorte que l'itération `eachindex` sur un `MyArray` utilise des entiers. Si vous ne spécifiez pas ce trait, la valeur par défaut `IndexCartesian()` est utilisée.

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

Les opérateurs suivants sont pris en charge pour les tableaux :

1. Arithmétique unaire – `-`, `+`
2. Arithmétique binaire – `-`, `+`, `*`, `/`, `\`, `^`
3. Comparaison – `==`, `!=`, `≈` ([`isapprox`](@ref)), `≉`

Pour permettre une vectorisation pratique des opérations mathématiques et autres, Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)`, par exemple `sin.(x)` ou `min.(x, y)`, pour des opérations élément par élément sur des tableaux ou des mélanges de tableaux et de scalaires (une opération [Broadcasting](@ref)) ; celles-ci ont l'avantage supplémentaire de "fusionner" en une seule boucle lorsqu'elles sont combinées avec d'autres appels de point, par exemple `sin.(cos.(x))`.

Aussi, *chaque* opérateur binaire prend en charge un [dot version](@ref man-dot-operators) qui peut être appliqué aux tableaux (et aux combinaisons de tableaux et de scalaires) dans un [fused broadcasting operations](@ref man-vectorized), par exemple `z .== sin.(x .* y)`.

Notez que des comparaisons telles que `==` opèrent sur des tableaux entiers, donnant une seule réponse booléenne. Utilisez des opérateurs de point comme `.==` pour des comparaisons élément par élément. (Pour les opérations de comparaison comme `<`, *seule* la version élément par élément `.<` est applicable aux tableaux.)

Remarquez également la différence entre `max.(a,b)`, qui [`broadcast`](@ref) [`max`](@ref) élément par élément sur `a` et `b`, et [`maximum(a)`](@ref), qui trouve la plus grande valeur dans `a`. La même relation s'applique à `min.(a, b)` et `minimum(a)`.

## Broadcasting

Il est parfois utile d'effectuer des opérations binaires élément par élément sur des tableaux de tailles différentes, comme ajouter un vecteur à chaque colonne d'une matrice. Une manière inefficace de le faire serait de répliquer le vecteur à la taille de la matrice :

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

C'est inutile lorsque les dimensions deviennent grandes, donc Julia fournit [`broadcast`](@ref), qui développe les dimensions singleton dans les arguments de tableau pour correspondre à la dimension correspondante dans l'autre tableau sans utiliser de mémoire supplémentaire, et applique la fonction donnée élément par élément :

```julia-repl
julia> broadcast(+, a, A)
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846

julia> b = rand(1,2)
1×2 Array{Float64,2}:
 0.867535  0.00457906

julia> broadcast(+, a, b)
2×2 Array{Float64,2}:
 1.71056  0.847604
 1.73659  0.873631
```

[Dotted operators](@ref man-dot-operators) tel que `.+` et `.*` sont équivalents à des appels `broadcast` (sauf qu'ils fusionnent, comme [described above](@ref man-array-and-vectorized-operators-and-functions)). Il existe également une fonction [`broadcast!`](@ref) pour spécifier une destination explicite (qui peut également être accessible de manière fusionnée par l'assignation `.=`). En fait, `f.(args...)` est équivalent à `broadcast(f, args...)`, fournissant une syntaxe pratique pour diffuser n'importe quelle fonction ([dot syntax](@ref man-vectorized)). Les "appels par points" imbriqués `f.(...)` (y compris les appels à `.+` etc.) [automatically fuse](@ref man-dot-operators) en un seul appel `broadcast`.

De plus, [`broadcast`](@ref) n'est pas limité aux tableaux (voir la documentation de la fonction) ; il gère également les scalaires, les tuples et d'autres collections. Par défaut, seuls certains types d'arguments sont considérés comme des scalaires, y compris (mais sans s'y limiter) les `Number`, les `String`, les `Symbol`, les `Type`, les `Function` et certains singletons courants comme `missing` et `nothing`. Tous les autres arguments sont itérés ou indexés élément par élément.

```jldoctest
julia> convert.(Float32, [1, 2])
2-element Vector{Float32}:
 1.0
 2.0

julia> ceil.(UInt8, [1.2 3.4; 5.6 6.7])
2×2 Matrix{UInt8}:
 0x02  0x04
 0x06  0x07

julia> string.(1:3, ". ", ["First", "Second", "Third"])
3-element Vector{String}:
 "1. First"
 "2. Second"
 "3. Third"
```

Parfois, vous souhaitez qu'un conteneur (comme un tableau) qui participerait normalement à la diffusion soit "protégé" du comportement de diffusion qui consiste à itérer sur tous ses éléments. En le plaçant à l'intérieur d'un autre conteneur (comme un élément unique [`Tuple`](@ref)), la diffusion le traitera comme une seule valeur.

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

Le type de tableau de base en Julia est le type abstrait [`AbstractArray{T,N}`](@ref). Il est paramétré par le nombre de dimensions `N` et le type d'élément `T`. [`AbstractVector`](@ref) et [`AbstractMatrix`](@ref) sont des alias pour les cas 1-d et 2-d. Les opérations sur les objets `AbstractArray` sont définies à l'aide d'opérateurs et de fonctions de niveau supérieur, d'une manière qui est indépendante du stockage sous-jacent. Ces opérations fonctionnent généralement correctement comme solution de repli pour toute implémentation de tableau spécifique.

Le type `AbstractArray` inclut tout ce qui est vaguement semblable à un tableau, et ses implémentations peuvent être assez différentes des tableaux conventionnels. Par exemple, les éléments peuvent être calculés à la demande plutôt que stockés. Cependant, tout type concret `AbstractArray{T,N}` devrait généralement implémenter au moins [`size(A)`](@ref) (retournant un tuple `Int`), [`getindex(A, i)`](@ref) et [`getindex(A, i1, ..., iN)`](@ref getindex); les tableaux mutables devraient également implémenter [`setindex!`](@ref). Il est recommandé que ces opérations aient une complexité temporelle presque constante, sinon certaines fonctions de tableau peuvent être lentement inattendues. Les types concrets devraient également généralement fournir une méthode [`similar(A, T=eltype(A), dims=size(A))`](@ref), qui est utilisée pour allouer un tableau similaire pour [`copy`](@ref) et d'autres opérations hors place. Peu importe comment un `AbstractArray{T,N}` est représenté en interne, `T` est le type d'objet retourné par l'indexation *entière* (`A[1, ..., 1]`, lorsque `A` n'est pas vide) et `N` devrait être la longueur du tuple retourné par [`size`](@ref). Pour plus de détails sur la définition d'implémentations personnalisées d'`AbstractArray`, voir le [array interface guide in the interfaces chapter](@ref man-interface-array).

`DenseArray` est un sous-type abstrait de `AbstractArray` destiné à inclure tous les tableaux où les éléments sont stockés de manière contiguë dans un ordre de colonne-major (voir [additional notes in Performance Tips](@ref man-performance-column-major)). Le type [`Array`](@ref) est une instance spécifique de `DenseArray`; [`Vector`](@ref) et [`Matrix`](@ref) sont des alias pour les cas 1-d et 2-d. Très peu d'opérations sont mises en œuvre spécifiquement pour `Array` au-delà de celles qui sont requises pour tous les `AbstractArray`; une grande partie de la bibliothèque de tableaux est mise en œuvre de manière générique, ce qui permet à tous les tableaux personnalisés de se comporter de manière similaire.

`SubArray` est une spécialisation de `AbstractArray` qui effectue l'indexation en partageant la mémoire avec le tableau original plutôt qu'en le copiant. Un `SubArray` est créé avec la fonction [`view`](@ref), qui est appelée de la même manière que [`getindex`](@ref) (avec un tableau et une série d'arguments d'index). Le résultat de `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` ressemble au résultat de `4d61726b646f776e2e436f64652822222c2022676574696e6465782229_40726566`, sauf que les données restent en place. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` stocke les vecteurs d'index d'entrée dans un objet `SubArray`, qui peut ensuite être utilisé pour indexer le tableau original de manière indirecte. En plaçant le macro [`@views`](@ref) devant une expression ou un bloc de code, tout `array[...]` dans cette expression sera converti pour créer une vue `SubArray` à la place.

[`BitArray`](@ref) sont des tableaux booléens "compressés" efficaces en espace, qui stockent un bit par valeur booléenne. Ils peuvent être utilisés de manière similaire aux tableaux `Array{Bool}` (qui stockent un octet par valeur booléenne) et peuvent être convertis de/vers ces derniers via `Array(bitarray)` et `BitArray(array)`, respectivement.

Un tableau est "stridé" s'il est stocké en mémoire avec des espacements bien définis (strides) entre ses éléments. Un tableau stridé avec un type d'élément pris en charge peut être passé à une bibliothèque externe (non-Julia) comme BLAS ou LAPACK en passant simplement son [`pointer`](@ref) et le stride pour chaque dimension. Le [`stride(A, d)`](@ref) est la distance entre les éléments le long de la dimension `d`. Par exemple, le `Array` intégré retourné par `rand(5,7,2)` a ses éléments disposés de manière contiguë dans l'ordre de colonne majeure. Cela signifie que le stride de la première dimension — l'espacement entre les éléments dans la même colonne — est `1` :

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

Le pas de la deuxième dimension est l'espacement entre les éléments dans la même ligne, en sautant autant d'éléments qu'il y en a dans une seule colonne (`5`). De même, sauter entre les deux "pages" (dans la troisième dimension) nécessite de sauter `5*7 == 35` éléments. Le [`strides`](@ref) de ce tableau est le tuple de ces trois nombres ensemble :

```julia-repl
julia> strides(A)
(1, 5, 35)
```

Dans ce cas particulier, le nombre d'éléments sautés *en mémoire* correspond au nombre de *indices linéaires* sautés. Cela n'est vrai que pour les tableaux contigus comme `Array` (et d'autres sous-types de `DenseArray`) et n'est pas vrai en général. Les vues avec des indices de plage sont un bon exemple de tableaux striés *non contigus* ; considérez `V = @view A[1:3:4, 2:2:6, 2:-1:1]`. Cette vue `V` fait référence à la même mémoire que `A` mais saute et réorganise certains de ses éléments. Le pas de la première dimension de `V` est `3` car nous ne sélectionnons qu'une ligne sur trois de notre tableau d'origine :

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

Cette vue sélectionne de manière similaire chaque colonne sur deux de notre `A` d'origine — et doit donc sauter l'équivalent de deux colonnes de cinq éléments lors du passage entre les indices dans la deuxième dimension :

```julia-repl
julia> stride(V, 2)
10
```

La troisième dimension est intéressante car son ordre est inversé ! Ainsi, pour passer de la première "page" à la seconde, il doit aller *en arrière* dans la mémoire, et donc son pas dans cette dimension est négatif !

```julia-repl
julia> stride(V, 3)
-35
```

Cela signifie que le `pointeur` pour `V` pointe en réalité vers le milieu du bloc mémoire de `A`, et il fait référence à des éléments à la fois en arrière et en avant dans la mémoire. Voir le [interface guide for strided arrays](@ref man-interface-strided-arrays) pour plus de détails sur la définition de vos propres tableaux striés. [`StridedVector`](@ref) et [`StridedMatrix`](@ref) sont des alias pratiques pour de nombreux types de tableaux intégrés qui sont considérés comme des tableaux striés, leur permettant de dispatcher vers des implémentations spécialisées qui appellent des fonctions BLAS et LAPACK hautement optimisées en utilisant simplement le pointeur et les strides.

Il convient de souligner que les strides concernent les décalages en mémoire plutôt que l'indexation. Si vous cherchez à convertir entre l'indexation linéaire (à un seul indice) et l'indexation cartésienne (multi-indice), consultez [`LinearIndices`](@ref) et [`CartesianIndices`](@ref).

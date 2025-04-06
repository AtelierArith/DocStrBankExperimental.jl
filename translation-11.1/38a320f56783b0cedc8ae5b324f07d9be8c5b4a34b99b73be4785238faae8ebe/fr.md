```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

Julia a un support pour les vecteurs creux et [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix) dans le module standard `SparseArrays`. Les tableaux creux sont des tableaux qui contiennent suffisamment de zéros pour que les stocker dans une structure de données spéciale entraîne des économies d'espace et de temps d'exécution, par rapport aux tableaux denses.

Des packages externes qui implémentent différents types de stockage sparse, des tableaux sparse multidimensionnels, et plus encore peuvent être trouvés dans [Noteworthy External Sparse Packages](@ref)

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

En Julia, les matrices creuses sont stockées dans le [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29). Les matrices creuses Julia ont le type [`SparseMatrixCSC{Tv,Ti}`](@ref), où `Tv` est le type des valeurs stockées, et `Ti` est le type entier pour stocker les pointeurs de colonne et les indices de ligne. La représentation interne de `SparseMatrixCSC` est la suivante :

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

Le stockage en colonne éparse compressé facilite et accélère l'accès aux éléments de la colonne d'une matrice éparse, tandis que l'accès à la matrice éparse par lignes est considérablement plus lent. Des opérations telles que l'insertion d'entrées précédemment non stockées une à une dans la structure CSC tendent à être lentes. Cela est dû au fait que tous les éléments de la matrice éparse qui se trouvent au-delà du point d'insertion doivent être déplacés d'une place.

Toutes les opérations sur les matrices creuses sont soigneusement mises en œuvre pour tirer parti de la structure de données CSC pour des performances optimales et éviter des opérations coûteuses.

Si vous avez des données au format CSC provenant d'une autre application ou bibliothèque, et que vous souhaitez les importer dans Julia, assurez-vous d'utiliser un indexage basé sur 1. Les indices de ligne dans chaque colonne doivent être triés, et s'ils ne le sont pas, la matrice s'affichera incorrectement. Si votre objet `SparseMatrixCSC` contient des indices de ligne non triés, une façon rapide de les trier est de faire une double transposition. Étant donné que l'opération de transposition est paresseuse, faites une copie pour matérialiser chaque transposition.

Dans certaines applications, il est pratique de stocker des valeurs zéro explicites dans un `SparseMatrixCSC`. Celles-ci *sont* acceptées par les fonctions de `Base` (mais il n'y a aucune garantie qu'elles seront préservées lors des opérations de mutation). Ces zéros stockés explicitement sont traités comme des non-zéros structurels par de nombreuses routines. La fonction [`nnz`](@ref) renvoie le nombre d'éléments stockés explicitement dans la structure de données sparse, y compris les zéros non structurels. Pour compter le nombre exact de non-zéros numériques, utilisez [`count(!iszero, x)`](@ref), qui inspecte chaque élément stocké d'une matrice sparse. [`dropzeros`](@ref), et le [`dropzeros!`](@ref) en place, peuvent être utilisés pour supprimer les zéros stockés de la matrice sparse.

```jldoctest
julia> A = sparse([1, 1, 2, 3], [1, 3, 2, 3], [0, 1, 2, 0])
3×3 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
 0  ⋅  1
 ⋅  2  ⋅
 ⋅  ⋅  0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Int64, Int64} with 2 stored entries:
 ⋅  ⋅  1
 ⋅  2  ⋅
 ⋅  ⋅  ⋅
```

## Sparse Vector Storage

Les vecteurs creux sont stockés dans un analogue proche du format de colonne creuse compressée pour les matrices creuses. En Julia, les vecteurs creux ont le type [`SparseVector{Tv,Ti}`](@ref) où `Tv` est le type des valeurs stockées et `Ti` le type entier pour les indices. La représentation interne est la suivante :

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

En ce qui concerne [`SparseMatrixCSC`](@ref), le type `SparseVector` peut également contenir des zéros stockés explicitement. (Voir [Sparse Matrix Storage](@ref man-csc).)

## Sparse Vector and Matrix Constructors

La manière la plus simple de créer un tableau creux est d'utiliser une fonction équivalente à la fonction [`zeros`](@ref) que Julia fournit pour travailler avec des tableaux denses. Pour produire un tableau creux à la place, vous pouvez utiliser le même nom avec un préfixe `sp` :

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

La fonction [`sparse`](@ref) est souvent un moyen pratique de construire des tableaux creux. Par exemple, pour construire une matrice creuse, nous pouvons entrer un vecteur `I` d'indices de lignes, un vecteur `J` d'indices de colonnes et un vecteur `V` de valeurs stockées (ceci est également connu sous le nom de [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29)). `sparse(I,J,V)` construit alors une matrice creuse telle que `S[I[k], J[k]] = V[k]`. Le constructeur de vecteur creux équivalent est [`sparsevec`](@ref), qui prend le vecteur d'indices (de ligne) `I` et le vecteur `V` avec les valeurs stockées et construit un vecteur creux `R` tel que `R[I[k]] = V[k]`.

```jldoctest sparse_function
julia> I = [1, 4, 3, 5]; J = [4, 7, 18, 9]; V = [1, 2, -5, 3];

julia> S = sparse(I,J,V)
5×18 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
⎡⠀⠈⠀⠀⠀⠀⠀⠀⢀⎤
⎣⠀⠀⠀⠂⡀⠀⠀⠀⠀⎦

julia> R = sparsevec(I,V)
5-element SparseVector{Int64, Int64} with 4 stored entries:
  [1]  =  1
  [3]  =  -5
  [4]  =  2
  [5]  =  3
```

L'inverse des fonctions [`sparse`](@ref) et [`sparsevec`](@ref) est [`findnz`](@ref), qui récupère les entrées utilisées pour créer le tableau sparse (y compris les entrées stockées égales à zéro). [`findall(!iszero, x)`](@ref) renvoie les indices cartésiens des entrées non nulles dans `x` (sans inclure les entrées stockées égales à zéro).

```jldoctest sparse_function
julia> findnz(S)
([1, 4, 5, 3], [4, 7, 9, 18], [1, 2, 3, -5])

julia> findall(!iszero, S)
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 4)
 CartesianIndex(4, 7)
 CartesianIndex(5, 9)
 CartesianIndex(3, 18)

julia> findnz(R)
([1, 3, 4, 5], [1, -5, 2, 3])

julia> findall(!iszero, R)
4-element Vector{Int64}:
 1
 3
 4
 5
```

Une autre façon de créer un tableau sparse est de convertir un tableau dense en un tableau sparse en utilisant la fonction [`sparse`](@ref) :

```jldoctest
julia> sparse(Matrix(1.0I, 5, 5))
5×5 SparseMatrixCSC{Float64, Int64} with 5 stored entries:
 1.0   ⋅    ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅   1.0   ⋅    ⋅
  ⋅    ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅    ⋅   1.0

julia> sparse([1.0, 0.0, 1.0])
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [3]  =  1.0
```

Vous pouvez aller dans l'autre direction en utilisant le constructeur [`Array`](@ref). La fonction [`issparse`](@ref) peut être utilisée pour interroger si une matrice est éparse.

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

Les opérations arithmétiques sur les matrices creuses fonctionnent également comme sur les matrices denses. L'indexation, l'assignation et la concaténation des matrices creuses fonctionnent de la même manière que pour les matrices denses. Les opérations d'indexation, en particulier l'assignation, sont coûteuses lorsqu'elles sont effectuées un élément à la fois. Dans de nombreux cas, il peut être préférable de convertir la matrice creuse en format `(I,J,V)` en utilisant [`findnz`](@ref), de manipuler les valeurs ou la structure dans les vecteurs denses `(I,J,V)`, puis de reconstruire la matrice creuse.

## Correspondence of dense and sparse methods

Le tableau suivant donne une correspondance entre les méthodes intégrées sur les matrices creuses et leurs méthodes correspondantes sur les types de matrices denses. En général, les méthodes qui génèrent des matrices creuses diffèrent de leurs homologues denses en ce sens que la matrice résultante suit le même motif de parcimonie qu'une matrice creuse donnée `S`, ou que la matrice creuse résultante a une densité `d`, c'est-à-dire que chaque élément de la matrice a une probabilité `d` d'être non nul.

Les détails peuvent être trouvés dans la section [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) de la référence de la bibliothèque standard.

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

Les solveurs de matrices creuses appellent des fonctions de [SuiteSparse](http://suitesparse.com). Les factorisations suivantes sont disponibles :

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

Ces factorizations sont décrites plus en détail dans le [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api) :

1. [`cholesky`](@ref SparseArrays.CHOLMOD.cholesky)
2. [`ldlt`](@ref SparseArrays.CHOLMOD.ldlt)
3. [`lu`](@ref SparseArrays.UMFPACK.lu)
4. [`qr`](@ref SparseArrays.SPQR.qr)

```@meta
DocTestSetup = nothing
```

# [SparseArrays API](@id stdlib-sparse-arrays)

```@docs
SparseArrays.AbstractSparseArray
SparseArrays.AbstractSparseVector
SparseArrays.AbstractSparseMatrix
SparseArrays.SparseVector
SparseArrays.SparseMatrixCSC
SparseArrays.sparse
SparseArrays.sparse!
SparseArrays.sparsevec
Base.similar(::SparseArrays.AbstractSparseMatrixCSC, ::Type)
SparseArrays.issparse
SparseArrays.nnz
SparseArrays.findnz
SparseArrays.spzeros
SparseArrays.spzeros!
SparseArrays.spdiagm
SparseArrays.sparse_hcat
SparseArrays.sparse_vcat
SparseArrays.sparse_hvcat
SparseArrays.blockdiag
SparseArrays.sprand
SparseArrays.sprandn
SparseArrays.nonzeros
SparseArrays.rowvals
SparseArrays.nzrange
SparseArrays.droptol!
SparseArrays.dropzeros!
SparseArrays.dropzeros
SparseArrays.permute
permute!{Tv, Ti, Tp <: Integer, Tq <: Integer}(::SparseMatrixCSC{Tv,Ti}, ::SparseMatrixCSC{Tv,Ti}, ::AbstractArray{Tp,1}, ::AbstractArray{Tq,1})
SparseArrays.halfperm!
SparseArrays.ftranspose!
```

```@meta
DocTestSetup = nothing
```

# [Sparse Linear Algebra API](@id stdlib-sparse-linalg-api)

```@docs; canonical=false
SparseArrays.CHOLMOD.cholesky
SparseArrays.CHOLMOD.cholesky!
SparseArrays.CHOLMOD.lowrankupdate
SparseArrays.CHOLMOD.lowrankupdate!
SparseArrays.CHOLMOD.lowrankdowndate
SparseArrays.CHOLMOD.lowrankdowndate!
SparseArrays.CHOLMOD.lowrankupdowndate!
SparseArrays.CHOLMOD.ldlt
SparseArrays.UMFPACK.lu
SparseArrays.SPQR.qr
```

```@meta
DocTestSetup = nothing
```

# Noteworthy External Sparse Packages

Plusieurs autres packages Julia fournissent des implémentations de matrices creuses qui devraient être mentionnées :

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl) est un wrapper sur la bibliothèque C SuiteSparse:GraphBLAS rapide et multithreadée. Sur CPU, c'est généralement l'option la plus rapide, surpassant souvent de manière significative MKLSparse.
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) expose la bibliothèque [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) pour les opérations de matrices creuses sur GPU.
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl) fournit une implémentation native en Julia du format Compressed Sparse Rows (CSR).
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl) accélère les opérations de matrices creuses-denses SparseArrays en utilisant la bibliothèque MKL d'Intel.
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) disponible pour des tableaux creux multidimensionnels.
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl) fournit des formats de tableau clairsemé statiques, ainsi qu'un format de coordonnées.
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl) permet une insertion rapide dans des matrices creuses en utilisant une approche paresseuse pour les nouveaux indices stockés.
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl) prend en charge des formats et des opérations de tableaux creux multidimensionnels étendus grâce à un mini langage de tenseurs et un compilateur, le tout en Julia natif. Prise en charge de COO, CSF, CSR, CSC et plus encore, ainsi que des opérations comme le broadcast, la réduction, etc. et des opérations personnalisées.

Packages externes fournissant des solveurs directs creux :

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

Packages externes fournissant des solveurs pour la solution itérative des systèmes d'eigenvalues et des décompositions en valeurs singulières :

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

Packages externes pour travailler avec des graphes :

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)

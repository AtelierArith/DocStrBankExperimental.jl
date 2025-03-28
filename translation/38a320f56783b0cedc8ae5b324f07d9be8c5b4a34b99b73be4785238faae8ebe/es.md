```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

Julia tiene soporte para vectores dispersos y [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix) en el módulo estándar `SparseArrays`. Los arreglos dispersos son arreglos que contienen suficientes ceros como para que almacenarlos en una estructura de datos especial conlleve ahorros en espacio y tiempo de ejecución, en comparación con los arreglos densos.

Se pueden encontrar paquetes externos que implementan diferentes tipos de almacenamiento disperso, arreglos dispersos multidimensionales y más en [Noteworthy External Sparse Packages](@ref)

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

En Julia, las matrices dispersas se almacenan en el [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29). Las matrices dispersas de Julia tienen el tipo [`SparseMatrixCSC{Tv,Ti}`](@ref), donde `Tv` es el tipo de los valores almacenados, y `Ti` es el tipo entero para almacenar punteros de columna e índices de fila. La representación interna de `SparseMatrixCSC` es la siguiente:

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

El almacenamiento en columnas dispersas comprimidas facilita y acelera el acceso a los elementos en la columna de una matriz dispersa, mientras que el acceso a la matriz dispersa por filas es considerablemente más lento. Operaciones como la inserción de entradas previamente no almacenadas una a la vez en la estructura CSC tienden a ser lentas. Esto se debe a que todos los elementos de la matriz dispersa que están más allá del punto de inserción deben ser movidos un lugar hacia adelante.

Todas las operaciones en matrices dispersas están cuidadosamente implementadas para aprovechar la estructura de datos CSC para el rendimiento y evitar operaciones costosas.

Si tienes datos en formato CSC de una aplicación o biblioteca diferente, y deseas importarlos en Julia, asegúrate de usar indexación basada en 1. Los índices de fila en cada columna deben estar ordenados, y si no lo están, la matriz se mostrará incorrectamente. Si tu objeto `SparseMatrixCSC` contiene índices de fila desordenados, una forma rápida de ordenarlos es haciendo una doble transposición. Dado que la operación de transposición es perezosa, haz una copia para materializar cada transposición.

En algunas aplicaciones, es conveniente almacenar valores cero explícitos en un `SparseMatrixCSC`. Estos *son* aceptados por funciones en `Base` (pero no hay garantía de que se conserven en operaciones mutantes). Tales ceros almacenados explícitamente se tratan como no ceros estructurales por muchas rutinas. La función [`nnz`](@ref) devuelve el número de elementos almacenados explícitamente en la estructura de datos dispersa, incluidos los ceros no estructurales. Para contar el número exacto de no ceros numéricos, utiliza [`count(!iszero, x)`](@ref), que inspecciona cada elemento almacenado de una matriz dispersa. [`dropzeros`](@ref), y el [`dropzeros!`](@ref) en su lugar, se pueden usar para eliminar ceros almacenados de la matriz dispersa.

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

Los vectores dispersos se almacenan en un análogo cercano al formato de columna dispersa comprimida para matrices dispersas. En Julia, los vectores dispersos tienen el tipo [`SparseVector{Tv,Ti}`](@ref) donde `Tv` es el tipo de los valores almacenados y `Ti` el tipo entero para los índices. La representación interna es la siguiente:

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

En cuanto a [`SparseMatrixCSC`](@ref), el tipo `SparseVector` también puede contener ceros almacenados explícitamente. (Ver [Sparse Matrix Storage](@ref man-csc).)

## Sparse Vector and Matrix Constructors

La forma más sencilla de crear un arreglo disperso es usar una función equivalente a la función [`zeros`](@ref) que Julia proporciona para trabajar con arreglos densos. Para producir un arreglo disperso en su lugar, puedes usar el mismo nombre con un prefijo `sp`:

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

La función [`sparse`](@ref) es a menudo una forma útil de construir arreglos dispersos. Por ejemplo, para construir una matriz dispersa podemos ingresar un vector `I` de índices de fila, un vector `J` de índices de columna y un vector `V` de valores almacenados (esto también se conoce como [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29)). `sparse(I,J,V)` construye entonces una matriz dispersa tal que `S[I[k], J[k]] = V[k]`. El constructor de vector disperso equivalente es [`sparsevec`](@ref), que toma el vector de índices (de fila) `I` y el vector `V` con los valores almacenados y construye un vector disperso `R` tal que `R[I[k]] = V[k]`.

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

La inversa de las funciones [`sparse`](@ref) y [`sparsevec`](@ref) es [`findnz`](@ref), que recupera las entradas utilizadas para crear el arreglo disperso (incluyendo entradas almacenadas iguales a cero). [`findall(!iszero, x)`](@ref) devuelve los índices cartesianos de las entradas no nulas en `x` (sin incluir entradas almacenadas iguales a cero).

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

Otra forma de crear un arreglo disperso es convertir un arreglo denso en un arreglo disperso utilizando la función [`sparse`](@ref):

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

Puedes ir en la otra dirección utilizando el constructor [`Array`](@ref). La función [`issparse`](@ref) se puede usar para consultar si una matriz es dispersa.

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

Las operaciones aritméticas en matrices dispersas también funcionan como lo hacen en matrices densas. La indexación, la asignación y la concatenación de matrices dispersas funcionan de la misma manera que las matrices densas. Las operaciones de indexación, especialmente la asignación, son costosas cuando se realizan un elemento a la vez. En muchos casos, puede ser mejor convertir la matriz dispersa en formato `(I,J,V)` utilizando [`findnz`](@ref), manipular los valores o la estructura en los vectores densos `(I,J,V)`, y luego reconstruir la matriz dispersa.

## Correspondence of dense and sparse methods

La siguiente tabla proporciona una correspondencia entre los métodos incorporados en matrices dispersas y sus métodos correspondientes en tipos de matrices densas. En general, los métodos que generan matrices dispersas difieren de sus contrapartes densas en que la matriz resultante sigue el mismo patrón de dispersión que una matriz dispersa dada `S`, o que la matriz dispersa resultante tiene una densidad `d`, es decir, cada elemento de la matriz tiene una probabilidad `d` de ser diferente de cero.

Los detalles se pueden encontrar en la sección [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) de la referencia de la biblioteca estándar.

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

Los solucionadores de matrices dispersas llaman a funciones de [SuiteSparse](http://suitesparse.com). Las siguientes factorizaciones están disponibles:

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

Estas factorizaciones se describen con más detalle en el [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api):

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

Varios otros paquetes de Julia proporcionan implementaciones de matrices dispersas que deben ser mencionadas:

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl) es un envoltorio sobre la rápida biblioteca C SuiteSparse:GraphBLAS multihilo. En CPU, esta es típicamente la opción más rápida, a menudo superando significativamente a MKLSparse.
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) expone la biblioteca [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) para operaciones de matrices dispersas en GPU.
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl) proporciona una implementación nativa en Julia del formato de Filas Escasas Comprimidas (CSR).
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl) acelera las operaciones de matrices dispersas-densas de SparseArrays utilizando la biblioteca MKL de Intel.
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) disponible para arreglos dispersos multidimensionales.
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl) proporciona formatos de arreglos dispersos estáticos, así como un formato de coordenadas.
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl) permite una inserción rápida en matrices dispersas utilizando un enfoque perezoso para nuevos índices almacenados.
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl) admite formatos y operaciones de arreglos dispersos multidimensionales extensos a través de un mini lenguaje de tensores y compilador, todo en Julia nativa. Soporte para COO, CSF, CSR, CSC y más, así como operaciones como difusión, reducción, etc. y operaciones personalizadas.

Paquetes externos que proporcionan solucionadores directos dispersos:

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

Paquetes externos que proporcionan solucionadores para la solución iterativa de sistemas de eigenvalores y descomposiciones en valores singulares:

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

Paquetes externos para trabajar con gráficos:

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)

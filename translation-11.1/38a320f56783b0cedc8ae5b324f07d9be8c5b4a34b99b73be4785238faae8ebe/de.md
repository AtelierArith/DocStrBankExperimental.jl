```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

Julia unterstützt spärliche Vektoren und [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix) im `SparseArrays`-Standardbibliotheksmodul. Spärliche Arrays sind Arrays, die genügend Nullen enthalten, sodass die Speicherung in einer speziellen Datenstruktur zu Einsparungen bei Speicherplatz und Ausführungszeit im Vergleich zu dichten Arrays führt.

Externe Pakete, die verschiedene spärliche Speicherarten, mehrdimensionale spärliche Arrays und mehr implementieren, sind in [Noteworthy External Sparse Packages](@ref) zu finden.

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

In Julia werden spärliche Matrizen im [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29) gespeichert. Julia spärliche Matrizen haben den Typ [`SparseMatrixCSC{Tv,Ti}`](@ref), wobei `Tv` der Typ der gespeicherten Werte und `Ti` der Ganzzahltyp für die Speicherung von Spaltenzeigern und Zeilenindizes ist. Die interne Darstellung von `SparseMatrixCSC` ist wie folgt:

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

Die komprimierte spärliche Spaltenspeicherung erleichtert und beschleunigt den Zugriff auf die Elemente in der Spalte einer spärlichen Matrix, während der Zugriff auf die spärliche Matrix nach Zeilen erheblich langsamer ist. Operationen wie das Einfügen zuvor nicht gespeicherter Einträge einzeln in die CSC-Struktur tendieren dazu, langsam zu sein. Dies liegt daran, dass alle Elemente der spärlichen Matrix, die über den Einfügepunkt hinausgehen, um einen Platz verschoben werden müssen.

Alle Operationen auf spärlichen Matrizen sind sorgfältig implementiert, um die CSC-Datenstruktur für die Leistung zu nutzen und teure Operationen zu vermeiden.

Wenn Sie Daten im CSC-Format aus einer anderen Anwendung oder Bibliothek haben und diese in Julia importieren möchten, stellen Sie sicher, dass Sie die 1-basierte Indizierung verwenden. Die Zeilenindizes in jeder Spalte müssen sortiert sein, und wenn dies nicht der Fall ist, wird die Matrix falsch angezeigt. Wenn Ihr `SparseMatrixCSC`-Objekt unsortierte Zeilenindizes enthält, ist eine schnelle Möglichkeit, sie zu sortieren, eine doppelte Transponierung durchzuführen. Da die Transponierungsoperation faul ist, erstellen Sie eine Kopie, um jede Transponierung zu materialisieren.

In einigen Anwendungen ist es praktisch, explizite Nullwerte in einer `SparseMatrixCSC` zu speichern. Diese *werden* von Funktionen in `Base` akzeptiert (aber es gibt keine Garantie, dass sie bei mutierenden Operationen erhalten bleiben). Solche explizit gespeicherten Nullen werden von vielen Routinen als strukturelle Nicht-Nullwerte behandelt. Die Funktion [`nnz`](@ref) gibt die Anzahl der explizit im sparsamen Datenspeicher gespeicherten Elemente zurück, einschließlich nicht-struktureller Nullen. Um die genaue Anzahl der numerischen Nicht-Nullwerte zu zählen, verwenden Sie [`count(!iszero, x)`](@ref), die jedes gespeicherte Element einer spärlichen Matrix inspiziert. [`dropzeros`](@ref) und das In-Place [`dropzeros!`](@ref) können verwendet werden, um gespeicherte Nullen aus der spärlichen Matrix zu entfernen.

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

Sparse-Vektoren werden in einem engen Analogon zum komprimierten spärlichen Spaltenformat für spärliche Matrizen gespeichert. In Julia haben spärliche Vektoren den Typ [`SparseVector{Tv,Ti}`](@ref), wobei `Tv` der Typ der gespeicherten Werte und `Ti` der Ganzzahltyp für die Indizes ist. Die interne Darstellung ist wie folgt:

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

Was [`SparseMatrixCSC`](@ref) betrifft, kann der `SparseVector`-Typ auch explizit gespeicherte Nullen enthalten. (Siehe [Sparse Matrix Storage](@ref man-csc).)

## Sparse Vector and Matrix Constructors

Der einfachste Weg, ein spärliches Array zu erstellen, besteht darin, eine Funktion zu verwenden, die der [`zeros`](@ref)-Funktion entspricht, die Julia für die Arbeit mit dichten Arrays bereitstellt. Um stattdessen ein spärliches Array zu erzeugen, können Sie denselben Namen mit einem `sp`-Präfix verwenden:

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

Die [`sparse`](@ref) Funktion ist oft eine praktische Möglichkeit, spärliche Arrays zu konstruieren. Zum Beispiel können wir, um eine spärliche Matrix zu konstruieren, einen Vektor `I` mit Zeilenindizes, einen Vektor `J` mit Spaltenindizes und einen Vektor `V` mit gespeicherten Werten eingeben (dies ist auch bekannt als der [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29)). `sparse(I,J,V)` konstruiert dann eine spärliche Matrix, so dass `S[I[k], J[k]] = V[k]`. Der entsprechende Konstruktor für spärliche Vektoren ist [`sparsevec`](@ref), der den (Zeilen-)Indexvektor `I` und den Vektor `V` mit den gespeicherten Werten nimmt und einen spärlichen Vektor `R` konstruiert, so dass `R[I[k]] = V[k]`.

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

Die Inverse der Funktionen [`sparse`](@ref) und [`sparsevec`](@ref) ist [`findnz`](@ref), die die Eingaben abruft, die zur Erstellung des spärlichen Arrays verwendet wurden (einschließlich gespeicherter Einträge, die gleich null sind). [`findall(!iszero, x)`](@ref) gibt die kartesischen Indizes der Nicht-Null-Einträge in `x` zurück (ohne gespeicherte Einträge, die gleich null sind).

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

Eine weitere Möglichkeit, ein spärliches Array zu erstellen, besteht darin, ein dichtes Array in ein spärliches Array mit der Funktion [`sparse`](@ref) zu konvertieren:

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

Sie können in die andere Richtung gehen, indem Sie den [`Array`](@ref) Konstruktor verwenden. Die [`issparse`](@ref) Funktion kann verwendet werden, um abzufragen, ob eine Matrix spärlich ist.

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

Arithmetische Operationen auf spärlichen Matrizen funktionieren ebenso wie bei dichten Matrizen. Das Indizieren, die Zuweisung und die Verkettung von spärlichen Matrizen funktionieren auf die gleiche Weise wie bei dichten Matrizen. Indizierungsoperationen, insbesondere Zuweisungen, sind teuer, wenn sie Element für Element durchgeführt werden. In vielen Fällen kann es besser sein, die spärliche Matrix in das `(I,J,V)`-Format zu konvertieren, indem man [`findnz`](@ref) verwendet, die Werte oder die Struktur in den dichten Vektoren `(I,J,V)` zu manipulieren und dann die spärliche Matrix wiederherzustellen.

## Correspondence of dense and sparse methods

Die folgende Tabelle zeigt eine Entsprechung zwischen integrierten Methoden für spärliche Matrizen und ihren entsprechenden Methoden für dichte Matrizen. Im Allgemeinen unterscheiden sich Methoden, die spärliche Matrizen erzeugen, von ihren dichten Gegenstücken darin, dass die resultierende Matrix dasselbe Sparsamkeitsmuster wie eine gegebene spärliche Matrix `S` aufweist oder dass die resultierende spärliche Matrix eine Dichte `d` hat, d.h. jedes Matrixelement hat eine Wahrscheinlichkeit `d`, ungleich null zu sein.

Details können im Abschnitt [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) des Referenzhandbuchs der Standardbibliothek gefunden werden.

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

Sparse-Matrix-Löser rufen Funktionen von [SuiteSparse](http://suitesparse.com) auf. Die folgenden Faktorisierungen sind verfügbar:

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

Diese Faktorisierungen werden ausführlicher beschrieben in der [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api):

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

Mehrere andere Julia-Pakete bieten Implementierungen von spärlichen Matrizen, die erwähnt werden sollten:

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl) ist ein Wrapper über die schnelle, multithreaded SuiteSparse:GraphBLAS C-Bibliothek. Auf der CPU ist dies typischerweise die schnellste Option, die oft MKLSparse erheblich übertrifft.
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) exponiert die [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) Bibliothek für GPU-sparsame Matrixoperationen.
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl) bietet eine native Julia-Implementierung des Compressed Sparse Rows (CSR) Formats.
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl) beschleunigt SparseArrays sparse-dense Matrixoperationen mit Intels MKL-Bibliothek.
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) verfügbar für mehrdimensionale spärliche Arrays.
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl) bietet statische spärliche Array-Formate sowie ein Koordinatenformat.
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl) ermöglicht eine schnelle Einfügung in spärliche Matrizen unter Verwendung eines faulen Ansatzes für neue gespeicherte Indizes.
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl) unterstützt umfangreiche multidimensionale spärliche Array-Formate und -Operationen durch eine Mini-Tensor-Sprache und einen Compiler, alles in nativem Julia. Unterstützung für COO, CSF, CSR, CSC und mehr, sowie Operationen wie Broadcast, Reduce usw. und benutzerdefinierte Operationen.

Externe Pakete, die spärliche direkte Solver bereitstellen:

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

Externe Pakete, die Löser für die iterative Lösung von Eigenwertsystemen und singulären Wertzerlegungen bereitstellen:

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

Externe Pakete zur Arbeit mit Graphen:

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)

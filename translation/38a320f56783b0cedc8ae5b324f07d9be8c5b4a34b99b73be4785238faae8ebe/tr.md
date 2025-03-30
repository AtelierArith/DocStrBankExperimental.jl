```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

Julia, seyrek vektörler ve [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix) için `SparseArrays` stdlib modülünde destek sunmaktadır. Seyrek diziler, yeterince sıfır içeren dizilerdir; bu dizileri özel bir veri yapısında saklamak, yoğun dizilere kıyasla alan ve yürütme süresinde tasarruf sağlar.

Farklı seyrek depolama türlerini, çok boyutlu seyrek dizileri ve daha fazlasını uygulayan harici paketler [Noteworthy External Sparse Packages](@ref) içinde bulunabilir.

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

Julia'da seyrek matrisler [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29) içinde saklanır. Julia seyrek matrislerinin tipi [`SparseMatrixCSC{Tv,Ti}`](@ref) şeklindedir; burada `Tv` saklanan değerlerin tipi ve `Ti` sütun işaretçileri ve satır indekslerini saklamak için kullanılan tam sayı tipidir. `SparseMatrixCSC`'nin içsel temsili aşağıdaki gibidir:

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

Sıkıştırılmış seyrek sütun depolama, seyrek bir matrisin sütunundaki elemanlara erişimi kolay ve hızlı hale getirirken, seyrek matrisi satırlar halinde erişmek oldukça daha yavaştır. CSC yapısında daha önce depolanmamış girişlerin birer birer eklenmesi gibi işlemler yavaş olma eğilimindedir. Bunun nedeni, ekleme noktasının ötesindeki seyrek matrisin tüm elemanlarının bir yer kaydırılması gerektiğidir.

Seyrek matrisler üzerindeki tüm işlemler, performans için CSC veri yapısını kullanacak şekilde dikkatlice uygulanmıştır ve pahalı işlemlerden kaçınılmıştır.

Eğer farklı bir uygulamadan veya kütüphaneden CSC formatında veriniz varsa ve bunu Julia'ya aktarmak istiyorsanız, 1 tabanlı indeksleme kullandığınızdan emin olun. Her sütundaki satır indeksleri sıralı olmalıdır ve eğer sıralı değillerse, matris yanlış bir şekilde görüntülenecektir. Eğer `SparseMatrixCSC` nesneniz sıralanmamış satır indeksleri içeriyorsa, bunları sıralamanın hızlı bir yolu çift transpoz yapmaktır. Transpoz işlemi tembel olduğu için, her transpozun somutlaşması için bir kopya oluşturun.

Bazı uygulamalarda, `SparseMatrixCSC` içinde açık sıfır değerlerini saklamak kullanışlıdır. Bu değerler `Base` içindeki fonksiyonlar tarafından *kabul edilir* (ancak mutasyona uğrayan işlemlerde korunacaklarına dair bir garanti yoktur). Açıkça saklanan bu sıfırlar, birçok rutin tarafından yapısal sıfır olmayanlar olarak değerlendirilir. [`nnz`](@ref) fonksiyonu, yapısal olmayan sıfırlar da dahil olmak üzere, seyrek veri yapısında açıkça saklanan elemanların sayısını döndürür. Sayısal sıfır olmayanların tam sayısını saymak için, her bir saklanan elemanı inceleyen [`count(!iszero, x)`](@ref) fonksiyonunu kullanın. [`dropzeros`](@ref) ve yerinde [`dropzeros!`](@ref) fonksiyonları, saklanan sıfırları seyrek matrisinden kaldırmak için kullanılabilir.

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

Seyrek vektörler, seyrek matrisler için sıkıştırılmış seyrek sütun formatına yakın bir şekilde saklanır. Julia'da, seyrek vektörlerin tipi [`SparseVector{Tv,Ti}`](@ref) şeklindedir; burada `Tv` saklanan değerlerin tipi ve `Ti` ise indeksler için tam sayı tipidir. İçsel temsil aşağıdaki gibidir:

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

[`SparseMatrixCSC`](@ref) için `SparseVector` türü ayrıca açıkça saklanan sıfırlar da içerebilir. (Bkz. [Sparse Matrix Storage](@ref man-csc).)

## Sparse Vector and Matrix Constructors

En basit seyrek dizi oluşturma yolu, Julia'nın yoğun dizilerle çalışmak için sağladığı [`zeros`](@ref) fonksiyonuna eşdeğer bir fonksiyon kullanmaktır. Bunun yerine seyrek bir dizi üretmek için, aynı ismi `sp` ön eki ile kullanabilirsiniz:

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

[`sparse`](@ref) fonksiyonu genellikle seyrek diziler oluşturmak için kullanışlı bir yoldur. Örneğin, bir seyrek matris oluşturmak için bir satır indeksleri vektörü `I`, bir sütun indeksleri vektörü `J` ve saklanan değerler vektörü `V` girebiliriz (bu aynı zamanda [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29) olarak bilinir). `sparse(I,J,V)` ardından `S[I[k], J[k]] = V[k]` olacak şekilde bir seyrek matris oluşturur. Eşdeğer seyrek vektör yapıcı [`sparsevec`](@ref) olup, (satır) indeks vektörü `I` ve saklanan değerlerle birlikte vektör `V` alır ve `R[I[k]] = V[k]` olacak şekilde bir seyrek vektör `R` oluşturur.

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

[`sparse`](@ref) ve [`sparsevec`](@ref) fonksiyonlarının tersinin [`findnz`](@ref) olduğu, seyrek diziyi oluşturmak için kullanılan girdileri (sıfıra eşit olan saklanan girişler dahil) geri getirdiği belirtilmektedir. [`findall(!iszero, x)`](@ref) ise `x` içindeki sıfıra eşit olmayan girişlerin Kartezyen indekslerini döndürmektedir (sıfıra eşit olan saklanan girişler dahil değildir).

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

Başka bir seyrek dizi oluşturmanın bir yolu, yoğun bir diziyi [`sparse`](@ref) fonksiyonunu kullanarak seyrek bir diziye dönüştürmektir:

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

Diğer yönde [`Array`](@ref) yapıcısını kullanarak gidebilirsiniz. [`issparse`](@ref) fonksiyonu, bir matrisin seyrek olup olmadığını sorgulamak için kullanılabilir.

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

Seyrek matrisler üzerinde aritmetik işlemler, yoğun matrislerde olduğu gibi çalışır. Seyrek matrislerin indekslenmesi, atanması ve birleştirilmesi, yoğun matrisler gibi aynı şekilde çalışır. İndeksleme işlemleri, özellikle atama, bir seferde bir eleman üzerinde gerçekleştirildiğinde pahalıdır. Birçok durumda, seyrek matrisi [`findnz`](@ref) formatına dönüştürmek, değerleri veya yapıyı yoğun vektörlerde `(I,J,V)` manipüle etmek ve ardından seyrek matrisi yeniden inşa etmek daha iyi olabilir.

## Correspondence of dense and sparse methods

Aşağıdaki tablo, seyrek matrisler üzerindeki yerleşik yöntemler ile yoğun matris türlerindeki karşılık gelen yöntemler arasındaki ilişkiyi vermektedir. Genel olarak, seyrek matrisler üreten yöntemler, sonuçta elde edilen matrisin belirli bir seyrek matris `S` ile aynı seyreklik desenini takip etmesi veya sonuçta elde edilen seyrek matrisin yoğunluğunun `d` olması, yani her matris elemanının sıfır olmama olasılığının `d` olması açısından yoğun karşıtlarından farklıdır.

Detaylar, standart kütüphane referansının [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) bölümünde bulunabilir.

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

Seyrek matris çözücüleri [SuiteSparse](http://suitesparse.com) adresinden fonksiyonlar çağırır. Aşağıdaki faktorizasyonlar mevcuttur:

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

Bu faktorizasyonlar, [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api) içinde daha ayrıntılı olarak açıklanmaktadır:

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

Birçok diğer Julia paketi, bahsedilmesi gereken seyrek matris uygulamaları sunmaktadır:

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl) hızlı, çok iş parçacıklı SuiteSparse:GraphBLAS C kütüphanesinin bir sarmalayıcısıdır. CPU'da bu genellikle en hızlı seçenektir ve genellikle MKLSparse'den önemli ölçüde daha iyi performans gösterir.
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) GPU seyrek matris işlemleri için [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) kütüphanesini açığa çıkarır.
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl) sıkıştırılmış seyrek satır (CSR) formatının Julia yerel uygulamasını sağlar.
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl) Intel'in MKL kütüphanesini kullanarak SparseArrays seyrek-sık matris işlemlerini hızlandırır.
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) çok boyutlu seyrek diziler için mevcuttur.
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl) statik seyrek dizi formatları ve bir koordinat formatı sağlar.
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl) enables fast insertion into sparse matrices using a lazy approach to new stored indices.
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl) çok boyutlu seyrek dizi formatları ve işlemleri için kapsamlı destek sunar; bu, yerel Julia'da mini bir tensör dili ve derleyici aracılığıyla gerçekleştirilir. COO, CSF, CSR, CSC ve daha fazlası için destek ile birlikte yayın, azaltma vb. gibi işlemler ve özel işlemler de mevcuttur.

Dış paketler, seyrek doğrudan çözücüler sağlar:

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

Dış paketler, özdeğer sistemlerinin ve tekil değer ayrıştırmalarının yinelemeli çözümü için çözücüler sağlar:

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

Dışa bağımlı paketler ile grafiklerle çalışma:

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)

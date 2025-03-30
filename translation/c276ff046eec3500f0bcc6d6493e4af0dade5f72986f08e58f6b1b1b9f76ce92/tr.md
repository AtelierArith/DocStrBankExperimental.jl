# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

Julia, diğer teknik hesaplama dilleri gibi, birinci sınıf bir dizi uygulaması sunar. Çoğu teknik hesaplama dili, diğer konteynerler pahasına dizi uygulamalarına büyük önem verir. Julia dizileri özel bir şekilde ele almaz. Dizi kütüphanesi neredeyse tamamen Julia'nın kendisiyle uygulanmıştır ve performansını, Julia'da yazılan diğer kodlar gibi, derleyiciden alır. Bu nedenle, [`AbstractArray`](@ref)'dan miras alarak özel dizi türleri tanımlamak da mümkündür. Özel bir dizi türü uygulamak için daha fazla ayrıntı için [manual section on the AbstractArray interface](@ref man-interface-array)'ya bakın.

Bir dizi, çok boyutlu bir ızgarada saklanan nesnelerin bir koleksiyonudur. Sıfır boyutlu dizilere izin verilir, bkz. [this FAQ entry](@ref faq-array-0dim). En genel durumda, bir dizi [`Any`](@ref) türünde nesneler içerebilir. Çoğu hesaplama amacı için diziler, [`Float64`](@ref) veya [`Int32`](@ref) gibi daha spesifik türde nesneler içermelidir.

Genel olarak, birçok diğer teknik hesaplama dillerinin aksine, Julia performans için programların vektörleştirilmiş bir tarzda yazılmasını beklemez. Julia'nın derleyicisi tür çıkarımı kullanır ve skalar dizi indeksleme için optimize edilmiş kod üretir, bu da programların performanstan ödün vermeden, okunabilir ve kullanışlı bir tarzda yazılmasına olanak tanır ve bazen daha az bellek kullanır.

In Julia, tüm fonksiyon argümanları [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing) (yani, işaretçilerle) geçilir. Bazı teknik hesaplama dilleri dizileri değerle geçirir ve bu, çağrılanların çağıranın bir değerini kazara değiştirmesini önlese de, dizilerin istenmeyen kopyalanmasını önlemeyi zorlaştırır. Gelenek olarak, `!` ile biten bir fonksiyon adı, bir veya daha fazla argümanının değerini değiştireceğini veya yok edeceğini belirtir (örneğin, [`sort`](@ref) ve [`sort!`](@ref) ile karşılaştırın). Çağrılanlar, değiştirmek istemedikleri girdileri değiştirmediklerinden emin olmak için açık kopyalar yapmalıdır. Birçok değiştirmeyen fonksiyon, girdinin açık bir kopyasında sonuna eklenmiş `!` ile aynı isimdeki bir fonksiyonu çağırarak ve o kopyayı döndürerek uygulanır.

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

Bir dizi oluşturma ve başlatma için birçok işlev sağlanmıştır. Aşağıdaki bu tür işlevlerin listesinde, `dims...` argümanına sahip çağrılar ya bir boyut boyutları demetini alabilir ya da değişken sayıda argüman olarak bir dizi boyut boyutunu alabilir. Bu işlevlerin çoğu ayrıca dizinin eleman türü olan birinci girdi `T`'yi de kabul eder. `T` türü atlanırsa, varsayılan olarak [`Float64`](@ref) olarak ayarlanır.

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

Bu fonksiyonlara boyutları geçmenin çeşitli yollarını görmek için aşağıdaki örneklere bakın:

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

Burada, `(2, 3)` bir [`Tuple`](@ref) ve ilk argüman — eleman türü — isteğe bağlıdır, varsayılan olarak `Float64`'tür.

## [Array literals](@id man-array-literals)

Diziler, kare parantezlerle doğrudan da oluşturulabilir; `[A, B, C, ...]` sözdizimi, virgülle ayrılmış argümanları elemanları olarak içeren bir boyutlu dizi (yani bir vektör) oluşturur. Sonuçta oluşan dizinin eleman tipi ([`eltype`](@ref)) parantez içindeki argümanların türlerine göre otomatik olarak belirlenir. Tüm argümanlar aynı türdeyse, o zaman bu dizinin `eltype`'ıdır. Eğer hepsi ortak bir [promotion type](@ref conversion-and-promotion) türüne sahipse, o zaman [`convert`](@ref) kullanılarak o türe dönüştürülür ve bu tür dizinin `eltype`'ıdır. Aksi takdirde, herhangi bir şeyi tutabilen bir heterojen dizi — `Vector{Any}` — oluşturulur; bu, hiçbir argüman verilmediğinde literal `[]`'yi de içerir. [Array literal can be typed](@ref man-array-typed-literal) sözdizimi ile `T[A, B, C, ...]` şeklindedir; burada `T` bir türdür.

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

Eğer köşeli parantezler içindeki argümanlar virgül yerine tek noktalı virgül (`;`) veya yeni satırlarla ayrılmışsa, o zaman içerikleri *dikey olarak birleştirilir* ve argümanlar kendileri eleman olarak kullanılmaz.

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

Benzer şekilde, eğer argümanlar sekmelerle, boşluklarla veya çift noktalı virgüllerle ayrılmışsa, o zaman içerikleri *yatay olarak birleştirilir*.

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

Tek bir noktalı virgül (veya yeni satır) ve boşluk (veya sekme) hem yatay hem de dikey olarak birleştirilerek birleştirilebilir.

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

Boşluklar (ve sekmeler) noktalı virgüllerden daha yüksek bir önceliğe sahiptir, önce herhangi bir yatay birleştirme gerçekleştirir ve ardından sonucu birleştirir. Öte yandan, yatay birleştirme için çift noktalı virgül kullanmak, önce dikey birleştirmeleri gerçekleştirir ve ardından sonucu yatay olarak birleştirir.

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

Tam `;` ve `;;` birinci ve ikinci boyutta birleştirirken, daha fazla noktalı virgül kullanmak bu genel şemayı genişletir. Ayırıcıdaki noktalı virgül sayısı belirli boyutu belirtir, bu nedenle `;;;` üçüncü boyutta birleştirir, `;;;;` dördüncü boyutta ve devam eder. Daha az noktalı virgül önceliğe sahiptir, bu nedenle daha düşük boyutlar genellikle önce birleştirilir.

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

Daha önce olduğu gibi, yatay birleştirme için boşluklar (ve sekmeler) herhangi bir sayıda noktalı virgülden daha yüksek önceliğe sahiptir. Bu nedenle, daha yüksek boyutlu diziler de satırlarını ilk olarak belirterek yazılabilir; elemanları, düzenlerine benzer bir şekilde metin olarak düzenlenmiştir:

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

İkinci boyutta birleştirme anlamına gelse de, boşluklar (veya sekmeler) ve `;;` aynı dizi ifadesinde bir arada bulunamaz, aksi takdirde çift noktalı virgül sadece "satır devamı" karakteri olarak işlev görüyor olabilir. Bu, tek bir yatay birleştirmenin birden fazla satıra yayılmasına olanak tanır (satır sonunun dikey bir birleştirme olarak yorumlanmadan).

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Sonlandırıcı noktalı virgüller, ayrıca sonlandırıcı uzunluk 1 boyutları eklemek için de kullanılabilir.

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

Daha genel olarak, birleştirme [`cat`](@ref) fonksiyonu aracılığıyla gerçekleştirilebilir. Bu sözdizimleri, kendileri de kolaylık sağlayan fonksiyon çağrıları için kısayollardır:

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

Belirli bir eleman türüne sahip bir dizi, `T[A, B, C, ...]` sözdizimi kullanılarak oluşturulabilir. Bu, `T` eleman türüne sahip, `A`, `B`, `C` vb. elemanları içerecek şekilde başlatılmış 1 boyutlu bir dizi oluşturur. Örneğin, `Any[x, y, z]` herhangi bir değeri içerebilen heterojen bir dizi oluşturur.

Birleştirme sözdizimi, sonuçtaki öğe türünü belirtmek için benzer şekilde bir tür ile ön eklenebilir.

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

Kapsamlar, dizileri oluşturmanın genel ve güçlü bir yolunu sağlar. Kapsam sözdizimi, matematikteki küme oluşturma notasyonuna benzer:

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

Bu formun anlamı, `F(x,y,...)` ifadesinin `x`, `y` vb. değişkenlerinin kendilerine verilen değerler listesindeki her bir değeri alarak değerlendirildiğidir. Değerler herhangi bir yinelemeli nesne olarak belirtilebilir, ancak genellikle `1:n` veya `2:(n-1)` gibi aralıklar ya da `[1.2, 3.4, 5.7]` gibi açık değer dizileri şeklinde olur. Sonuç, değişken aralıklarının `rx`, `ry` vb. boyutlarının birleştirilmesiyle oluşan boyutlara sahip N-d yoğun bir dizi olup, her `F(x,y,...)` değerlendirmesi bir skalar değer döndürür.

Aşağıdaki örnek, 1 boyutlu bir ızgara boyunca mevcut elemanın ve sol ve sağ komşusunun ağırlıklı ortalamasını hesaplar. :

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

Sonuç dizisi türü, hesaplanan öğelerin türlerine bağlıdır, tıpkı [array literals](@ref man-array-literals) gibi. Türü açıkça kontrol etmek için, bir tür anlayışın önüne eklenebilir. Örneğin, sonucu tek hassasiyetle istemiş olabilirdik, şöyle yazarak:

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

Kapsamlar, dıştaki köşeli parantezler olmadan da yazılabilir ve bu, bir jeneratör olarak bilinen bir nesne üretir. Bu nesne, değerleri talep üzerine üretmek için yinelemeli olarak kullanılabilir; bu, bir dizi ayırmak ve bunları önceden depolamak yerine (bkz. [Iteration](@ref)). Örneğin, aşağıdaki ifade bir dizi toplamını bellek ayırmadan hesaplar:

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

Bir argüman listesinde birden fazla boyutlu bir jeneratör ifadesi yazarken, jeneratörü sonraki argümanlardan ayırmak için parantezler gereklidir:

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

Tüm virgülle ayrılmış ifadeler `for` ifadesinden sonra aralıklar olarak yorumlanır. Parantez eklemek, [`map`](@ref) için üçüncü bir argüman eklememizi sağlar:

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

Jeneratörler iç fonksiyonlar aracılığıyla uygulanır. Dilin başka yerlerinde kullanılan iç fonksiyonlar gibi, kapsayıcı kapsamdan değişkenler iç fonksiyonda "yakalanabilir". Örneğin, `sum(p[i] - q[i] for i=1:n)` kapsayıcı kapsamdan `p`, `q` ve `n` değişkenlerini yakalar. Yakalanan değişkenler performans zorlukları yaratabilir; bkz. [performance tips](@ref man-performance-captured).

Üreticiler ve anlama ifadelerindeki aralıklar, birden fazla `for` anahtar kelimesi yazarak önceki aralıklara bağlı olabilir:

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

Bu tür durumlarda, sonuç her zaman 1-d'dir.

Üretilen değerler `if` anahtar kelimesi kullanılarak filtrelenebilir:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

n boyutlu bir dizi `A` içine indeksleme için genel sözdizimi:

```
X = A[I_1, I_2, ..., I_n]
```

her `I_k` bir skalar tam sayı, bir tam sayı dizisi veya başka bir [supported index](@ref man-supported-index-types) olabilir. Bu, tüm boyut içindeki tüm indeksleri seçmek için [`Colon`](@ref) (`:`), bitişik veya adımlı alt bölümleri seçmek için `a:c` veya `a:b:c` biçimindeki aralıkları ve `true` indekslerinde elemanları seçmek için boolean dizilerini içerir.

Eğer tüm indeksler skalar ise, o zaman sonuç `X`, dizi `A`'dan tek bir elemandır. Aksi takdirde, `X`, tüm indekslerin boyutlarının toplamı kadar boyuta sahip bir dizi olur.

Eğer tüm indeksler `I_k` vektörler ise, o zaman `X`'in şekli `(length(I_1), length(I_2), ..., length(I_n))` olacaktır; `X`'in `i_1, i_2, ..., i_n` konumunda `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]` değeri bulunacaktır.

Örnek:

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

Sonuç dizisinin boyutunun son iki durumda nasıl farklı olduğunu not edin.

Eğer `I_1` iki boyutlu bir matris haline getirilirse, o zaman `X`, `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))` şekline sahip `n+1` boyutlu bir dizi haline gelir. Matris bir boyut ekler.

Örnek:

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

Konum `i_1, i_2, i_3, ..., i_{n+1}` değeri `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]` içerir. Skalarlarla indekslenmiş tüm boyutlar atılır. Örneğin, `J` bir indeksler dizisi ise, o zaman `A[2, J, 3]` sonucu `size(J)` boyutunda bir dizi olur. `j`'nci elemanı `A[2, J[j], 3]` ile doldurulur.

Bu sözdiziminin özel bir parçası olarak, `end` anahtar kelimesi, dizinleme parantezleri içindeki her boyutun son indeksini temsil etmek için kullanılabilir; bu, dizinlenen en içteki dizinin boyutuna bağlıdır. `end` anahtar kelimesi olmadan dizinleme sözdizimi, [`getindex`](@ref) çağrısına eşdeğerdir:

```
X = getindex(A, I_1, I_2, ..., I_n)
```

Örnek:

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

n boyutlu bir dizi `A`'da değer atamanın genel sözdizimi:

```
A[I_1, I_2, ..., I_n] = X
```

her `I_k` bir skalar tam sayı, bir tam sayı dizisi veya başka bir [supported index](@ref man-supported-index-types) olabilir. Bu, tüm boyut içindeki tüm indeksleri seçmek için [`Colon`](@ref) (`:`), bitişik veya adımlı alt bölümleri seçmek için `a:c` veya `a:b:c` biçimindeki aralıkları ve `true` indekslerinde elemanları seçmek için boolean dizilerini içerir.

Eğer tüm indeksler `I_k` tam sayılarsa, o zaman `A`'nın `I_1, I_2, ..., I_n` konumundaki değer `X` ile, gerekirse `A`'nın [`convert`](@ref)'sına [`eltype`](@ref)'na yazılır.

Eğer herhangi bir indeks `I_k` kendisi bir dizi ise, o zaman sağdaki `X` da `A[I_1, I_2, ..., I_n]` indekslemenin sonucuyla aynı şekle sahip bir dizi veya aynı sayıda elemana sahip bir vektör olmalıdır. `A`'nın `I_1[i_1], I_2[i_2], ..., I_n[i_n]` konumundaki değer, gerekirse dönüştürülerek `X[i_1, i_2, ..., i_n]` ile üzerine yazılır. Eleman bazında atama operatörü `.=` seçilen konumlar üzerinde `X`'i [broadcast](@ref Broadcasting) kullanarak uygulamak için kullanılabilir:

```
A[I_1, I_2, ..., I_n] .= X
```

Tıpkı [Indexing](@ref man-array-indexing) içinde olduğu gibi, `end` anahtar kelimesi, atanan dizinin boyutuna bağlı olarak, indeksleme parantezleri içindeki her boyutun son indeksini temsil etmek için kullanılabilir. `end` anahtar kelimesi olmadan indeksli atama sözdizimi, [`setindex!`](@ref) çağrısına eşdeğerdir:

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

Örnek:

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

`A[I_1, I_2, ..., I_n]` ifadesinde, her `I_k` bir skalar indeks, skalar indekslerin bir dizisi veya skalar indekslerin bir dizisini temsil eden ve [`to_indices`](@ref) ile dönüştürülebilen bir nesne olabilir:

1. Bir skalar indeks. Varsayılan olarak bu şunları içerir:

      * Boolean olmayan tam sayılar
      * [`CartesianIndex{N}`](@ref) gibi, aşağıdaki gibi daha fazla ayrıntı için (birden fazla boyutta uzanan `N`-demet tamsayıları gibi davranan)
2. Bir dizi skalar indeks. Bu şunları içerir:

      * Tam sayılardan oluşan vektörler ve çok boyutlu diziler
      * Boş diziler gibi `[]`, hiçbir öğe seçmeyen örneğin `A[[]]` (A[] ile karıştırılmamalıdır)
      * `a:c` veya `a:b:c` gibi aralıklar, `a` ile `c` (dahil) arasında bitişik veya adımlı alt bölümleri seçer.
      * Herhangi bir `AbstractArray` alt türü olan özel bir skalar indeks dizisi
      * `CartesianIndex{N}` dizileri (aşağıda daha fazla ayrıntı için bakınız)
3. Bir dizi skalar indeksini temsil eden ve [`to_indices`](@ref) ile böyle bir diziye dönüştürülebilen bir nesne. Varsayılan olarak bu şunları içerir:

      * [`Colon()`](@ref) (`:`), tüm bir boyuttaki veya tüm dizi üzerindeki tüm indeksleri temsil eder.
      * Boolean dizileri, `true` indekslerinde elemanları seçer (aşağıda daha fazla ayrıntı için bakınız)

Bazı örnekler:

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

Özel `CartesianIndex{N}` nesnesi, birden fazla boyutu kapsayan bir `N`-demet tam sayısı gibi davranan bir skalar indeksi temsil eder. Örneğin:

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

Tek başına düşünüldüğünde, bu nispeten önemsiz görünebilir; `CartesianIndex`, birden fazla tam sayıyı bir araya getirerek tek bir çok boyutlu indeksi temsil eden bir nesne oluşturur. Ancak, diğer indeksleme biçimleri ve `CartesianIndex` üreten iteratörlerle birleştirildiğinde, bu çok şık ve verimli kodlar üretebilir. Aşağıdaki [Iteration](@ref) ve daha ileri örnekler için [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration) adresine bakın.

`CartesianIndex{N}` dizileri de desteklenmektedir. Bunlar, her biri `N` boyutunu kapsayan bir dizi skalar indeksi temsil eder ve bazen noktasal indeksleme olarak adlandırılan bir indeksleme biçimini mümkün kılar. Örneğin, yukarıdan `A`'nın ilk "sayfasından" köşegen elemanlarına erişimi sağlar:

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

Bu, [dot broadcasting](@ref man-vectorized) ile çok daha basit bir şekilde ifade edilebilir ve bunu normal bir tam sayı indeksi ile birleştirerek (A'dan ilk `page`'i ayrı bir adım olarak çıkarmak yerine) yapılabilir. Aynı zamanda, iki sayfanın her ikisinden de aynı anda iki diyagonal çıkarmak için `:` ile birleştirilebilir:

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
    `CartesianIndex` ve `CartesianIndex` dizileri, bir boyutun son indeksini temsil etmek için `end` anahtar kelimesi ile uyumlu değildir. `CartesianIndex` veya bunların dizilerini içerebilecek indeksleme ifadelerinde `end` kullanmayın.


### Logical indexing

Sıklıkla mantıksal indeksleme veya mantıksal maske ile indeksleme olarak adlandırılan, bir boolean dizisi ile indeksleme, değerlerinin `true` olduğu indekslerdeki öğeleri seçer. Bir boolean vektörü `B` ile indeksleme, etkili bir şekilde [`findall(B)`](@ref) tarafından döndürülen tamsayı vektörü ile indekslemeye eşdeğerdir. Benzer şekilde, `N`-boyutlu bir boolean dizisi ile indeksleme, değerlerinin `true` olduğu `CartesianIndex{N}` vektörü ile indekslemeye etkili bir şekilde eşdeğerdir. Mantıksal bir indeks, indekslediği boyut(lar) ile aynı şekle sahip bir dizi olmalı veya sağlanan tek indeks olmalı ve indekslediği dizinin bir boyutlu yeniden şekillendirilmiş görünümünün şekliyle eşleşmelidir. Boolean dizilerini doğrudan indeks olarak kullanmak, öncelikle [`findall`](@ref) çağırmaktan genellikle daha verimlidir.

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

`N` boyutlu bir diziye indeksleme yapmanın sıradan yolu, tam olarak `N` indeks kullanmaktır; her indeks, belirli bir boyuttaki konum(lar)ı seçer. Örneğin, üç boyutlu dizi `A = rand(4, 3, 2)` içinde, `A[2, 3, 1]` dizinin ilk "sayfasındaki" üçüncü sütunun ikinci satırındaki sayıyı seçecektir. Bu genellikle *kartezian indeksleme* olarak adlandırılır.

#### Linear indexing

Tam olarak bir `i` indeksi verildiğinde, bu indeks artık dizinin belirli bir boyutundaki bir konumu temsil etmez. Bunun yerine, tüm diziyi doğrusal olarak kapsayan sütun-öncelikli yineleme sırasını kullanarak `i`'nci öğeyi seçer. Bu, *doğrusal indeksleme* olarak bilinir. Temelde, diziyi [`vec`](@ref) ile yeniden şekillendirilmiş gibi bir boyutlu bir vektör olarak ele alır.

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

Bir dizi `A` içindeki lineer bir indeks, `CartesianIndices(A)[i]` ile kartezyen indeksleme için bir `CartesianIndex`'e dönüştürülebilir (bkz. [`CartesianIndices`](@ref)), ve bir dizi `N` kartezyen indeksi, `LinearIndices(A)[i_1, i_2, ..., i_N]` ile bir lineer indekse dönüştürülebilir (bkz. [`LinearIndices`](@ref)).

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

Dönüşümlerin performansında çok büyük bir asimetri olduğunu belirtmek önemlidir. Bir lineer indeksi bir dizi kartezyen indekse dönüştürmek, bölme ve kalanı alma gerektirirken, diğer yönde gitmek sadece çarpma ve toplama gerektirir. Modern işlemcilerde, tam sayı bölme, çarpmadan 10-50 kat daha yavaş olabilir. Bazı diziler — örneğin [`Array`](@ref) — lineer bir bellek parçası kullanılarak uygulanmış ve uygulamalarında doğrudan bir lineer indeks kullanırken, diğer diziler — örneğin [`Diagonal`](@ref) — arama yapmak için tam bir dizi kartezyen indekse ihtiyaç duyar (hangisinin hangisi olduğunu incelemek için [`IndexStyle`](@ref)'ya bakın).

!!! warning
    Dizi için tüm indeksler üzerinde dönerken, [`eachindex(A)`](@ref) üzerinde döngü yapmak, `1:length(A)` üzerinde döngü yapmaktan daha iyidir. Bu, `A` 'nın `IndexCartesian` olduğu durumlarda daha hızlı olacaktır, ayrıca [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl) gibi özel indeksleme ile dizileri de destekleyecektir. Eğer sadece değerlere ihtiyaç varsa, o zaman diziyi doğrudan döngü ile geçmek daha iyidir, yani `for a in A`.


#### Omitted and extra indices

Bunun yanı sıra, `N` boyutlu bir dizi, belirli durumlarda `N`'den daha az veya daha fazla indeks ile indekslenebilir.

İndeksler, yalnızca indekslenmeyen son boyutların hepsi bir uzunluğunda olduğunda atlanabilir. Diğer bir deyişle, son indeksler yalnızca, atlanan indekslerin bir in-bounds indeksleme ifadesi için alabileceği yalnızca bir olası değer olduğunda atlanabilir. Örneğin, boyutu `(3, 4, 2, 1)` olan dört boyutlu bir dizi, atlanan boyut (dördüncü boyut) bir uzunluğunda olduğu için yalnızca üç indeks ile indekslenebilir. Doğrusal indekslemenin bu kuraldan önceliği olduğunu unutmayın.

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

`A[]` kullanarak *tüm* indeksleri atladığınızda, bu anlam, bir dizideki tek bir öğeyi almak ve aynı zamanda yalnızca bir öğe olduğundan emin olmak için basit bir deyim sağlar.

Benzer şekilde, `N`'den fazla indeks sağlanabilir eğer dizinin boyutunun ötesindeki tüm indeksler `1` (veya daha genel olarak `d` o belirli boyut numarası olan `axes(A, d)`'nin ilk ve tek elemanı) ise. Bu, vektörlerin tek sütunlu matrisler gibi indekslenmesine olanak tanır, örneğin:

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

Dizinin tamamı üzerinde yineleme yapmanın önerilen yolları şunlardır:

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

İlk yapı, her bir elemanın değerine, ancak indeksine ihtiyaç duyduğunuzda kullanılır. İkinci yapıda, `i` bir `Int` olacaktır eğer `A` hızlı lineer indeksleme ile bir dizi türüyse; aksi takdirde, bir `CartesianIndex` olacaktır:

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
    `for i = 1:length(A)` ile karşılaştırıldığında, [`eachindex`](@ref) kullanarak yineleme, herhangi bir dizi türü üzerinde verimli bir şekilde yineleme yapmanın bir yolunu sunar. Ayrıca, bu, [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl) gibi özel indeksleme ile genel dizileri de destekler.


## Array traits

Eğer özel bir [`AbstractArray`](@ref) türü yazarsanız, hızlı doğrusal dizinleme özelliğine sahip olduğunu belirtebilirsiniz.

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Bu ayar, `MyArray` üzerinde `eachindex` yinelemesinin tam sayılar kullanmasını sağlayacaktır. Bu özelliği belirtmezseniz, varsayılan değer `IndexCartesian()` kullanılır.

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

Aşağıdaki operatörler diziler için desteklenmektedir:

1. Unary aritmetik – `-`, `+`
2. İkili aritmetik – `-`, `+`, `*`, `/`, `\`, `^`
3. Karşılaştırma – `==`, `!=`, `≈` ([`isapprox`](@ref)), `≉`

Matematiksel ve diğer işlemlerin uygun vektörleştirilmesini sağlamak için Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)` kullanır; örneğin `sin.(x)` veya `min.(x, y)`, diziler veya diziler ve skalarların karışımları üzerinde eleman bazında işlemler için (bir [Broadcasting](@ref) işlemi); bunlar, diğer nokta çağrılarıyla birleştirildiğinde tek bir döngüye "birleşme" avantajına da sahiptir, örneğin `sin.(cos.(x))`.

Also, *every* binary operator supports a [dot version](@ref man-dot-operators) that can be applied to arrays (and combinations of arrays and scalars) in such [fused broadcasting operations](@ref man-vectorized), e.g. `z .== sin.(x .* y)`.

Dikkat edin ki `==` gibi karşılaştırmalar tüm diziler üzerinde çalışır ve tek bir boolean yanıt verir. Eleman bazında karşılaştırmalar için `.==` gibi nokta operatörlerini kullanın. (Karşılaştırma işlemleri için `<`, *yalnızca* eleman bazında `.<` versiyonu dizilere uygulanabilir.)

Ayrıca `max.(a,b)` ile [`broadcast`](@ref)'nın [`max`](@ref)'yi `a` ve `b` üzerinde eleman bazında karşılaştırdığını, [`maximum(a)`](@ref)'nın ise `a` içindeki en büyük değeri bulduğunu unutmayın. Aynı ilişki `min.(a, b)` ve `minimum(a)` için de geçerlidir.

## Broadcasting

Bazen, farklı boyutlardaki diziler üzerinde eleman bazında ikili işlemler gerçekleştirmek faydalı olabilir; örneğin, bir vektörü bir matrisin her sütununa eklemek. Bunu yapmanın verimsiz bir yolu, vektörü matrisin boyutuna kopyalamaktır:

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

Bu, boyutlar büyük olduğunda israf yaratır, bu nedenle Julia, [`broadcast`](@ref) sağlar; bu, dizi argümanlarındaki tekil boyutları diğer dizideki karşılık gelen boyutla eşleştirmek için genişletir ve ekstra bellek kullanmadan, verilen işlevi eleman bazında uygular:

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

[Dotted operators](@ref man-dot-operators) gibi `.+` ve `.*` `broadcast` çağrılarıyla eşdeğerdir (fakat birleştirme yaparlar, çünkü [described above](@ref man-array-and-vectorized-operators-and-functions)). Ayrıca, belirli bir hedefi belirtmek için [`broadcast!`](@ref) fonksiyonu da vardır (bu, `.=` ataması ile birleştirilmiş bir şekilde de erişilebilir). Aslında, `f.(args...)` `broadcast(f, args...)` ile eşdeğerdir ve herhangi bir fonksiyonu yaymak için kullanışlı bir sözdizimi sağlar ([dot syntax](@ref man-vectorized)). İç içe "nokta çağrıları" `f.(...)` (örneğin `.+` gibi çağrılar dahil) [automatically fuse](@ref man-dot-operators) tek bir `broadcast` çağrısına dönüştürülür.

Ayrıca, [`broadcast`](@ref) dizilerle sınırlı değildir (fonksiyon belgelerine bakın); aynı zamanda skalarlar, demetler ve diğer koleksiyonları da işler. Varsayılan olarak, yalnızca bazı argüman türleri skalar olarak kabul edilir, bunlar arasında (ancak bunlarla sınırlı olmamak üzere) `Number`, `String`, `Symbol`, `Type`, `Function` ve `missing` ile `nothing` gibi bazı yaygın tekil nesneler bulunur. Diğer tüm argümanlar eleman bazında yineleme veya indeksleme ile işlenir.

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

Bazen, bir dizinin gibi bir konteynerin, genellikle yayılma işlemine katılmasını istemezsiniz ve bu nedenle tüm elemanları üzerinde yineleme yapma davranışından "korunmuş" olmasını istersiniz. Bunu, başka bir konteynerin içine yerleştirerek (örneğin, tek bir eleman [`Tuple`](@ref)) yayılma işlemi onu tek bir değer olarak değerlendirecektir.

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

Julia'daki temel dizi türü, soyut tür [`AbstractArray{T,N}`](@ref)'dır. Bu, boyut sayısı `N` ve eleman türü `T` ile parametreleştirilmiştir. [`AbstractVector`](@ref) ve [`AbstractMatrix`](@ref) 1-d ve 2-d durumları için takma adlardır. `AbstractArray` nesneleri üzerindeki işlemler, temel depolamadan bağımsız bir şekilde, daha yüksek seviyeli operatörler ve fonksiyonlar kullanılarak tanımlanmıştır. Bu işlemler, belirli bir dizi uygulaması için bir geri dönüş olarak genellikle doğru bir şekilde çalışır.

`AbstractArray` türü, herhangi bir şekilde dizi benzeri olan her şeyi içerir ve bunun uygulamaları geleneksel dizilerden oldukça farklı olabilir. Örneğin, elemanlar depolanmak yerine talep üzerine hesaplanabilir. Ancak, herhangi bir somut `AbstractArray{T,N}` türü genellikle en az [`size(A)`](@ref) (bir `Int` demetini döndürür), [`getindex(A, i)`](@ref) ve [`getindex(A, i1, ..., iN)`](@ref getindex) uygulamalıdır; değiştirilebilir diziler ayrıca [`setindex!`](@ref) uygulamalıdır. Bu işlemlerin neredeyse sabit zaman karmaşıklığına sahip olması önerilir, aksi takdirde bazı dizi işlevleri beklenmedik şekilde yavaş olabilir. Somut türler ayrıca genellikle [`similar(A, T=eltype(A), dims=size(A))`](@ref) yöntemini sağlamalıdır; bu, [`copy`](@ref) ve diğer yer dışı işlemler için benzer bir dizi tahsis etmek için kullanılır. Bir `AbstractArray{T,N}` içsel olarak nasıl temsil edilirse edilsin, `T`, *tam sayı* indeksleme ile döndürülen nesne türüdür (`A[1, ..., 1]`, `A` boş değilse) ve `N`, [`size`](@ref) tarafından döndürülen demetin uzunluğu olmalıdır. Özel `AbstractArray` uygulamalarını tanımlama hakkında daha fazla bilgi için [array interface guide in the interfaces chapter](@ref man-interface-array) kısmına bakın.

`DenseArray`, `AbstractArray`'ın, elemanların sütun-anahtar sırasına göre sürekli olarak depolandığı tüm dizileri içermek üzere tasarlanmış soyut bir alt türüdür (bkz. [additional notes in Performance Tips](@ref man-performance-column-major)). [`Array`](@ref) türü, `DenseArray`'nın belirli bir örneğidir; [`Vector`](@ref) ve [`Matrix`](@ref) 1-d ve 2-d durumları için takma adlardır. `Array` için, tüm `AbstractArray`'lar için gerekli olanlar dışında çok az işlem özel olarak uygulanmıştır; dizi kütüphanesinin çoğu, tüm özel dizilerin benzer şekilde davranmasına olanak tanıyan genel bir şekilde uygulanmıştır.

`SubArray`, `AbstractArray`'ın bellek paylaşımı ile dizinleme yapan bir özel versiyonudur; bu, dizinin kopyalanması yerine orijinal dizi ile bellek paylaşarak gerçekleştirilir. `SubArray`, [`view`](@ref) fonksiyonu ile oluşturulur; bu fonksiyon, bir dizi ve bir dizi indeks argümanı ile aynı şekilde çağrılır. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566`'nın sonucu, [`getindex`](@ref)'nın sonucu ile aynı görünür, tek farkla verilerin yerinde bırakılmasıdır. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566`, giriş indeks vektörlerini bir `SubArray` nesnesinde saklar; bu nesne daha sonra orijinal diziyi dolaylı olarak dizinlemek için kullanılabilir. Bir ifadenin veya kod bloğunun önüne [`@views`](@ref) makrosunu koyarak, o ifadede bulunan herhangi bir `array[...]` dilimi, bir `SubArray` görünümü oluşturacak şekilde dönüştürülür.

[`BitArray`](@ref) alanında, her boolean değeri için bir bit depolayan, alan açısından verimli "paketlenmiş" boolean dizileri bulunmaktadır. Bunlar, her boolean değeri için bir byte depolayan `Array{Bool}` dizileri ile benzer şekilde kullanılabilir ve `Array(bitarray)` ve `BitArray(array)` aracılığıyla birbirine dönüştürülebilir.

Bir dizi "stride" olarak adlandırılırsa, bellekte elemanları arasında iyi tanımlanmış boşluklarla (stride'lar) saklanır. Desteklenen bir eleman türüne sahip bir stride dizisi, [`pointer`](@ref) ve her boyut için stride'ı geçerek BLAS veya LAPACK gibi bir dış (Julia dışı) kütüphaneye aktarılabilir. [`stride(A, d)`](@ref) ise `d` boyutu boyunca elemanlar arasındaki mesafedir. Örneğin, `rand(5,7,2)` ile döndürülen yerleşik `Array`, elemanlarını sütun ana sırasına göre ardışık olarak düzenler. Bu, ilk boyutun stride'ının — aynı sütundaki elemanlar arasındaki boşluğun — `1` olduğu anlamına gelir:

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

İkinci boyutun adımı, aynı satırdaki elemanlar arasındaki boşluktur ve bir sütundaki eleman sayısı kadar (`5`) atlanır. Benzer şekilde, iki "sayfa" arasında (üçüncü boyutta) atlamak `5*7 == 35` eleman atlamayı gerektirir. Bu dizinin [`strides`](@ref) değeri, bu üç sayının bir arada bulunduğu demettir:

```julia-repl
julia> strides(A)
(1, 5, 35)
```

Bu özel durumda, *bellekte* atlanan eleman sayısı, atlanan *doğrusal indeksler* sayısıyla eşleşmektedir. Bu, yalnızca `Array` (ve diğer `DenseArray` alt türleri) gibi bitişik diziler için geçerlidir ve genel olarak doğru değildir. Aralık indekslerine sahip görünümler, *bitişiksiz* adımlı dizilerin iyi bir örneğidir; `V = @view A[1:3:4, 2:2:6, 2:-1:1]` ifadesini düşünün. Bu `V` görünümü, `A` ile aynı belleği referans alır ancak bazı elemanlarını atlamakta ve yeniden düzenlemektedir. `V`'nin birinci boyutunun adımı `3`'tür çünkü orijinal dizimizden yalnızca her üçüncü satırı seçiyoruz:

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

Bu görünüm, orijinal `A`'mızdan her diğer sütunu benzer şekilde seçiyor - bu nedenle, ikinci boyuttaki indeksler arasında hareket ederken iki beş elemanlı sütunu atlaması gerekiyor:

```julia-repl
julia> stride(V, 2)
10
```

Üçüncü boyut ilginçtir çünkü sırası tersine dönmüştür! Bu nedenle birinci "sayfadan" ikinci "sayfaya" geçmek için bellekte *geriye* gitmesi gerekir ve bu nedenle bu boyuttaki adımı negatiftir!

```julia-repl
julia> stride(V, 3)
-35
```

Bu, `V` için `pointer`'ın aslında `A`'nın bellek bloğunun ortasına işaret ettiğini ve bellek içinde hem geriye hem de ileriye doğru elemanlara atıfta bulunduğunu gösterir. Kendi adım dizilerinizi tanımlamak için daha fazla ayrıntı için [interface guide for strided arrays](@ref man-interface-strided-arrays)'e bakın. [`StridedVector`](@ref) ve [`StridedMatrix`](@ref), adım dizileri olarak kabul edilen birçok yerleşik dizi türü için kullanışlı takma adlardır ve bunların, yalnızca işaretçi ve adımlar kullanarak yüksek derecede ayarlanmış ve optimize edilmiş BLAS ve LAPACK fonksiyonlarını çağıran özel uygulamalara yönlendirilmesine olanak tanır.

Belleklemek gerekir ki, adımlar bellek içindeki kaydırmalarla ilgilidir, indeksleme ile değil. Eğer lineer (tek indeks) indeksleme ile kartezyen (çoklu indeks) indeksleme arasında dönüşüm yapmak istiyorsanız, [`LinearIndices`](@ref) ve [`CartesianIndices`](@ref)'ya bakın.

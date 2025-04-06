# Interfaces

Julia'daki güç ve genişletilebilirliğin çoğu, bir dizi gayri resmi arayüzden gelmektedir. Belirli birkaç yöntemi özel bir tür için çalışacak şekilde genişleterek, o türün nesneleri yalnızca bu işlevsellikleri almakla kalmaz, aynı zamanda bu davranışlara genel olarak dayanan diğer yöntemlerde de kullanılabilir hale gelirler.

## [Iteration](@id man-interface-iteration)

Her zaman gerekli olan iki yöntem vardır:

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

Bazı durumlarda tanımlanması gereken birkaç yöntem daha vardır. Lütfen her zaman `Base.IteratorSize(IterType)` ve `length(iter)`'den en az birini tanımlamanız gerektiğini unutmayın, çünkü `Base.IteratorSize(IterType)`'nin varsayılan tanımı `Base.HasLength()`'dir.

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

Sıralı yineleme, [`iterate`](@ref) fonksiyonu ile uygulanır. Julia yineleyicileri, yineleme sırasında nesneleri değiştirmek yerine, yineleme durumunu nesneden bağımsız olarak takip edebilir. `iterate` fonksiyonunun döndürdüğü değer her zaman bir değer ve bir durumdan oluşan bir demet ya da hiçbir eleman kalmadığında `nothing` olur. Durum nesnesi, bir sonraki yinelemede `iterate` fonksiyonuna geri gönderilecek ve genellikle yineleyici nesneye özel bir uygulama detayı olarak kabul edilir.

Herhangi bir nesne bu işlevi tanımlıyorsa, yine de [many functions that rely upon iteration](@ref lib-collections-iteration) içinde kullanılabilir ve yine de [`for`](@ref) döngüsünde doğrudan kullanılabilir, çünkü sözdizimi:

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

lütfen çevrilecek metni paylaşın.

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

Kısa bir örnek, belirli bir uzunluğa sahip kare sayıların yinelemeli bir dizisidir:

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

Sadece [`iterate`](@ref) tanımı ile `Squares` tipi zaten oldukça güçlü. Tüm öğeler üzerinde yineleyebiliriz:

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

Birçok iterable ile çalışan yerleşik yöntemleri kullanabiliriz, örneğin [`in`](@ref) veya [`sum`](@ref):

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

Julia'nın bu iterable koleksiyonu hakkında daha fazla bilgi vermek için uzatabileceğimiz birkaç yöntem var. `Squares` dizisindeki elemanların her zaman `Int` olacağını biliyoruz. [`eltype`](@ref) yöntemini uzatarak, bu bilgiyi Julia'ya verebilir ve daha karmaşık yöntemlerde daha özel kodlar oluşturmasına yardımcı olabiliriz. Ayrıca dizimizdeki eleman sayısını da biliyoruz, bu yüzden [`length`](@ref) yöntemini de uzatabiliriz:

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

Şimdi, Julia'dan [`collect`](@ref) tüm elemanları bir diziye koymasını istediğimizde, her bir elemanı naif bir şekilde [`push!`](@ref) bir `Vector{Any}`'ye eklemek yerine doğru boyutta bir `Vector{Int}` önceden ayırabilir:

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

Genel uygulamalara güvenebileceğimiz gibi, daha basit bir algoritmanın bulunduğu yerlerde belirli yöntemleri de genişletebiliriz. Örneğin, karelerin toplamını hesaplamak için bir formül vardır, bu nedenle genel yinelemeli versiyonu daha performanslı bir çözümle geçersiz kılabiliriz:

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

Bu, Julia Base'de yaygın bir modeldir: bir dizi gerekli yöntem, birçok daha şık davranışı mümkün kılan gayri resmi bir arayüz tanımlar. Bazı durumlarda, türler, belirli bir durumda daha verimli bir algoritmanın kullanılabileceğini bildiklerinde, bu ek davranışları ayrıca özelleştirmek isteyebilirler.

Ayrıca, bir koleksiyon üzerinde *ters sırayla* yineleme yapmayı sağlamak da sıklıkla faydalıdır; bu, [`Iterators.reverse(iterator)`](@ref) üzerinde yineleme yaparak gerçekleştirilir. Ancak, ters sırayla yinelemeyi gerçekten desteklemek için, bir `T` türü iteratörünün `Iterators.Reverse{T}` için `iterate` yöntemini uygulaması gerekir. (Verilen `r::Iterators.Reverse{T}` için, `T` türündeki alt iteratör `r.itr`'dir.) `Squares` örneğimizde, `Iterators.Reverse{Squares}` yöntemlerini uygulayacağız:

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

`Squares` iterable'ı için, dizinin `i`'nci elemanını kare alarak kolayca hesaplayabiliriz. Bunu `S[i]` şeklinde bir indeksleme ifadesi olarak açığa çıkarabiliriz. Bu davranışı etkinleştirmek için, `Squares` sadece [`getindex`](@ref) tanımlamalıdır:

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

Ayrıca, `S[begin]` ve `S[end]` sözdizimini desteklemek için, sırasıyla ilk ve son geçerli indeksleri belirtmek için [`firstindex`](@ref) ve [`lastindex`](@ref) tanımlamalıyız:

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

`begin`/`end` çok boyutlu indeksleme için, örneğin `a[3, begin, 7]`, `firstindex(a, dim)` ve `lastindex(a, dim)` tanımlamalısınız (bu, sırasıyla `axes(a, dim)` üzerinde `first` ve `last` çağırmayı varsayar).

Not edin, yukarıdaki *sadece* [`getindex`](@ref) bir tamsayı indeksi ile tanımlar. `Int` dışındaki herhangi bir şeyle indeksleme, eşleşen bir yöntem olmadığına dair [`MethodError`](@ref) hatası verecektir. Aralıklar veya `Int` vektörleri ile indekslemeyi desteklemek için ayrı yöntemler yazılmalıdır:

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

Bu, [indexing operations supported by some of the builtin types](@ref man-array-indexing) daha fazla desteklemeye başladıkça, hala eksik olan birçok davranış var. Bu `Squares` dizisi, ona davranışlar ekledikçe giderek daha fazla bir vektör gibi görünmeye başlıyor. Tüm bu davranışları kendimiz tanımlamak yerine, bunu resmi olarak [`AbstractArray`](@ref) alt türü olarak tanımlayabiliriz.

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

Eğer bir tür `AbstractArray`'ın alt türü olarak tanımlanmışsa, tekil eleman erişiminin üzerine inşa edilmiş çok boyutlu indeksleme ve yineleme gibi çok büyük bir zengin davranış setini miras alır. Daha fazla desteklenen yöntem için [arrays manual page](@ref man-multi-dim-arrays) ve [Julia Base section](@ref lib-arrays)'e bakın.

`AbstractArray` alt türünü tanımlamanın anahtar bir parçası [`IndexStyle`](@ref)'dır. Dizinin önemli bir parçası olan indeksleme, genellikle sıcak döngülerde gerçekleştiği için, hem indeksleme hem de indeksli atamanın mümkün olduğunca verimli olmasını sağlamak önemlidir. Dizi veri yapıları genellikle iki şekilde tanımlanır: ya elemanlarına yalnızca bir indeks kullanarak (doğrusal indeksleme) en verimli şekilde erişir ya da her boyut için belirtilen indekslerle elemanlara içsel olarak erişir. Bu iki modalite Julia tarafından `IndexLinear()` ve `IndexCartesian()` olarak tanımlanır. Doğrusal bir indeksi birden fazla indeksleme alt dizisine dönüştürmek genellikle çok pahalıdır, bu nedenle bu, tüm dizi türleri için verimli genel kodu etkinleştirmek için bir özellik tabanlı mekanizma sağlar.

Bu ayrım, türün hangi skalar indeksleme yöntemlerini tanımlaması gerektiğini belirler. `IndexLinear()` dizileri basittir: sadece `getindex(A::ArrayType, i::Int)` tanımlayın. Dizi daha sonra çok boyutlu bir indeks seti ile indekslendiğinde, yedek `getindex(A::AbstractArray, I...)` indeksleri bir lineer indekse verimli bir şekilde dönüştürür ve ardından yukarıdaki yöntemi çağırır. Öte yandan, `IndexCartesian()` dizileri, `ndims(A)` `Int` indeksleri ile desteklenen her boyut için yöntemlerin tanımlanmasını gerektirir. Örneğin, `SparseArrays` standart kütüphane modülünden [`SparseMatrixCSC`](@ref) yalnızca iki boyutu destekler, bu nedenle sadece `getindex(A::SparseMatrixCSC, i::Int, j::Int)` tanımlar. Aynı şey [`setindex!`](@ref) için de geçerlidir.

Yukarıdaki kareler dizisine dönersek, bunu `AbstractArray{Int, 1}`'in bir alt türü olarak tanımlayabiliriz:

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

Not edin ki, `AbstractArray`'ın iki parametresini belirtmek çok önemlidir; ilki [`eltype`](@ref)'yı tanımlar ve ikincisi [`ndims`](@ref)'yı tanımlar. O süpertip ve o üç yöntem, `SquaresVector`'ın yinelemeli, indekslenebilir ve tamamen işlevsel bir dizi olmasını sağlamak için yeterlidir:

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

Daha karmaşık bir örnek olarak, [`Dict`](@ref) üzerine inşa edilmiş kendi oyuncak N-boyutlu seyrek benzeri dizi türümüzü tanımlayalım:

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

Dikkat edin ki bu bir `IndexCartesian` dizisi, bu nedenle [`getindex`](@ref) ve [`setindex!`](@ref) dizinin boyutuna göre manuel olarak tanımlamamız gerekiyor. `SquaresVector`'ın aksine, `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566` tanımlayabiliyoruz ve böylece diziyi değiştirebiliyoruz:

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

`AbstractArray`'in indekslenmesi sonucu kendisi de bir dizi olabilir (örneğin, `AbstractRange` ile indekslenirken). `AbstractArray` yedekleme yöntemleri, uygun boyut ve eleman türünde bir `Array` tahsis etmek için [`similar`](@ref) kullanır ve bu, yukarıda açıklanan temel indeksleme yöntemi kullanılarak doldurulur. Ancak, bir dizi sarmalayıcı uygularken, genellikle sonucun da sarılmış olmasını istersiniz:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

Bu örnekte, uygun sarmalanmış diziyi oluşturmak için `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where T` tanımlanarak başarıya ulaşılmıştır. (`similar`'ın 1- ve 2-argümanlı formları desteklediğini, ancak çoğu durumda yalnızca 3-argümanlı formu özelleştirmeniz gerektiğini unutmayın.) Bunun çalışması için `SparseArray`'nın değiştirilebilir olması ( `setindex!`'i desteklemesi) önemlidir. `SparseArray` için `similar`, `getindex` ve `setindex!` tanımlamak, diziyi [`copy`](@ref) yapmayı da mümkün kılar.

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

Bunların yanı sıra, yukarıdaki tüm yineleyici ve indekslenebilir yöntemlere ek olarak, bu türler birbirleriyle etkileşimde bulunabilir ve Julia Base'de `AbstractArrays` için tanımlanan yöntemlerin çoğunu kullanabilir:

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

If you are defining an array type that allows non-traditional indexing (indices that start at something other than 1), you should specialize [`axes`](@ref). You should also specialize [`similar`](@ref) so that the `dims` argument (ordinarily a `Dims` size-tuple) can accept `AbstractUnitRange` objects, perhaps range-types `Ind` of your own design. For more information, see [Arrays with custom indices](@ref man-custom-indices).

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

Bir adım aralıklı dizi, girişlerinin bellekte sabit adımlarla saklandığı `AbstractArray`'ın bir alt türüdür. Dizinin eleman türü BLAS ile uyumluysa, bir adım aralıklı dizi daha verimli lineer cebir rutinleri için BLAS ve LAPACK rutinlerini kullanabilir. Kullanıcı tanımlı bir adım aralıklı dizinin tipik bir örneği, standart bir `Array`'i ek yapı ile saran bir dizidir.

Uyarı: Eğer temel depolama gerçekten adımlı değilse bu yöntemleri uygulamayın, çünkü bu yanlış sonuçlara veya segmentasyon hatalarına yol açabilir.

İşte hangi tür dizilerin adım adım olduğunu ve hangilerinin olmadığını göstermek için bazı örnekler:

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

[Broadcasting](@ref) açık bir `broadcast` veya `broadcast!` çağrısı ile tetiklenir veya `A .+ b` veya `f.(x, y)` gibi "nokta" işlemleriyle örtük olarak tetiklenir. [`axes`](@ref) ve indekslemeyi destekleyen herhangi bir nesne, yayılma işlemi için bir argüman olarak katılabilir ve varsayılan olarak sonuç bir `Array` içinde saklanır. Bu temel çerçeve üç ana şekilde genişletilebilir:

  * Tüm argümanların yayını desteklediğinden emin olmak
  * Verilen argüman seti için uygun bir çıktı dizisi seçimi
  * Verilen argüman seti için verimli bir uygulama seçimi

Tüm türler `axes` ve indekslemeyi desteklemez, ancak birçok tür yaygın olarak yayında kullanılmasına izin verir. [`Base.broadcastable`](@ref) fonksiyonu yayında her bir argüman üzerinde çağrılır ve `axes` ve indekslemeyi destekleyen farklı bir şey döndürmesine izin verir. Varsayılan olarak, bu tüm `AbstractArray` ve `Number`'lar için kimlik fonksiyonudur — zaten `axes` ve indekslemeyi desteklerler.

Eğer bir tür "0-boyutlu skalar" (tek bir nesne) gibi davranması amaçlanıyorsa, o zaman aşağıdaki yöntem tanımlanmalıdır:

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

bu, argümanı 0 boyutlu [`Ref`](@ref) konteyneri içinde döndüren bir yöntemdir. Örneğin, bu tür bir sarmalayıcı yöntem, türler, fonksiyonlar, [`missing`](@ref) ve [`nothing`](@ref) gibi özel tekil nesneler ve tarihler için tanımlanmıştır.

Özel dizi benzeri türler, şekillerini tanımlamak için `Base.broadcastable`'ı özelleştirebilir, ancak `collect(Base.broadcastable(x)) == collect(x)` kuralına uymalıdırlar. Önemli bir istisna `AbstractString`'dir; dizeler, karakterlerinin yinelemeli koleksiyonları olmalarına rağmen, yayılma amacıyla skalarlar gibi davranacak şekilde özel olarak ele alınmıştır (daha fazla bilgi için [Strings](@ref)'ya bakın).

Sonraki iki adım (çıktı dizisinin seçilmesi ve uygulanması), belirli bir argüman seti için tek bir cevabın belirlenmesine bağlıdır. Yayın, argümanlarının tüm çeşitli türlerini almalı ve bunları yalnızca bir çıktı dizisi ve bir uygulama haline getirmelidir. Yayın, bu tek cevabı "stil" olarak adlandırır. Her yayınlanabilir nesnenin kendi tercih edilen stili vardır ve bu stilleri tek bir cevapta birleştirmek için bir terfi benzeri sistem kullanılır - "hedef stil".

### Broadcast Styles

`Base.BroadcastStyle`, tüm yayın stillerinin türediği soyut bir türdür. Bir fonksiyon olarak kullanıldığında iki olası biçimi vardır: tekil (tek argümanlı) ve ikili. Tekil varyant, belirli bir yayın davranışı ve/veya çıktı türü uygulamayı amaçladığınızı ve varsayılan geri dönüş [`Broadcast.DefaultArrayStyle`](@ref) üzerine güvenmek istemediğinizi belirtir.

Bu varsayılanları geçersiz kılmak için, nesneniz için özel bir `BroadcastStyle` tanımlayabilirsiniz:

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

Bazen `MyStyle` tanımlamak zorunda kalmamak pratik olabilir, bu durumda genel yayın sarmalayıcılarından birini kullanabilirsiniz:

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()` her türlü türler için kullanılabilir.
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()` tercih edilir eğer `MyType` bir `AbstractArray` ise.
  * `Belirli bir boyutluluğu yalnızca destekleyen`AbstractArrays`için,`Broadcast.AbstractArrayStyle{N}`'in bir alt türünü oluşturun (aşağıya bakın).

Yayın işleminiz birden fazla argüman içerdiğinde, bireysel argüman stilleri, çıktı konteynerinin türünü kontrol eden tek bir `DestStyle` belirlemek için birleştirilir. Daha fazla ayrıntı için [below](@ref writing-binary-broadcasting-rules) adresine bakın.

### Selecting an appropriate output array

Her yayınlama işlemi için yayınlama stili hesaplanır, böylece dağıtım ve uzmanlaşma sağlanır. Sonuç dizisinin gerçek tahsisi `benzer` tarafından, Yayınlanan nesneyi ilk argüman olarak kullanarak gerçekleştirilir.

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

Yedek tanım şudur:

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

Ancak, gerekirse bu argümanların herhangi birine veya hepsine özelleşebilirsiniz. Son argüman `bc`, (potansiyel olarak birleştirilmiş) bir yayılma işleminin tembel bir temsilidir, bir `Broadcasted` nesnesidir. Bu amaçlar için, sarmalayıcının en önemli alanları `f` ve `args`'dir; bunlar sırasıyla fonksiyonu ve argüman listesini tanımlar. Argüman listesinin — ve genellikle de — diğer iç içe geçmiş `Broadcasted` sarmalayıcılarını içerebileceğini unutmayın.

Tam bir örnek için, diyelim ki bir `ArrayAndChar` türü oluşturdunuz; bu tür bir dizi ve tek bir karakter saklar:

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

Yayınlamanın `char` "meta verilerini" korumasını isteyebilirsiniz. Öncelikle tanımlıyoruz

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

Bu, aynı zamanda karşılık gelen bir `benzer` yöntemini tanımlamamız gerektiği anlamına gelir:

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

Bu tanımlardan, aşağıdaki davranış elde edilir:

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

Genel olarak, bir yayın işlemi, uygulanacak işlevi ve argümanlarını tutan tembel bir `Broadcasted` konteyneri ile temsil edilir. Bu argümanlar, daha iç içe geçmiş `Broadcasted` konteynerleri de olabilir ve değerlendirilecek büyük bir ifade ağacı oluşturabilir. İç içe geçmiş `Broadcasted` konteynerleri, örtük nokta sözdizimi ile doğrudan oluşturulur; örneğin, `5 .+ 2.*x` geçici olarak `Broadcasted(+, 5, Broadcasted(*, 2, x))` ile temsil edilir. Bu, kullanıcılar için görünmez çünkü hemen `copy` çağrısı ile gerçekleştirilir, ancak bu konteyner, özel türlerin yazarları için yayının genişletilebilirliğinin temelini sağlar. Yerleşik yayın mekanizması, ardından argümanlara dayanarak sonuç türünü ve boyutunu belirleyecek, bunu tahsis edecek ve sonunda `Broadcasted` nesnesinin gerçekleştirilmesini varsayılan `copyto!(::AbstractArray, ::Broadcasted)` yöntemi ile kopyalayacaktır. Yerleşik yedek `broadcast` ve `broadcast!` yöntemleri de benzer şekilde işlemin geçici bir `Broadcasted` temsilini oluşturur, böylece aynı kod yolunu takip edebilirler. Bu, özel dizi uygulamalarının kendi `copyto!` uzmanlaşmalarını sağlayarak yayını özelleştirmesine ve optimize etmesine olanak tanır. Bu, hesaplanan yayın stiline göre belirlenir. Bu, işlemin bu kadar önemli bir parçası olduğu için, `Broadcasted` türünün ilk tür parametresi olarak saklanır ve bu da dağıtım ve uzmanlaşma sağlar.

Bazı türler için, iç içe yayılma seviyeleri arasında işlemleri "birleştirmek" için gereken makine mevcut değildir veya daha verimli bir şekilde kademeli olarak yapılabilir. Bu tür durumlarda, `x .* (x .+ 1)` ifadesini, iç işlemin dış işlemi ele almadan önce değerlendirildiği `broadcast(*, x, broadcast(+, x, 1))` şeklinde yazılmış gibi değerlendirmeniz gerekebilir veya isteyebilirsiniz. Bu tür bir hevesli işlem, biraz dolaylılıkla doğrudan desteklenir; Julia, birleştirilmiş ifadeyi `x .* (x .+ 1)` doğrudan `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))` olarak düşürür. Artık, varsayılan olarak, `broadcasted` sadece birleştirilmiş ifade ağacının tembel temsilini oluşturmak için `Broadcasted` yapıcısını çağırır, ancak belirli bir işlev ve argüman kombinasyonu için bunu geçersiz kılmayı seçebilirsiniz.

Bir örnek olarak, yerleşik `AbstractRange` nesneleri, başlangıç, adım ve uzunluk (veya durdurma) terimleriyle tamamen değerlendirilip değerlendirilebilecek parçaları optimize etmek için bu mekanizmayı kullanır; bu, her bir öğeyi hesaplamak yerine yapılır. Diğer tüm mekanizmalar gibi, `broadcasted` de argümanlarının birleştirilmiş yayılma stilini hesaplar ve sergiler, bu nedenle `broadcasted(f, args...)` üzerinde uzmanlaşmak yerine, stil, fonksiyon ve argümanların herhangi bir kombinasyonu için `broadcasted(::DestStyle, f, args...)` üzerinde uzmanlaşabilirsiniz.

Örneğin, aşağıdaki tanım aralıkların olumsuzluğunu destekler:

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

Yerinde yayılma, uygun `copyto!(dest, bc::Broadcasted)` yöntemini tanımlayarak desteklenebilir. `dest` veya `bc`'nin belirli bir alt türü üzerinde uzmanlaşmak isteyebileceğiniz için, paketler arasında belirsizlikleri önlemek adına aşağıdaki kuralı öneriyoruz.

Eğer belirli bir stil `DestStyle` üzerinde uzmanlaşmak istiyorsanız, bir yöntem tanımlayın.

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

İsteğe bağlı olarak, bu form ile `dest` türüne de özel hale gelebilirsiniz.

Eğer `DestStyle` üzerinde uzmanlaşmak yerine `DestType` üzerinde uzmanlaşmak istiyorsanız, aşağıdaki imzaya sahip bir yöntem tanımlamalısınız:

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

Bu, sarmalayıcıyı `Broadcasted{Nothing}`'a dönüştüren bir yedek uygulamasını kullanır. Sonuç olarak, `DestType` üzerinde uzmanlaşmak, `DestStyle` üzerinde uzmanlaşan yöntemlerden daha düşük önceliğe sahiptir.

Benzer şekilde, `copy(::Broadcasted)` yöntemi ile yerinde olmayan yayılmayı tamamen geçersiz kılabilirsiniz.

#### Working with `Broadcasted` objects

`copy` veya `copyto!` yöntemini uygulamak için, elbette, her bir elementi hesaplamak için `Broadcasted` sarmalayıcısıyla çalışmalısınız. Bunu yapmanın iki ana yolu vardır:

  * `Broadcast.flatten` potansiyel olarak iç içe geçmiş işlemi tek bir fonksiyon ve düz bir argüman listesi haline getirir. Yayılma şekil kurallarını kendiniz uygulamakla sorumlusunuz, ancak bu sınırlı durumlarda yardımcı olabilir.
  * `Broadcasted`'in `axes(::Broadcasted)`'in `CartesianIndices`'ini döngüye alarak ve elde edilen `CartesianIndex` nesnesi ile indeksleme yaparak sonucu hesaplamak.

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

Öncelik kuralları, ikili `BroadcastStyle` çağrılarıyla tanımlanır:

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

`Style12` burada `Style1` ve `Style2` argümanları içeren çıktılar için seçmek istediğiniz `BroadcastStyle`'dır. Örneğin,

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

`Tuple`'ın sıfır boyutlu dizilere (çıktı konteyneri bir demet olacaktır) "üstün" olduğunu belirtir. Kullanıcının argümanları hangi sırayla sağladığından bağımsız olarak, bu çağrının yalnızca bir argüman sırasını tanımlamanız gerektiğini (ve tanımlamamanız gerektiğini) belirtmek önemlidir.

`AbstractArray` türleri için, bir `BroadcastStyle` tanımlamak, geri dönüş seçiminden daha üstündür, [`Broadcast.DefaultArrayStyle`](@ref). `DefaultArrayStyle` ve soyut üst tür `AbstractArrayStyle`, sabit boyut gereksinimlerine sahip özel dizi türlerini desteklemek için boyutluluğu bir tür parametresi olarak saklar.

`DefaultArrayStyle` "kaybeder" tanımlanmış herhangi bir diğer `AbstractArrayStyle`'a aşağıdaki yöntemler nedeniyle:

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

İki veya daha fazla `DefaultArrayStyle` olmayan tür için öncelik belirlemek istemiyorsanız, ikili `BroadcastStyle` kuralları yazmanıza gerek yoktur.

Eğer dizi türünüzün sabit boyut gereksinimleri varsa, `AbstractArrayStyle` alt sınıfını oluşturmalısınız. Örneğin, seyrek dizi kodunun aşağıdaki tanımları vardır:

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

Herhangi bir `AbstractArrayStyle` alt türü oluşturduğunuzda, aynı zamanda bir `Val(N)` argümanı alan stiliniz için bir yapıcı tanımlayarak boyutların birleştirilmesi için kurallar belirlemeniz gerekir. Örneğin:

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

Bu kurallar, `SparseVecStyle`'ın 0 veya 1 boyutlu dizilerle birleştirilmesinin başka bir `SparseVecStyle` ürettiğini, 2 boyutlu bir dizi ile birleştirilmesinin ise bir `SparseMatStyle` ürettiğini belirtir ve daha yüksek boyutlulukların yoğun, keyfi boyutlu çerçeveye geri döndüğünü gösterir. Bu kurallar, yayılmanın, bir veya iki boyutlu çıktılar üreten işlemler için seyrek temsili korumasına izin verir, ancak diğer boyutluluklar için bir `Array` üretir.

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

Bazen, son kullanıcının bir nesnenin alanlarıyla etkileşim şeklini değiştirmek istenir. Kullanıcıya doğrudan alanlara erişim vermek yerine, kullanıcı ile kod arasında bir soyutlama katmanı sağlamak için `object.field` aşırı yüklenebilir. Özellikler, kullanıcının nesneden *gördüğü* şeydir; alanlar ise nesnenin *gerçekten ne olduğu*dur.

Varsayılan olarak, özellikler ve alanlar aynıdır. Ancak, bu davranış değiştirilebilir. Örneğin, [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system) içindeki bir düzlemdeki bir noktanın bu temsilini ele alalım:

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

Yukarıda belirtilen tabloda, nokta erişimi `p.r`, varsayılan olarak `getproperty(p, :r)` ile aynı olup, bu da `getfield(p, :r)` ile aynıdır:

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

Ancak, kullanıcıların `Point`'in koordinatları `r` ve `ϕ` (alanlar) olarak sakladığından haberdar olmalarını istemeyebiliriz ve bunun yerine `x` ve `y` (özellikler) ile etkileşimde bulunmalarını sağlayabiliriz. İlk sütundaki yöntemler, yeni işlevsellik eklemek için tanımlanabilir:

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

`getfield` ve `setfield`'in `getproperty` ve `setproperty!` içinde kullanılması önemlidir, çünkü nokta sözdizimi bu fonksiyonları özyinelemeli hale getirebilir ve bu da tür çıkarım sorunlarına yol açabilir. Artık yeni işlevselliği deneyebiliriz:

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

Son olarak, bu şekilde örnek özellikleri eklemenin Julia'da oldukça nadir yapıldığını ve genel olarak yalnızca iyi bir sebep varsa yapılması gerektiğini belirtmek gerekir.

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

Yeni bir türde yuvarlama desteği sağlamak için genellikle `round(x::ObjType, r::RoundingMode)` tek bir yöntemini tanımlamak yeterlidir. Geçilen yuvarlama modu, değerin hangi yönde yuvarlanması gerektiğini belirler. En yaygın kullanılan yuvarlama modları `RoundNearest`, `RoundToZero`, `RoundDown` ve `RoundUp`'dır; çünkü bu yuvarlama modları, tek argümanlı `round`, `trunc`, `floor` ve `ceil` yöntemlerinin tanımlarında kullanılır.

Bazı durumlarda, iki argümanlı yöntemden daha doğru veya performanslı olan üç argümanlı bir `round` yöntemini tanımlamak mümkündür. Bu durumda, iki argümanlı yöntemin yanı sıra üç argümanlı yöntemi tanımlamak kabul edilebilir. Eğer yuvarlanmış sonucu `T` türünde bir nesne olarak temsil etmek imkansızsa, üç argümanlı yöntem bir `InexactError` fırlatmalıdır.

Örneğin, `Interval` türüne sahip isek ve bu tür, https://github.com/JuliaPhysics/Measurements.jl benzeri olası değerlerin bir aralığını temsil ediyorsa, bu tür üzerinde aşağıdaki gibi yuvarlama tanımlayabiliriz.

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

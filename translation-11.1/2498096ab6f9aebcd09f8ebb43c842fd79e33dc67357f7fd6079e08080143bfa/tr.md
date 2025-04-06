# Sorting and Related Functions

Julia, sıralama ve zaten sıralanmış değer dizileriyle etkileşim kurma konusunda kapsamlı ve esnek bir API'ye sahiptir. Varsayılan olarak, Julia makul algoritmalar seçer ve artan sırada sıralar:

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

Ters sıralama da yapabilirsiniz:

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort`, girdi değişmeden sıralı bir kopya oluşturur. Mevcut bir diziyi değiştirmek için sıralama fonksiyonunun "bang" versiyonunu kullanın:

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

Diziyi doğrudan sıralamak yerine, dizinin sıralı hale gelmesini sağlayan dizinin indekslerinin bir permütasyonunu hesaplayabilirsiniz:

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Diziler, değerlerinin keyfi bir dönüşümüne göre sıralanabilir:

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

Ya da bir dönüşümle ters sırayla:

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

Gerekirse, sıralama algoritması seçilebilir:

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Tüm sıralama ve düzen ile ilgili işlevler, işlenmesi gereken değerler üzerinde bir [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) tanımlayan bir "küçüktür" ilişkisine dayanır. `isless` işlevi varsayılan olarak çağrılır, ancak ilişki `lt` anahtar kelimesi aracılığıyla belirtilebilir; bu, iki dizi elemanı alan ve yalnızca ilk argümanın ikinci argümandan "küçük" olması durumunda `true` döndüren bir işlevdir. Daha fazla bilgi için [`sort!`](@ref) ve [Alternate Orderings](@ref)'ya bakın.

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

Şu anda temel Julia'da kamuya açık olarak mevcut olan dört sıralama algoritması bulunmaktadır:

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

Varsayılan olarak, `sort` fonksiyonları ailesi, çoğu girdi üzerinde hızlı olan kararlı sıralama algoritmalarını kullanır. Tam algoritma seçimi, gelecekteki performans iyileştirmelerine olanak tanımak için bir uygulama ayrıntısıdır. Şu anda, girdi türüne, boyutuna ve bileşimine bağlı olarak `RadixSort`, `ScratchQuickSort`, `InsertionSort` ve `CountingSort`'un bir hibriti kullanılmaktadır. Uygulama ayrıntıları değişebilir, ancak şu anda `??Base.DEFAULT_STABLE`'nin genişletilmiş yardımında ve orada listelenen dahili sıralama algoritmalarının docstring'lerinde mevcuttur.

`alg` anahtar kelimesi ile tercih ettiğiniz algoritmayı açıkça belirtebilirsiniz (örneğin, `sort!(v, alg=PartialQuickSort(10:20))`) veya özel türler için varsayılan sıralama algoritmasını yeniden yapılandırmak için `Base.Sort.defalg` fonksiyonuna özel bir yöntem ekleyebilirsiniz. Örneğin, [InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903) aşağıdaki yöntemi tanımlar:

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    `Base.Sort.defalg` tarafından döndürülen varsayılan sıralama algoritması, Julia 1.9'dan itibaren kararlıdır. Önceki sürümlerde sayısal dizileri sıralarken kararsız kenar durumları vardı.


## Alternate Orderings

Varsayılan olarak, `sort`, `searchsorted` ve ilgili fonksiyonlar, iki öğeyi karşılaştırmak için [`isless`](@ref) kullanır ve hangisinin önce geleceğini belirler. [`Base.Order.Ordering`](@ref) soyut türü, aynı öğe kümesi üzerinde alternatif sıralamalar tanımlamak için bir mekanizma sağlar: `sort!` gibi bir sıralama fonksiyonu çağrıldığında, `order` anahtar kelime argümanı ile bir `Ordering` örneği sağlanabilir.

`Ordering` örnekleri, [`Base.Order.lt`](@ref) fonksiyonu aracılığıyla bir sıralama tanımlar; bu, `isless`'in genelleştirilmiş bir versiyonudur. Bu fonksiyonun özel `Ordering`'ler üzerindeki davranışı, [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings)'ün tüm koşullarını karşılamalıdır. Geçerli ve geçersiz `lt` fonksiyonları hakkında ayrıntılar ve örnekler için [`sort!`](@ref)'ya bakın.

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```

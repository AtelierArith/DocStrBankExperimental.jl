# [Missing Values](@id missing)

Julia, istatistiksel anlamda eksik değerleri temsil etme desteği sağlar. Bu, bir gözlemde bir değişken için hiçbir değerin mevcut olmadığı, ancak teorik olarak geçerli bir değerin var olduğu durumlar içindir. Eksik değerler, [`missing`](@ref) nesnesi aracılığıyla temsil edilir; bu, [`Missing`](@ref) türünün tekil örneğidir. `missing`, [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) ve [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling) ile eşdeğerdir ve çoğu durumda onlarla aynı şekilde davranır.

## Propagation of Missing Values

`eksik` değerler *otomatik olarak* standart matematiksel operatörler ve fonksiyonlara geçirildiğinde yayılır. Bu fonksiyonlar için, operandlardan birinin değeri hakkında belirsizlik, sonucun belirsizliğini doğurur. Pratikte, bir `eksik` değer içeren bir matematik işlemi genellikle `eksik` döner:

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

`missing` normal bir Julia nesnesi olduğu için, bu yayılma kuralı yalnızca bu davranışı uygulamayı seçen fonksiyonlar için geçerlidir. Bu, aşağıdaki şekilde gerçekleştirilebilir:

  * `Missing` türündeki argümanlar için tanımlanmış özel bir yöntem ekleniyor,
  * bu tür argümanları kabul etmek ve bunları (standart matematik operatörleri gibi) yayan fonksiyonlara iletmek.

Paketler, yeni fonksiyonlar tanımlarken eksik değerlerin yayılmasının mantıklı olup olmadığını dikkate almalı ve bu durum söz konusuysa yöntemleri uygun şekilde tanımlamalıdır. Bir `missing` değerini, `Missing` türünde argümanları kabul eden bir yöntemi olmayan bir fonksiyona geçirmek, diğer türler için olduğu gibi [`MethodError`](@ref) hatasını fırlatır.

`missing` değerlerini yaymayan fonksiyonlar, [Missings.jl](https://github.com/JuliaData/Missings.jl) paketinde sağlanan `passmissing` fonksiyonu ile sarılarak bu şekilde çalıştırılabilir. Örneğin, `f(x)` ifadesi `passmissing(f)(x)` haline gelir.

## Equality and Comparison Operators

Standart eşitlik ve karşılaştırma operatörleri yukarıda sunulan yayılma kuralını takip eder: eğer operandlardan herhangi biri `eksik` ise, sonuç `eksik` olur. İşte birkaç örnek:

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

Özellikle, `missing == missing` ifadesinin `missing` döndürdüğünü unutmayın, bu nedenle `==` operatörü bir değerin eksik olup olmadığını test etmek için kullanılamaz. `x`'in `missing` olup olmadığını test etmek için [`ismissing(x)`](@ref) kullanın.

Özel karşılaştırma operatörleri [`isequal`](@ref) ve [`===`](@ref) yayılma kuralının istisnalarıdır. Her zaman bir `Bool` değeri döndüreceklerdir, `missing` değerlerinin varlığında bile, `missing` değerini `missing` ile eşit ve diğer herhangi bir değerden farklı olarak kabul ederek. Bu nedenle, bir değerin `missing` olup olmadığını test etmek için kullanılabilirler:

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

[`isless`](@ref) operatörü başka bir istisnadır: `missing`, diğer tüm değerlerden daha büyük olarak kabul edilir. Bu operatör, [`sort!`](@ref) tarafından kullanılır; bu nedenle `missing` değerleri diğer tüm değerlerin ardından yer alır:

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

Mantıksal (veya boolean) operatörler [`|`](@ref), [`&`](@ref) ve [`xor`](@ref) başka bir özel durumdur çünkü yalnızca mantıksal olarak gerekli olduğunda `eksik` değerleri yayarlar. Bu operatörler için, sonucun belirsiz olup olmaması, belirli bir işleme bağlıdır. Bu, [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic) tarafından uygulanan iyi bilinen kuralları takip eder; örneğin SQL'deki `NULL` ve R'deki `NA`. Bu soyut tanım, somut örneklerle en iyi şekilde açıklanan nispeten doğal bir davranışa karşılık gelir.

Bu prensibi mantıksal "veya" operatörü [`|`](@ref) ile gösterelim. Boolean mantığı kurallarına göre, eğer operandlardan biri `doğru` ise, diğer operandın değeri sonuca etki etmez, sonuç her zaman `doğru` olacaktır:

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

Bu gözlemden yola çıkarak, eğer operandlardan biri `doğru` ve diğeri `eksik` ise, bir operandın gerçek değeri hakkında belirsizlik olmasına rağmen sonucun `doğru` olduğunu biliyoruz. Eğer ikinci operandın gerçek değerini gözlemleyebilseydik, bu yalnızca `doğru` veya `yanlış` olabilir ve her iki durumda da sonuç `doğru` olurdu. Bu nedenle, bu özel durumda, eksiklik *yayılmaz*:

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

Tam tersine, eğer operandlardan biri `false` ise, sonuç diğer operandın değerine bağlı olarak ya `true` ya da `false` olabilir. Bu nedenle, eğer o operand `missing` ise, sonuç da `missing` olmalıdır:

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

Mantıksal "ve" operatörünün [`&`](@ref) davranışı, `|` operatörünün davranışına benzer; ancak, bir operand `false` olduğunda eksikliklerin yayılmadığı bir fark vardır. Örneğin, bu durum ilk operand için geçerli olduğunda:

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

Diğer yandan, eksiklik, operandlardan biri `true` olduğunda yayılır, örneğin ilki:

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

Sonunda, "özel veya" mantıksal operatör [`xor`](@ref) her zaman `eksik` değerleri yayar, çünkü her iki operand da sonucun üzerinde her zaman etkiye sahiptir. Ayrıca, [`!`](@ref) olumsuzlama operatörünün operandı `eksik` olduğunda `eksik` döndürdüğünü, diğer tekil operatörler gibi unutmayın.

## Control Flow and Short-Circuiting Operators

Kontrol akış operatörleri [`if`](@ref), [`while`](@ref) ve [ternary operator](@ref man-conditional-evaluation) `x ? y : z` eksik değerleri kabul etmez. Bunun nedeni, gözlemleyebilseydik gerçek değerin `true` veya `false` olup olmayacağı konusunda belirsizlik olmasıdır. Bu, programın nasıl davranması gerektiğini bilmediğimiz anlamına gelir. Bu durumda, bu bağlamda bir `missing` değeriyle karşılaşıldığında hemen bir [`TypeError`](@ref) fırlatılır:

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

Aynı nedenle, yukarıda sunulan mantıksal operatörlerin aksine, kısa devre boolean operatörleri [`&&`](@ref) ve [`||`](@ref), operandın değeri bir sonraki operandın değerlendirilip değerlendirilmeyeceğini belirlediği durumlarda `eksik` değerlere izin vermez. Örneğin:

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

Buna karşılık, `eksik` değerler olmadan sonucun belirlenebildiği durumlarda hata fırlatılmaz. Bu, kodun `eksik` operatörünü değerlendirmeden önce kısa devre yaptığı ve `eksik` operatörünün sonuncu olduğu durumlarda geçerlidir:

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

Eksik değerler içeren diziler, diğer diziler gibi oluşturulabilir:

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

Bu örneğin gösterdiği gibi, bu tür dizilerin eleman tipi `Union{Missing, T}`'dir; burada `T`, eksik olmayan değerlerin tipidir. Bu, dizi girişlerinin ya `T` tipinde (burada `Int64`) ya da `Missing` tipinde olabileceğini yansıtır. Bu tür bir dizi, gerçek değerleri tutan bir `Array{T}` ile girişin tipini (yani, `Missing` mi yoksa `T` mi olduğunu) belirten bir `Array{UInt8}`'in birleşimi ile eşdeğer verimli bir bellek depolama kullanır.

Eksik değerleri içeren diziler standart sözdizimi ile oluşturulabilir. Eksik değerlerle doldurulmuş diziler oluşturmak için `Array{Union{Missing, T}}(missing, dims)` kullanın:

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    `undef` veya `benzer` kullanmak şu anda `missing` ile doldurulmuş bir dizi verebilir, ancak bu tür bir diziyi elde etmenin doğru yolu değildir. Bunun yerine yukarıda gösterildiği gibi bir `missing` yapıcı kullanın.


Bir `missing` girişlerine izin veren bir dizi türü (örneğin, `Vector{Union{Missing, T}}`) `missing` girişleri içermiyorsa, `missing` girişlerine izin vermeyen bir dizi türüne (örneğin, `Vector{T}`) [`convert`](@ref) kullanılarak dönüştürülebilir. Dizi `missing` değerleri içeriyorsa, dönüştürme sırasında bir `MethodError` hatası fırlatılır:

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

`missing` değerleri standart matematiksel operatörlerle yayıldığı için, eksik değerler içeren diziler üzerinde çağrıldığında azaltma fonksiyonları `missing` döner:

```jldoctest
julia> sum([1, missing])
missing
```

Bu durumda, eksik değerleri atlamak için [`skipmissing`](@ref) fonksiyonunu kullanın:

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

Bu kullanım kolaylığı sağlayan fonksiyon, `eksik` değerleri verimli bir şekilde filtreleyen bir yineleyici döndürür. Bu nedenle, yineleyicileri destekleyen herhangi bir fonksiyonla kullanılabilir:

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

`skipmissing` ile bir dizi üzerinde çağrılarak oluşturulan nesneler, ana diziden alınan indeksler kullanılarak indekslenebilir. Eksik değerlere karşılık gelen indeksler bu nesneler için geçerli değildir ve bunları kullanmaya çalıştığınızda bir hata fırlatılır (aynı zamanda `keys` ve `eachindex` tarafından da atlanır):

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

Bu, indeksler üzerinde çalışan işlevlerin `skipmissing` ile bir arada çalışmasına olanak tanır. Bu, özellikle arama ve bulma işlevleri için geçerlidir. Bu işlevler, `skipmissing` tarafından döndürülen nesne için geçerli olan indeksleri döndürür ve ayrıca eşleşen girişlerin *ana dizideki* indeksleridir:

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

[`collect`](@ref) değerlerini kullanarak `missing` olmayan değerleri çıkarın ve bir diziye kaydedin:

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

Yukarıda açıklanan üç değerli mantık, dizilere uygulanan mantıksal fonksiyonlar tarafından da kullanılmaktadır. Bu nedenle, [`==`](@ref) operatörünü kullanan dizi eşitlik testleri, `missing` girişinin gerçek değerini bilmeden belirlenemeyen bir sonuç olduğunda `missing` döndürür. Pratikte, bu, karşılaştırılan dizilerin tüm eksik olmayan değerleri eşitse, ancak bir veya her iki dizinin eksik değerler içermesi durumunda (muhtemelen farklı konumlarda) `missing` döndürüldüğü anlamına gelir:

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

Tekil değerler için, [`isequal`](@ref) kullanarak `missing` değerlerini diğer `missing` değerlerle eşit, ancak eksik olmayan değerlerden farklı olarak ele alın.

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

Fonksiyonlar [`any`](@ref) ve [`all`](@ref) aynı zamanda üç değerli mantık kurallarını takip eder. Bu nedenle, sonuç belirlenemediğinde `missing` döner:

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```

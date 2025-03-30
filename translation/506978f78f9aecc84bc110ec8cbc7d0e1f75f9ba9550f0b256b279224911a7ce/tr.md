# Reflection and introspection

Julia, çeşitli çalışma zamanı yansıma yetenekleri sunar.

## Module bindings

`Module` için kamuya açık isimler [`names(m::Module)`](@ref) kullanılarak elde edilebilir; bu, kamuya açık bağlamaları temsil eden [`Symbol`](@ref) elemanlarının bir dizisini döndürecektir. `names(m::Module, all = true)` ise `m` içindeki tüm bağlamalar için, kamuya açık durumuna bakılmaksızın semboller döndürür.

## DataType fields

`DataType` alanlarının isimleri [`fieldnames`](@ref) kullanılarak sorgulanabilir. Örneğin, aşağıdaki tür için `fieldnames(Point)` ifadesi, alan isimlerini temsil eden bir [`Symbol`](@ref) demetini döndürür:

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

`Point` nesnesindeki her alanın türü, `Point` değişkeninin kendisindeki `types` alanında saklanır:

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

`x` bir `Int` olarak anotasyonlanmışken, `y` tip tanımında anotasyonsuz bırakılmıştır, bu nedenle `y` varsayılan olarak `Any` tipine sahiptir.

Türler, `DataType` adı verilen bir yapı olarak temsil edilir:

```jldoctest struct_point
julia> typeof(Point)
DataType
```

`fieldnames(DataType)` ifadesinin, `DataType`'ın kendisine ait her bir alanın adlarını verdiğini ve bu alanlardan birinin yukarıdaki örnekte gözlemlenen `types` alanı olduğunu unutmayın.

## Subtypes

Herhangi bir `DataType`'ın *doğrudan* alt türleri [`subtypes`](@ref) kullanılarak listelenebilir. Örneğin, soyut `DataType` [`AbstractFloat`](@ref) dört (somut) alt türe sahiptir:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

Herhangi bir soyut alt tür de bu listeye dahil edilecektir, ancak bunların daha fazla alt türü dahil edilmeyecektir; [`subtypes`](@ref) ifadesinin özyinelemeli uygulanması tam tür ağaç yapısını incelemek için kullanılabilir.

Not edin ki [`subtypes`](@ref) [`InteractiveUtils`](@ref man-interactive-utils) içinde yer almaktadır ancak REPL kullanıldığında otomatik olarak dışa aktarılmaktadır.

## DataType layout

`DataType`'ın içsel temsili, C kodu ile etkileşimde kritik öneme sahiptir ve bu ayrıntıları incelemek için birkaç işlev mevcuttur. [`isbitstype(T::DataType)`](@ref), `T`'nin C ile uyumlu hizalamayla saklandığında doğru döner. [`fieldoffset(T::DataType, i::Integer)`](@ref), türün başlangıcına göre alan *i* için (bayt) ofseti döner.

## Function methods

Herhangi bir genel fonksiyonun yöntemleri [`methods`](@ref) kullanılarak listelenebilir. Belirli bir türü kabul eden yöntemler için yöntem dağıtım tablosu [`methodswith`](@ref) kullanılarak aranabilir.

## Expansion and lowering

[Metaprogramming](@ref) bölümünde tartışıldığı gibi, [`macroexpand`](@ref) fonksiyonu, belirli bir makro için alıntılanmamış ve interpolasyonlu ifadeyi ([`Expr`](@ref)) verir. `macroexpand` kullanmak için, ifade bloğunu kendisini `quote` edin (aksi takdirde, makro değerlendirilecek ve sonuç yerine geçecektir!). Örneğin:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

`Base.Meta.show_sexpr` ve [`dump`](@ref) fonksiyonları, herhangi bir ifadenin S-expr tarzı görünümlerini ve derinlik açısından iç içe geçmiş detay görünümlerini görüntülemek için kullanılır.

Sonunda, [`Meta.lower`](@ref) fonksiyonu, herhangi bir ifadenin `lowered` formunu verir ve dil yapıların temel işlemlere, örneğin atamalar, dallanmalar ve çağrılar gibi, nasıl eşlendiğini anlamak için özellikle ilgi çekicidir:

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

Fonksiyonlar için düşürülmüş formu incelemek, belirli bir yöntemi görüntülemek için seçim yapmayı gerektirir, çünkü genel fonksiyonların farklı tür imzalarına sahip birçok yöntemi olabilir. Bu amaçla, yöntem-spesifik kod düşürme [`code_lowered`](@ref) kullanılarak mevcuttur ve tür çıkarımlı form [`code_typed`](@ref) kullanılarak mevcuttur. [`code_warntype`](@ref), `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566` çıktısına vurgulama ekler.

Makineye daha yakın, bir fonksiyonun LLVM ara temsili [`code_llvm`](@ref) kullanılarak yazdırılabilir ve nihayetinde derlenmiş makine kodu [`code_native`](@ref) kullanılarak erişilebilir (bu, daha önce çağrılmamış herhangi bir fonksiyon için JIT derleme/kod üretimini tetikleyecektir).

Kolaylık sağlamak için, yukarıdaki işlevlerin standart işlev çağrılarını alıp argüman türlerini otomatik olarak genişleten makro sürümleri vardır:

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

Daha fazla bilgi için [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_warntype`](@ref), [`@code_llvm`](@ref), ve [`@code_native`](@ref).

### Printing of debug information

Yukarıda bahsedilen fonksiyonlar ve makrolar, yazdırılan hata ayıklama bilgisi seviyesini kontrol eden `debuginfo` anahtar kelime argümanını alır.

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

`debuginfo` için olası değerler: `:none`, `:source` ve `:default`. Varsayılan olarak hata ayıklama bilgisi yazdırılmaz, ancak bu, `Base.IRShow.default_debuginfo[] = :source` ayarlanarak değiştirilebilir.

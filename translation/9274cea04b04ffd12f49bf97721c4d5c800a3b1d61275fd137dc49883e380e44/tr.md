```
AnnotatedString{S <: AbstractString} <: AbstractString
```

Metadata içeren, anotasyonlu bölgeler şeklinde bir dize.

Daha spesifik olarak, bu, sarılı dize içindeki bölgelerin etiketli değerlerle anotasyonlanmasına izin veren herhangi bir [`AbstractString`](@ref) etrafında basit bir sargıdır.

```text
                           C
                    ┌──────┸─────────┐
  "bu bir örnek anotasyonlu dizedir"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

Yukarıdaki diyagram, üç aralığın anotasyonlandığı bir `AnnotatedString`'i temsil etmektedir (etiketleri `A`, `B` ve `C`). Her anotasyon bir etiket (`Symbol`) ve bir değer (`Any`) tutar. Bu üç bilgi, `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}` olarak tutulur.

Etiketlerin benzersiz olması gerekmez, aynı bölge aynı etiketle birden fazla anotasyon tutabilir.

Genel olarak `AnnotatedString`'ler için yazılan kod, aşağıdaki özellikleri korumalıdır:

  * Bir anotasyonun hangi karakterlere uygulandığı
  * Her karakter için anotasyonların uygulandığı sıra

`AnnotatedString`'lerin belirli kullanımlarıyla ek anlamlar getirilebilir.

Bu kuralların bir sonucu olarak, aynı etiket ve değerlere sahip bitişik, ardışık yerleştirilmiş anotasyonlar, birleşik aralığı kapsayan tek bir anotasyona eşdeğerdir.

Ayrıca [`AnnotatedChar`](@ref), [`annotatedstring`](@ref), [`annotations`](@ref) ve [`annotate!`](@ref) ile de bakılabilir.

# Yapıcılar

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

Bir AnnotatedString, [`annotatedstring`](@ref) ile de oluşturulabilir; bu, [`string`](@ref) gibi çalışır ancak argümanlarda mevcut olan herhangi bir anotasyonu korur.

# Örnekler

```julia-repl
julia> AnnotatedString("bu bir örnek anotasyonlu dizedir",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"bu bir örnek anotasyonlu dizedir"
```

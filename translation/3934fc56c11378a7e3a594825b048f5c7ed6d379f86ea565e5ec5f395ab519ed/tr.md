```
@NamedTuple{anahtar1::Tip1, anahtar2::Tip2, ...}
@NamedTuple begin anahtar1::Tip1; anahtar2::Tip2; ...; end
```

Bu makro, `NamedTuple` türlerini tanımlamak için daha kullanışlı bir sözdizimi sağlar. Verilen anahtarlar ve türlerle bir `NamedTuple` türü döndürür; bu, `NamedTuple{(:anahtar1, :anahtar2, ...), Tuple{Tip1,Tip2,...}}` ile eşdeğerdir. `::Tip` bildirimi atlandığında, bu `Any` olarak alınır. `begin ... end` biçimi, bildirimlerin birden fazla satıra bölünmesine izin verir (bir `struct` bildirimine benzer), ancak aksi takdirde eşdeğerdir. `NamedTuple` makrosu, `NamedTuple` türlerini örneğin REPL'de yazdırırken kullanılır.

Örneğin, `(a=3.1, b="merhaba")` demeti `NamedTuple{(:a, :b), Tuple{Float64, String}}` türüne sahiptir; bu da `@NamedTuple` ile şu şekilde tanımlanabilir:

```jldoctest
julia> @NamedTuple{a::Float64, b::String}
@NamedTuple{a::Float64, b::String}

julia> @NamedTuple begin
           a::Float64
           b::String
       end
@NamedTuple{a::Float64, b::String}
```

!!! uyumluluk "Julia 1.5"
    Bu makro, Julia 1.5 itibarıyla mevcuttur.


```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

`xs`'yi bir sembol veya tam sayı olarak belirtilen bir renkte, isteğe bağlı olarak kalın olarak yazdırır.

`color` anahtar kelimesi `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white` veya `:yellow` veya 0 ile 255 arasında bir tam sayı alabilir. Tüm terminallerin 256 rengi desteklemediğini unutmayın.

`bold=true`, `italic=true`, `underline=true`, `blink=true` anahtar kelimeleri kendiliğinden açıklayıcıdır. `reverse=true` anahtar kelimesi, ön plan ve arka plan renklerini değiştirilmiş olarak yazdırır ve `hidden=true` terminalde görünmez olmalıdır ancak yine de kopyalanabilir. Bu özellikler herhangi bir kombinasyonda kullanılabilir.

Ayrıca [`print`](@ref), [`println`](@ref), [`show`](@ref) bakınız.

!!! not
    Tüm terminaller italik çıktıyı desteklemez. Bazı terminaller italik çıktıyı ters veya yanıp sönen olarak yorumlar.


!!! uyumluluk "Julia 1.7"
    `color` ve `bold` dışındaki anahtar kelimeler Julia 1.7'de eklendi.


!!! uyumluluk "Julia 1.10"
    İtalik çıktı desteği Julia 1.10'da eklendi.


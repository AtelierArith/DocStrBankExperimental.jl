```
showable(mime, x)
```

Verilen `mime` türünde nesne `x`'in yazılıp yazılamayacağını belirten bir boolean değeri döndürür.

(Varsayılan olarak, bu, `typeof(x)` için karşılık gelen [`show`](@ref) yönteminin varlığına göre otomatik olarak belirlenir. Bazı türler özel `showable` yöntemleri sağlar; örneğin, mevcut MIME formatları `x`'in *değerine* bağlıysa.)

# Örnekler

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```

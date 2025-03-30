```
+(x, y...)
```

Toplama operatörü.

İnfix `x+y+z+...` bu fonksiyonu tüm argümanlarla çağırır, yani `+(x, y, z, ...)`, bu varsayılan olarak soldan başlayarak `(x+y) + z + ...` çağırır.

Büyük sayılar toplandığında, varsayılan `Int` dahil olmak üzere çoğu tam sayı türü için taşma olasılığının olduğunu unutmayın.

# Örnekler

```jldoctest
julia> 1 + 20 + 4
25

julia> +(1, 20, 4)
25

julia> [1,2] + [3,4]
2-element Vector{Int64}:
 4
 6

julia> typemax(Int) + 1 < 0
true
```

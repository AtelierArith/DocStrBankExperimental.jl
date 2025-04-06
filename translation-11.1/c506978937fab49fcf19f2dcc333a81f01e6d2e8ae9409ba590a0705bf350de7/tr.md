```
argmin(f, domain)
```

`f(x)`'in en küçük olduğu `domain`'den bir değer `x` döndürür. Eğer `f(x)` için birden fazla en küçük değer varsa, ilki bulunacaktır.

`domain` boş olmayan bir yineleyici olmalıdır.

`NaN`, `missing` hariç tüm diğer değerlerden daha küçük olarak kabul edilir.

!!! compat "Julia 1.7"
    Bu yöntem Julia 1.7 veya daha yenisini gerektirir.


Ayrıca bkz. [`argmax`](@ref), [`findmin`](@ref).

# Örnekler

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```

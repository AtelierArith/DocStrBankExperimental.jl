```
@ncallkw N f kw sym...
```

Anahtar argümanlar `kw...` ile bir fonksiyon çağrısı ifadesi oluşturun. [`@ncall`](@ref) durumunda olduğu gibi, `sym` herhangi bir sayıda fonksiyon argümanını temsil eder, bunların sonuncusu bir anonim fonksiyon ifadesi olabilir ve `N` argümanına genişletilir.

# Örnekler

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```

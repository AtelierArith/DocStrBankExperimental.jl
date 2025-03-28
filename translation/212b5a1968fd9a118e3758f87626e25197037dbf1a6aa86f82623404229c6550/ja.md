```
frexp(val)
```

`x`が$[1/2, 1)$または0の範囲の大きさを持ち、`val`が$x \times 2^{exp}$に等しいように、`(x,exp)`を返します。

関連情報としては、[`significand`](@ref)、[`exponent`](@ref)、[`ldexp`](@ref)があります。

# 例

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # [1, 2)の範囲に代わり
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # exponentはエラーを返す
((0.0, 0), (NaN, 0), (-Inf, 0))
```

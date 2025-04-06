```
widemul(x, y)
```

`x`와 `y`를 곱하여 결과를 더 큰 타입으로 반환합니다.

자세한 내용은 [`promote`](@ref), [`Base.add_sum`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```

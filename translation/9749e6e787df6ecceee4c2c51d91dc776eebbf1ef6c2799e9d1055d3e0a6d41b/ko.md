```
cld(x, y)
```

`x / y`보다 크거나 같은 가장 작은 정수. `div(x, y, RoundUp)`와 동일합니다.

자세한 내용은 [`div`](@ref), [`fld`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```

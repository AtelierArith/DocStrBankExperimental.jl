```
div(x, y)
÷(x, y)
```

유클리드(정수) 나눗셈의 몫. 일반적으로 분수 부분이 없는 수학적 연산 x/y와 동등합니다.

참고: [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# 예제

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```

```
sign(x)
```

`x==0`일 때는 0을 반환하고, 그렇지 않으면 $x/|x|$를 반환합니다 (즉, 실수 `x`에 대해 ±1).

자세한 내용은 [`signbit`](@ref), [`zero`](@ref), [`copysign`](@ref), [`flipsign`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> sign(-4.0)
-1.0

julia> sign(99)
1

julia> sign(-0.0)
-0.0

julia> sign(0 + im)
0.0 + 1.0im
```

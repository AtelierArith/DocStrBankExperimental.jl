```
-(x)
```

단항 음수 연산자.

참고: [`abs`](@ref), [`flipsign`](@ref).

# 예제

```jldoctest
julia> -1
-1

julia> -(2)
-2

julia> -[1 2; 3 4]
2×2 Matrix{Int64}:
 -1  -2
 -3  -4

julia> -(true)  # Int로 승격됨
-1

julia> -(0x003)
0xfffd
```

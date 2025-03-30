```
exp2(x)
```

`x`의 밑 2 지수를 계산합니다. 즉, $2^x$입니다.

또한 [`ldexp`](@ref), [`<<`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```

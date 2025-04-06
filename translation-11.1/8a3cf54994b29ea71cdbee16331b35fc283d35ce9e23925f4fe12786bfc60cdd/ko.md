```
@showtime expr
```

`@time`와 비슷하지만 참조를 위해 평가되는 표현식도 출력합니다.

!!! compat "Julia 1.8"
    이 매크로는 Julia 1.8에 추가되었습니다.


또한 [`@time`](@ref)를 참조하세요.

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 seconds (4 allocations: 128 bytes)
```

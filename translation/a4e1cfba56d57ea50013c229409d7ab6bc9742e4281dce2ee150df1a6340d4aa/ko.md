```
@allocations
```

표현식을 평가하고 결과 값을 버린 다음, 표현식 평가 중에 발생한 총 할당 수를 반환하는 매크로입니다.

또한 [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), 및 [`@elapsed`](@ref)를 참조하십시오.

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    이 매크로는 Julia 1.9에 추가되었습니다.


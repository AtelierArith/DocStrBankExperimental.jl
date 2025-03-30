```
@allocated
```

표현식을 평가하고 결과 값을 버린 다음, 표현식 평가 중에 할당된 총 바이트 수를 반환하는 매크로입니다.

또한 [`@allocations`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), 및 [`@elapsed`](@ref)를 참조하십시오.

```julia-repl
julia> @allocated rand(10^6)
8000080
```

```
@timed
```

표현식을 실행하고, 표현식의 값, 경과 시간(초), 총 할당된 바이트, 가비지 수집 시간, 다양한 메모리 할당 카운터가 포함된 객체, 컴파일 시간(초) 및 재컴파일 시간(초)을 반환하는 매크로입니다. [`ReentrantLock`](@ref) 이 대기해야 했던 모든 잠금 충돌은 카운트로 표시됩니다.

경우에 따라 시스템은 `@timed` 표현식 내부를 살펴보고 최상위 표현식의 실행이 시작되기 전에 호출된 코드의 일부를 컴파일합니다. 그럴 경우 일부 컴파일 시간은 계산되지 않습니다. 이 시간을 포함하려면 `@timed @eval ...`을 실행할 수 있습니다.

또한 [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), [`@allocations`](@ref), 및 [`@lock_conflicts`](@ref)도 참조하십시오.

```julia-repl
julia> stats = @timed rand(10^6);

julia> stats.time
0.006634834

julia> stats.bytes
8000256

julia> stats.gctime
0.0055765

julia> propertynames(stats.gcstats)
(:allocd, :malloc, :realloc, :poolalloc, :bigalloc, :freecall, :total_time, :pause, :full_sweep)

julia> stats.gcstats.total_time
5576500

julia> stats.compile_time
0.0

julia> stats.recompile_time
0.0

```

!!! compat "Julia 1.5"
    이 매크로의 반환 유형은 Julia 1.5에서 `Tuple`에서 `NamedTuple`로 변경되었습니다.


!!! compat "Julia 1.11"
    `lock_conflicts`, `compile_time`, 및 `recompile_time` 필드는 Julia 1.11에서 추가되었습니다.


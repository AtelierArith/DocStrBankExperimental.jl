```
@timev expr
@timev "description" expr
```

이것은 `@time` 매크로의 자세한 버전입니다. 먼저 `@time`과 동일한 정보를 출력한 다음, 비제로 메모리 할당 카운터를 출력하고, 마지막으로 표현식의 값을 반환합니다.

선택적으로 시간 보고서 전에 출력할 설명 문자열을 제공할 수 있습니다.

!!! compat "Julia 1.8"
    설명을 추가하는 옵션은 Julia 1.8에서 도입되었습니다.


또한 [`@time`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), 및 [`@allocations`](@ref)를 참조하십시오.

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 seconds (2.20 M allocations: 116.632 MiB, 4.23% gc time, 99.94% compilation time)
elapsed time (ns): 546769547
gc time (ns):      23115606
bytes allocated:   122297811
pool allocs:       2197930
non-pool GC allocs:1327
malloc() calls:    36
realloc() calls:   5
GC pauses:         3

julia> @timev x * x;
  0.000010 seconds (1 allocation: 896 bytes)
elapsed time (ns): 9848
bytes allocated:   896
pool allocs:       1
```

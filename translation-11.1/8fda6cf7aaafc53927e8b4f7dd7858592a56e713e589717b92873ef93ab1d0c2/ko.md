```
@time expr
@time "description" expr
```

표현식을 실행하고, 실행하는 데 걸린 시간, 할당 수, 실행으로 인해 할당된 총 바이트 수를 인쇄한 후 표현식의 값을 반환하는 매크로입니다. 가비지 수집(gc), 새로운 코드 컴파일 또는 무효화된 코드 재컴파일에 소요된 시간은 백분율로 표시됩니다. [`ReentrantLock`](@ref) 대기와 같은 잠금 충돌은 카운트로 표시됩니다.

선택적으로 시간 보고서 전에 인쇄할 설명 문자열을 제공할 수 있습니다.

일부 경우 시스템은 `@time` 표현식 내부를 살펴보고 최상위 표현식 실행이 시작되기 전에 호출된 코드의 일부를 컴파일합니다. 그럴 경우 일부 컴파일 시간은 계산되지 않습니다. 이 시간을 포함하려면 `@time @eval ...`을 실행할 수 있습니다.

또한 [`@showtime`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), 및 [`@allocations`](@ref)를 참조하십시오.

!!! note
    보다 심각한 벤치마킹을 위해 BenchmarkTools.jl 패키지의 `@btime` 매크로를 고려하십시오. 이 매크로는 여러 번 함수를 평가하여 노이즈를 줄이는 등의 기능을 제공합니다.


!!! compat "Julia 1.8"
    설명을 추가하는 옵션은 Julia 1.8에서 도입되었습니다.

    컴파일 시간과 별도로 재컴파일 시간이 표시되는 것은 Julia 1.8에서 도입되었습니다.


!!! compat "Julia 1.11"
    잠금 충돌 보고는 Julia 1.11에서 추가되었습니다.


```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 seconds (2.19 M allocations: 116.555 MiB, 3.75% gc time, 99.94% compilation time)

julia> @time x * x;
  0.000009 seconds (1 allocation: 896 bytes)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 seconds (8 allocations: 336 bytes)
2

julia> @time "A one second sleep" sleep(1)
A one second sleep: 1.005750 seconds (5 allocations: 144 bytes)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 seconds (5 allocations: 144 bytes)
2: 1.001263 seconds (5 allocations: 144 bytes)
3: 1.003676 seconds (5 allocations: 144 bytes)
```

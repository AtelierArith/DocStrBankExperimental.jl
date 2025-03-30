```
rmprocs(pids...; waitfor=typemax(Int))
```

지정된 작업자를 제거합니다. 프로세스 1만 작업자를 추가하거나 제거할 수 있습니다.

인수 `waitfor`는 작업자가 종료될 때까지 기다리는 시간을 지정합니다:

  * 지정하지 않으면, `rmprocs`는 요청된 모든 `pids`가 제거될 때까지 기다립니다.
  * 요청된 `waitfor` 초 이전에 모든 작업자를 종료할 수 없는 경우 [`ErrorException`](@ref)이 발생합니다.
  * `waitfor` 값이 0이면, 호출은 즉시 반환되며 작업자는 다른 작업에서 제거될 예정입니다. 예약된 [`Task`](@ref) 객체가 반환됩니다. 사용자는 다른 병렬 호출을 수행하기 전에 작업에서 [`wait`](@ref)를 호출해야 합니다.

# 예제

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```

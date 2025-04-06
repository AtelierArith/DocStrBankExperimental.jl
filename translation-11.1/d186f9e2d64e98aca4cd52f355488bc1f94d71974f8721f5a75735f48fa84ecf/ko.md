```
@lock_conflicts
```

표현식을 평가하고 결과 값을 버린 다음, 평가 중에 잠금 시도가 [`ReentrantLock`](@ref)에서 대기하게 된 잠금 충돌의 총 수를 반환하는 매크로입니다.

또한 [`@time`](@ref), [`@timev`](@ref) 및 [`@timed`](@ref)를 참조하십시오.

```julia-repl
julia> @lock_conflicts begin
    l = ReentrantLock()
    Threads.@threads for i in 1:Threads.nthreads()
        lock(l) do
        sleep(1)
        end
    end
end
5
```

!!! compat "Julia 1.11"
    이 매크로는 Julia 1.11에 추가되었습니다.


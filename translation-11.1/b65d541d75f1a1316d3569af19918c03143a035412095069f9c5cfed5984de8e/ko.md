```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

`func`에서 새 작업을 생성하고, 이를 크기 `size`와 유형 `T`의 새 채널에 바인딩한 후, 단일 호출로 작업을 예약합니다. 작업이 종료되면 채널이 자동으로 닫힙니다.

`func`는 바인딩된 채널을 유일한 인수로 받아야 합니다.

생성된 작업에 대한 참조가 필요하면 키워드 인수 `taskref`를 통해 `Ref{Task}` 객체를 전달하십시오.

`spawn=true`인 경우, `func`에 대해 생성된 `Task`는 다른 스레드에서 병렬로 예약될 수 있으며, 이는 [`Threads.@spawn`](@ref)를 통해 작업을 생성하는 것과 동등합니다.

`spawn=true`이고 `threadpool` 인수가 설정되지 않은 경우 기본값은 `:default`입니다.

`threadpool` 인수가 설정된 경우(`:default` 또는 `:interactive`), 이는 `spawn=true`를 의미하며 새 작업이 지정된 스레드 풀에 생성됩니다.

`Channel`을 반환합니다.

# 예제

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

생성된 작업 참조하기:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    `spawn=` 매개변수는 Julia 1.3에서 추가되었습니다. 이 생성자는 Julia 1.3에서 추가되었습니다. 이전 버전의 Julia에서는 채널이 키워드 인수를 사용하여 `size`와 `T`를 설정했지만, 이러한 생성자는 더 이상 사용되지 않습니다.


!!! compat "Julia 1.9"
    `threadpool=` 인수는 Julia 1.9에서 추가되었습니다.


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```

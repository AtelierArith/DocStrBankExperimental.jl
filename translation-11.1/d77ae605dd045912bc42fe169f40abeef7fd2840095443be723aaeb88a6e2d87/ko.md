```
Threads.threadid() -> Int
```

현재 실행 중인 스레드의 ID 번호를 가져옵니다. 마스터 스레드는 ID `1`을 가집니다.

# 예제

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! note
    작업이 양보할 경우 작업이 실행되는 스레드는 변경될 수 있으며, 이는 [`Task Migration`](@ref man-task-migration)으로 알려져 있습니다. 이러한 이유로 대부분의 경우 `threadid()`를 사용하여 버퍼 또는 상태 객체의 벡터에 인덱싱하는 것은 안전하지 않습니다.


```
Threads.@spawn [:default|:interactive] expr
```

[`Task`](@ref)를 생성하고 지정된 스레드 풀에서 사용 가능한 스레드에서 실행되도록 [`schedule`](@ref)합니다(`:default`가 지정되지 않은 경우). 작업은 스레드가 사용 가능해지면 해당 스레드에 할당됩니다. 작업이 완료될 때까지 기다리려면 이 매크로의 결과에 대해 [`wait`](@ref)를 호출하거나, [`fetch`](@ref)를 호출하여 기다린 후 반환 값을 얻습니다.

값은 `$`를 통해 `@spawn`에 삽입될 수 있으며, 이는 값을 생성된 기본 클로저에 직접 복사합니다. 이를 통해 변수의 *값*을 삽입할 수 있으며, 현재 작업에서 변수의 값 변경으로부터 비동기 코드를 격리할 수 있습니다.

!!! note
    작업이 실행되는 스레드는 작업이 양보할 경우 변경될 수 있으므로, `threadid()`는 작업에 대해 상수로 취급해서는 안 됩니다. [`Task Migration`](@ref man-task-migration) 및 더 넓은 [multi-threading](@ref man-multithreading) 매뉴얼에서 추가적인 중요한 주의 사항을 참조하십시오. [threadpools](@ref man-threadpools) 장도 참조하십시오.


!!! compat "Julia 1.3"
    이 매크로는 Julia 1.3부터 사용할 수 있습니다.


!!! compat "Julia 1.4"
    `$`를 통한 값의 인터폴레이션은 Julia 1.4부터 사용할 수 있습니다.


!!! compat "Julia 1.9"
    스레드 풀은 Julia 1.9부터 지정할 수 있습니다.


# 예제

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```

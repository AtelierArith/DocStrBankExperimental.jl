```
bind(chnl::Channel, task::Task)
```

`chnl`의 생명주기를 작업에 연결합니다. `Channel` `chnl`은 작업이 종료될 때 자동으로 닫힙니다. 작업에서 발생한 모든 uncaught 예외는 `chnl`의 모든 대기자에게 전파됩니다.

`chnl` 객체는 작업 종료와 관계없이 명시적으로 닫을 수 있습니다. 종료된 작업은 이미 닫힌 `Channel` 객체에 영향을 미치지 않습니다.

하나의 채널이 여러 작업에 바인딩될 때, 가장 먼저 종료된 작업이 채널을 닫습니다. 여러 채널이 동일한 작업에 바인딩될 때, 작업의 종료는 모든 바인딩된 채널을 닫습니다.

# 예제

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
ERROR: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```

```
wait(c::Channel)
```

`Channel` [`isready`](@ref)가 될 때까지 블록합니다.

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # 작업은 채널이 준비되지 않았기 때문에 블록됨
false

julia> put!(c, 1);

julia> istaskdone(task)  # 작업이 이제 언블록됨
true
```

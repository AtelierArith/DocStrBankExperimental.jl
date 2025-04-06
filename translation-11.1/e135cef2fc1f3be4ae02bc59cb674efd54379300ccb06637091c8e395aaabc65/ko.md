```
isready(c::Channel)
```

채널이 [`Channel`](@ref)에 값이 저장되어 있는지 여부를 결정합니다. 즉시 반환되며, 블록하지 않습니다.

버퍼가 없는 채널의 경우, [`put!`](@ref)를 기다리고 있는 작업이 있는 경우 `true`를 반환합니다.

# 예제

버퍼가 있는 채널:

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

버퍼가 없는 채널:

```jldoctest
julia> c = Channel();

julia> isready(c)  # 값을 넣으려고 대기 중인 작업이 없음!
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # put! 작업을 스케줄링합니다.

julia> isready(c)
true
```

```
take!(c::Channel)
```

채널(`Channel`)에서 값을 제거하고 반환합니다. 데이터가 사용 가능할 때까지 블록됩니다. 버퍼가 없는 채널의 경우, 다른 작업이 [`put!`](@ref)를 수행할 때까지 블록됩니다.

# 예제

버퍼가 있는 채널:

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

버퍼가 없는 채널:

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```

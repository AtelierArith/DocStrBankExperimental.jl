```
closewrite(stream)
```

전체 이중 방향 I/O 스트림의 쓰기 절반을 종료합니다. 먼저 [`flush`](@ref)를 수행합니다. 다른 쪽에 더 이상 기본 파일에 데이터가 쓰이지 않을 것임을 알립니다. 이는 모든 IO 유형에서 지원되지 않습니다.

구현된 경우, `closewrite`는 차단될 `read` 또는 `eof` 호출이 EOF를 던지거나 각각 true를 반환하도록 합니다. 스트림이 이미 닫혀 있는 경우, 이는 항등적입니다.

# 예제

```jldoctest
julia> io = Base.BufferStream(); # 이 작업은 결코 차단되지 않으므로 같은 작업에서 읽고 쓸 수 있습니다.

julia> write(io, "request");

julia> # 여기서 `read(io)`를 호출하면 영원히 차단됩니다.

julia> closewrite(io);

julia> read(io, String)
"request"
```

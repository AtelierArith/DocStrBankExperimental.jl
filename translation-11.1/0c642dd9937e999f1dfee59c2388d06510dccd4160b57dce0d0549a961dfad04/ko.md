```
isopen(object) -> Bool
```

객체(예: 스트림 또는 타이머)가 아직 닫히지 않았는지 확인합니다. 객체가 닫히면 새로운 이벤트를 생성하지 않습니다. 그러나 닫힌 스트림은 여전히 버퍼에 읽을 데이터가 있을 수 있으므로, [`eof`](@ref)를 사용하여 데이터를 읽을 수 있는지 확인하십시오. `FileWatching` 패키지를 사용하여 스트림이 쓰기 가능하거나 읽기 가능할 때 알림을 받을 수 있습니다.

# 예제

```jldoctest
julia> io = open("my_file.txt", "w+");

julia> isopen(io)
true

julia> close(io)

julia> isopen(io)
false
```

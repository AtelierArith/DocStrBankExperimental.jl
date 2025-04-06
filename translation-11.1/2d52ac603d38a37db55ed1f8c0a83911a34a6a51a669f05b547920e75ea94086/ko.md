```
eof(stream) -> Bool
```

I/O 스트림이 파일 끝에 도달했는지 테스트합니다. 스트림이 아직 소진되지 않았다면, 이 함수는 필요할 경우 더 많은 데이터를 기다리기 위해 블록됩니다. 그리고 나서 `false`를 반환합니다. 따라서 `eof`가 `false`를 반환한 후에는 항상 한 바이트를 읽는 것이 안전합니다. `eof`는 버퍼링된 데이터가 여전히 사용 가능할 때는 `false`를 반환하며, 연결의 원격 끝이 닫혀 있어도 마찬가지입니다.

# 예제

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```

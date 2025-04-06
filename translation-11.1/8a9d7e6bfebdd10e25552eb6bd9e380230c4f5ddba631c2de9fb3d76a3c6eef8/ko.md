```
deserialize(stream)
```

[`serialize`](@ref)로 작성된 값을 읽습니다. `deserialize`는 `stream`에서 읽은 이진 데이터가 올바르며 [`serialize`](@ref)의 호환 가능한 구현에 의해 직렬화되었다고 가정합니다. `deserialize`는 단순성과 성능을 위해 설계되었으며, 읽은 데이터의 유효성을 검사하지 않습니다. 잘못된 데이터는 프로세스 종료를 초래할 수 있습니다. 호출자는 `stream`에서 읽은 데이터의 무결성과 정확성을 보장해야 합니다.

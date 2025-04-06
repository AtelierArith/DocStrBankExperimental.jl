```
isfieldatomic(t::DataType, s::Union{Int,Symbol}) -> Bool
```

주어진 타입 `t`에서 필드 `s`가 `@atomic`으로 선언되었는지 여부를 결정합니다.

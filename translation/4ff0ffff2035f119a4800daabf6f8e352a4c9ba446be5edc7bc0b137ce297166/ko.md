```
estate::EscapeState
```

인수와 SSA 값을 [`EscapeInfo`](@ref)로 표현된 탈출 정보에 매핑하는 확장 격자입니다. SSA IR 요소 `x`에 부과된 탈출 정보는 `estate[x]`를 통해 검색할 수 있습니다.

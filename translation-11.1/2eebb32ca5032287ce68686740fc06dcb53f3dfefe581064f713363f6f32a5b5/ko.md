```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

실행 컨텍스트에 대한 포인터(일반적으로 `backtrace` 호출로 생성됨)를 주면 스택 프레임 컨텍스트 정보를 조회합니다. 해당 시점에서 인라인된 모든 함수에 대한 프레임 정보 배열을 반환하며, 가장 안쪽 함수가 먼저 나옵니다.

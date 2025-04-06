```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

메모리 객체와 오프셋 인덱스(1부터 시작)로 `GenericMemoryRef`를 생성합니다. 이 인덱스는 음수일 수도 있습니다. 이는 항상 유효한 객체를 반환하며, 불가능할 경우 오류를 발생시킵니다(인덱스가 기본 메모리의 경계를 넘어서는 이동을 초래할 경우).

```
Base.datatype_haspadding(dt::DataType) -> Bool
```

이 타입의 인스턴스 필드가 메모리에 패딩 비트 없이 포장되어 있는지 여부를 반환합니다(패딩 비트는 구조체 필드에 적용될 때 동등성 테스트에 고유하게 영향을 미치지 않는 비트로 정의됨). `isconcretetype`에 대해 호출할 수 있습니다.

```
Base.datatype_alignment(dt::DataType) -> Int
```

이 유형의 인스턴스에 대한 메모리 할당 최소 정렬입니다. `isconcretetype`에 대해 호출할 수 있지만, Memory의 경우 전체 객체가 아닌 요소의 정렬을 제공합니다.

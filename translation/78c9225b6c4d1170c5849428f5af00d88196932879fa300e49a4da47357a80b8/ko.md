```
Base.datatype_pointerfree(dt::DataType) -> Bool
```

이 타입의 인스턴스가 gc-관리 메모리에 대한 참조를 포함할 수 있는지 여부를 반환합니다. `isconcretetype`에 대해 호출할 수 있습니다.

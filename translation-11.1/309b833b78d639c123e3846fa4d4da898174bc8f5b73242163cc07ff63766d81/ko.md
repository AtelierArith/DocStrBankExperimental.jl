```
record(ts::AbstractTestSet, res::Result)
```

테스트 세트에 결과를 기록합니다. 이 함수는 포함된 `@test` 매크로가 완료될 때마다 `@testset` 인프라에 의해 호출되며, 테스트 결과(이는 `Error`일 수 있음)를 받습니다. 테스트 블록 내에서 `@test` 컨텍스트 외부에서 예외가 발생하면 `Error`와 함께 호출됩니다.

```
Test.Error <: Test.Result
```

테스트 조건을 예외로 인해 평가할 수 없거나 [`Bool`](@ref) 이외의 다른 것으로 평가되었습니다. `@test_broken`의 경우, 예상치 못한 `Pass` `Result`가 발생했음을 나타내는 데 사용됩니다.

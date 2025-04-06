```
fetch(t::Task)
```

[`Task`](@ref)가 완료될 때까지 기다린 후, 그 결과 값을 반환합니다. 작업이 예외로 실패하면 실패한 작업을 감싸는 [`TaskFailedException`](@ref)가 발생합니다.

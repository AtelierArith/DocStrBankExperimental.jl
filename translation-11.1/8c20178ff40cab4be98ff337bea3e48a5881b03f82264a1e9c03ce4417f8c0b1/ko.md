```
withenv(f, kv::Pair...)
```

`f`를 임시로 수정된 환경에서 실행합니다( `setenv`와 같이 교체되지 않음) `"var"=>val` 인수 `kv`가 0개 이상입니다. `withenv`는 일반적으로 `withenv(kv...) do ... end` 구문을 통해 사용됩니다. `nothing` 값을 사용하여 환경 변수를 임시로 해제할 수 있습니다(설정된 경우). `withenv`가 반환되면 원래 환경이 복원됩니다.

!!! 경고     환경을 변경하는 것은 스레드 안전하지 않습니다. 부모 프로세스와 다른 환경에서 외부 명령을 실행하려면 `withenv`보다 [`addenv`](@ref)를 사용하는 것이 좋습니다.

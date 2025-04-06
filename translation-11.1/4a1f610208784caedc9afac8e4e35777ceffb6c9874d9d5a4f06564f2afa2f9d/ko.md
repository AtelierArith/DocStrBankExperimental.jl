```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

현재 처리 중인 예외의 스택을 가져옵니다. 중첩된 catch 블록이 있는 경우, 현재 예외가 여러 개일 수 있으며, 이 경우 가장 최근에 발생한 예외가 스택의 마지막에 위치합니다. 스택은 `ExceptionStack`으로 반환되며, 이는 이름이 있는 튜플 `(exception,backtrace)`의 AbstractVector입니다. `backtrace`가 false인 경우, 각 쌍의 백트레이스는 `nothing`으로 설정됩니다.

명시적으로 `task`를 전달하면 임의의 작업에서 현재 예외 스택을 반환합니다. 이는 처리되지 않은 예외로 인해 실패한 작업을 검사하는 데 유용합니다.

!!! compat "Julia 1.7"
    이 함수는 Julia 1.1–1.6에서 실험적 이름 `catch_stack()`으로 불렸으며, 반환 유형은 일반적인 튜플의 Vector였습니다.


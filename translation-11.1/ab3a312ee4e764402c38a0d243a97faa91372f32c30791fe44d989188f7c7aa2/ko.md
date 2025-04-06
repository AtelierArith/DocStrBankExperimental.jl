```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

`@threadcall` 매크로는 [`ccall`](@ref)와 같은 방식으로 호출되지만, 다른 스레드에서 작업을 수행합니다. 이는 현재 `julia` 스레드가 차단되지 않도록 차단 C 함수를 호출하고자 할 때 유용합니다. 동시성은 libuv 스레드 풀의 크기에 의해 제한되며, 기본값은 4개의 스레드이지만 `UV_THREADPOOL_SIZE` 환경 변수를 설정하고 `julia` 프로세스를 재시작하여 늘릴 수 있습니다.

호출된 함수는 절대 Julia로 다시 호출해서는 안 됩니다.

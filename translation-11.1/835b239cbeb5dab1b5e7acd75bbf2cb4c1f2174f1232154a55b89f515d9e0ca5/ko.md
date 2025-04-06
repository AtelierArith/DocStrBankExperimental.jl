```
exit_on_sigint(on::Bool)
```

`exit_on_sigint` 플래그를 줄리아 런타임에 설정합니다. `false`인 경우, Ctrl-C (SIGINT)는 `try` 블록에서 [`InterruptException`](@ref)으로 캡처할 수 있습니다. 이는 REPL의 기본 동작이며, `-e` 및 `-E`를 통해 실행되는 모든 코드와 `-i` 옵션으로 실행되는 줄리아 스크립트에서도 마찬가지입니다.

`true`인 경우, Ctrl-C에 의해 `InterruptException`이 발생하지 않습니다. 이러한 이벤트에서 코드를 실행하려면 [`atexit`](@ref)가 필요합니다. 이는 `-i` 옵션 없이 실행되는 줄리아 스크립트의 기본 동작입니다.

!!! compat "Julia 1.5"
    함수 `exit_on_sigint`는 최소한 줄리아 1.5가 필요합니다.


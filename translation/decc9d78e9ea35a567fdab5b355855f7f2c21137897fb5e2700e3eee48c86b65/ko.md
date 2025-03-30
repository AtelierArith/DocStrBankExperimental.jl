```
redirect_stderr([stream]) -> stream
```

[`stderr`](@ref)에 대한 [`redirect_stdout`](@ref)와 유사합니다.

!!! note
    `stream`은 `IOStream`, `TTY`, [`Pipe`](@ref), 소켓 또는 `devnull`과 같은 호환 가능한 객체여야 합니다.


또한 [`redirect_stdio`](@ref)를 참조하십시오.

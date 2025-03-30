```
redirect_stdin([stream]) -> stream
```

[`redirect_stdout`](@ref)와 유사하지만 [`stdin`](@ref)에 대한 것입니다. 스트림의 방향이 반전된다는 점에 유의하세요.

!!! note
    `stream`은 `IOStream`, `TTY`, [`Pipe`](@ref), 소켓 또는 `devnull`과 같은 호환 가능한 객체여야 합니다.


또한 [`redirect_stdio`](@ref)를 참조하세요.

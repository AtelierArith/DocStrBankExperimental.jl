```
redirect_stdout([stream]) -> stream
```

모든 C 및 Julia 수준의 [`stdout`](@ref) 출력을 리디렉션할 파이프를 생성합니다. 파이프의 끝을 나타내는 스트림을 반환합니다. 이제 [`stdout`](@ref)에 작성된 데이터는 파이프의 `rd` 끝에서 읽을 수 있습니다.

!!! note
    `stream`은 `IOStream`, `TTY`, [`Pipe`](@ref), 소켓 또는 `devnull`과 같은 호환 가능한 객체여야 합니다.


자세한 내용은 [`redirect_stdio`](@ref)를 참조하십시오.

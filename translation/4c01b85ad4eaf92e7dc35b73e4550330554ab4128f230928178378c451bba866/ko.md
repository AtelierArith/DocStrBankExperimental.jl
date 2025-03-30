```
InterruptException()
```

프로세스가 터미널 인터럽트 (CTRL+C)에 의해 중지되었습니다.

`-i` (대화형) 옵션 없이 시작된 Julia 스크립트에서는 기본적으로 `InterruptException`이 발생하지 않음을 유의하십시오. 스크립트에서 [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint)를 호출하면 REPL의 동작을 복구할 수 있습니다. 또는 Julia 스크립트를 다음과 같이 시작할 수 있습니다.

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

이렇게 하면 실행 중에 CTRL+C에 의해 `InterruptException`이 발생하게 됩니다.

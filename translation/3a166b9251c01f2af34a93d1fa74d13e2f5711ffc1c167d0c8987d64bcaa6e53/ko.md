```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

파일이나 디렉토리를 편집하며, 선택적으로 파일을 편집할 줄 번호를 제공할 수 있습니다. 편집기를 종료하면 `julia` 프롬프트로 돌아갑니다. 편집기는 환경 변수로 `JULIA_EDITOR`, `VISUAL` 또는 `EDITOR`를 설정하여 변경할 수 있습니다.

!!! compat "Julia 1.9"
    `column` 인자는 최소한 Julia 1.9가 필요합니다.


또한 [`InteractiveUtils.define_editor`](@ref)를 참조하세요.

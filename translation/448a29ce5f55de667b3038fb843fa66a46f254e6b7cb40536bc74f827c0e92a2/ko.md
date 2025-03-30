```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

문자열 또는 스트림 `x`를 파싱하고 결과 테이블(사전)을 반환합니다. 실패 시 [`ParserError`](@ref)를 발생시킵니다.

또한 [`TOML.tryparse`](@ref)를 참조하세요.

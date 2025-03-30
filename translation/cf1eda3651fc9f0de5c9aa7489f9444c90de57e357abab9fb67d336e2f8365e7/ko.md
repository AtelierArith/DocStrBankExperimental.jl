```
tryparse(x::Union{AbstractString, IO})
tryparse(p::Parser, x::Union{AbstractString, IO})
```

문자열 또는 스트림 `x`를 파싱하고 결과 테이블(사전)을 반환합니다. 실패할 경우 [`ParserError`](@ref)를 반환합니다.

또한 [`TOML.parse`](@ref)를 참조하십시오.

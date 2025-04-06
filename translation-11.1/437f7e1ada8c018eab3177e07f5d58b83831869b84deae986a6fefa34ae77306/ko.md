```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

파일 `f`를 파싱하고 결과 테이블(사전)을 반환합니다. 실패 시 [`ParserError`](@ref)를 발생시킵니다.

또한 [`TOML.tryparsefile`](@ref)를 참조하세요.

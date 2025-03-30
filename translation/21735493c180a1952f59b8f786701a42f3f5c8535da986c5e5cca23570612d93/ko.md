```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

`ir`에서 탈출 정보를 분석합니다:

  * `nargs`: 분석된 호출의 실제 인수 수
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}`: 캐시된 인수 탈출 정보를 검색합니다.

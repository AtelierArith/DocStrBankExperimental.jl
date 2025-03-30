```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

`pattern`을 포함하는 항목에 대한 사용 가능한 문서 문자열을 검색합니다.

`pattern`이 문자열인 경우 대소문자는 무시됩니다. 결과는 `io`에 인쇄됩니다.

`apropos`는 REPL의 도움말 모드에서 쿼리를 큰따옴표로 감싸 호출할 수 있습니다:

```
help?> "pattern"
```

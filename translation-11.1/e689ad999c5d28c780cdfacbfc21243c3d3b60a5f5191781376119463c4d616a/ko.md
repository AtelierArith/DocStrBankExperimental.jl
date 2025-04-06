```
latex([io::IO], md)
```

Markdown 객체 `md`의 내용을 LaTeX 형식으로 출력합니다. (선택적) `io` 스트림에 쓰거나 문자열로 반환합니다.

대신 `show(io, "text/latex", md)` 또는 `repr("text/latex", md)`를 사용할 수 있습니다.

# 예시

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```

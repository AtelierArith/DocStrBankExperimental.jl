```
html([io::IO], md)
```

Markdown 객체 `md`의 내용을 HTML 형식으로 출력합니다. (선택적) `io` 스트림에 쓰거나 문자열로 반환합니다.

대안으로 `show(io, "text/html", md)` 또는 `repr("text/html", md)`를 사용할 수 있으며, 이들은 출력 결과를 `<div class="markdown"> ... </div>` 요소로 감싼다는 점에서 다릅니다.

# 예시

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```

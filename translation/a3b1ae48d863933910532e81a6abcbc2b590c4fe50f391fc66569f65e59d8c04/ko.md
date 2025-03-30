```
@doc_str -> MD
```

주어진 문자열을 Markdown 텍스트로 파싱하고, 라인 및 모듈 정보를 추가한 후 해당하는 [`MD`](@ref) 객체를 반환합니다.

`@doc_str`는 [`Base.Docs`](@ref) 모듈과 함께 사용할 수 있습니다. 더 많은 정보는 [문서화](@ref man-documentation) 매뉴얼 섹션을 참조하십시오.

# 예제

```
julia> s = doc"f(x) = 2*x"
  f(x) = 2*x

julia> typeof(s)
Markdown.MD

```

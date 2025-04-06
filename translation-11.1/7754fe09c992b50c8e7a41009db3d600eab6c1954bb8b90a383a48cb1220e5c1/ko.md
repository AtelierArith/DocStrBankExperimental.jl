```
@md_str -> MD
```

주어진 문자열을 Markdown 텍스트로 파싱하고 해당하는 [`MD`](@ref) 객체를 반환합니다.

# 예시

```jldoctest
julia> s = md"# Hello, world!"
  Hello, world!
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```

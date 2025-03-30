```
tryparse(::Type{SimpleColor}, rgb::String)
```

`rgb`를 `SimpleColor`로 파싱하려고 시도합니다. `rgb`가 `#`로 시작하고 길이가 7인 경우, `RGBTuple` 기반의 `SimpleColor`로 변환됩니다. `rgb`가 `a`-`z`로 시작하는 경우, `rgb`는 색상 이름으로 해석되어 `Symbol` 기반의 `SimpleColor`로 변환됩니다.

그렇지 않으면 `nothing`이 반환됩니다.

# 예제

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```

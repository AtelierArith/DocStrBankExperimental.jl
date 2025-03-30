```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

`xs`를 기호 또는 정수로 지정된 색상으로 인쇄하며, 선택적으로 굵게 인쇄합니다.

키워드 `color`는 `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white`, 또는 `:yellow` 또는 0에서 255 사이의 정수를 포함할 수 있습니다. 모든 터미널이 256색을 지원하는 것은 아닙니다.

키워드 `bold=true`, `italic=true`, `underline=true`, `blink=true`는 자명합니다. 키워드 `reverse=true`는 전경색과 배경색이 교환된 상태로 인쇄하며, `hidden=true`는 터미널에서 보이지 않지만 여전히 복사할 수 있어야 합니다. 이러한 속성은 어떤 조합으로도 사용할 수 있습니다.

또한 [`print`](@ref), [`println`](@ref), [`show`](@ref)를 참조하십시오.

!!! note
    모든 터미널이 이탤릭 출력을 지원하는 것은 아닙니다. 일부 터미널은 이탤릭을 반전 또는 깜박임으로 해석합니다.


!!! compat "Julia 1.7"
    `color`와 `bold`를 제외한 키워드는 Julia 1.7에서 추가되었습니다.


!!! compat "Julia 1.10"
    이탤릭 출력에 대한 지원이 Julia 1.10에서 추가되었습니다.


```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

`x`를 디스플레이 스택에서 가장 적합한 디스플레이를 사용하여 표시합니다. 일반적으로 `x`에 대해 지원되는 가장 풍부한 멀티미디어 출력을 사용하며, 기본 텍스트 [`stdout`](@ref) 출력을 대체로 사용합니다. `display(d, x)` 변형은 주어진 디스플레이 `d`에서만 `x`를 표시하려고 시도하며, `d`가 이 유형의 객체를 표시할 수 없는 경우 [`MethodError`](@ref)를 발생시킵니다.

일반적으로 `display` 출력이 `stdout`로 간주된다고 가정할 수 없습니다 (예: [`print(x)`](@ref) 또는 [`show(x)`](@ref)와는 다르게). 예를 들어, `display(x)`는 이미지가 있는 별도의 창을 열 수 있습니다. `display(x)`는 "현재 출력 장치에 대해 가능한 최상의 방법으로 `x`를 표시하라"는 의미입니다. `stdout`로 보장된 REPL과 같은 텍스트 출력을 원한다면 대신 [`show(stdout, "text/plain", x)`](@ref)를 사용하십시오.

`mime` 인수(예: `"image/png"`와 같은 MIME 유형 문자열)를 가진 두 가지 변형도 있으며, 요청된 MIME 유형 *만* 사용하여 `x`를 표시하려고 시도하며, 이 유형이 디스플레이 또는 `x`에 의해 지원되지 않는 경우 `MethodError`를 발생시킵니다. 이러한 변형을 사용하면 `x::AbstractString`(text/html 또는 application/postscript와 같은 텍스트 기반 저장을 위한 MIME 유형) 또는 `x::Vector{UInt8}`(이진 MIME 유형을 위한)으로 요청된 MIME 유형의 "원시" 데이터를 제공할 수도 있습니다.

유형의 인스턴스가 표시되는 방식을 사용자 정의하려면, 매뉴얼의 [사용자 정의 예쁘게 출력하기](@ref man-custom-pretty-printing) 섹션에 설명된 대로 `display`가 아닌 [`show`](@ref)를 오버로드하십시오.

```
repr(mime, x; context=nothing)
```

요청된 `mime` 유형으로 `x`의 표현을 포함하는 `AbstractString` 또는 `Vector{UInt8}`를 반환합니다. 이는 [`show(io, mime, x)`](@ref)에서 작성된 대로 반환되며, 적절한 `show`가 없으면 [`MethodError`](@ref)를 발생시킵니다. 텍스트 표현이 있는 MIME 유형(예: `"text/html"` 또는 `"application/postscript"`)의 경우 `AbstractString`이 반환되며, 이진 데이터는 `Vector{UInt8}`로 반환됩니다. (`istextmime(mime)` 함수는 주어진 `mime` 유형을 Julia가 텍스트로 처리하는지 여부를 반환합니다.)

선택적 키워드 인수 `context`는 `:key=>value` 쌍 또는 `show`에 전달된 I/O 스트림에 사용되는 속성을 가진 `IO` 또는 [`IOContext`](@ref) 객체로 설정할 수 있습니다.

특별한 경우로, `x`가 `AbstractString`(텍스트 MIME 유형의 경우) 또는 `Vector{UInt8}`(이진 MIME 유형의 경우)인 경우, `repr` 함수는 `x`가 이미 요청된 `mime` 형식에 있다고 가정하고 단순히 `x`를 반환합니다. 이 특별한 경우는 `"text/plain"` MIME 유형에는 적용되지 않습니다. 이는 원시 데이터를 `display(m::MIME, x)`에 전달할 수 있도록 유용합니다.

특히, `repr("text/plain", x)`는 일반적으로 인간 소비를 위해 설계된 `x`의 "예쁘게 인쇄된" 버전입니다. 대신 [`show(x)`](@ref)에 해당하는 문자열을 반환하려면 [`repr(x)`](@ref)를 참조하세요. 이는 `x`의 값이 Julia에 입력될 때 더 가까운 형태일 수 있습니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```

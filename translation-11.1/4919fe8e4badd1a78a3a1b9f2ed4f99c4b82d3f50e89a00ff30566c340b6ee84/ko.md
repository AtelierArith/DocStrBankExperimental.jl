```
stringmime(mime, x; context=nothing)
```

요청된 `mime` 유형으로 `x`의 표현을 포함하는 `AbstractString`을 반환합니다. 이는 [`repr(mime, x)`](@ref)와 유사하지만 이진 데이터는 ASCII 문자열로 base64 인코딩됩니다.

선택적 키워드 인수 `context`는 `:key=>value` 쌍 또는 [`show`](@ref)에 전달되는 I/O 스트림에 사용되는 속성을 가진 `IO` 또는 [`IOContext`](@ref) 객체로 설정할 수 있습니다.

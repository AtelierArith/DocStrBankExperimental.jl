```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

[`write`](@ref)와 유사한 함수 `writefunc`가 첫 번째 인수로 I/O 스트림을 받는 경우, `base64encode(writefunc, args...)`는 `writefunc`를 호출하여 `args...`를 base64로 인코딩된 문자열로 작성하고, 그 문자열을 반환합니다. `base64encode(args...)`는 `base64encode(write, args...)`와 동일합니다: 이는 표준 [`write`](@ref) 함수를 사용하여 인수를 바이트로 변환하고 base64로 인코딩된 문자열을 반환합니다.

선택적 키워드 인수 `context`는 `:key=>value` 쌍 또는 `IO` 또는 [`IOContext`](@ref) 객체로 설정할 수 있으며, 이 객체의 속성은 `writefunc` 또는 `write`에 전달되는 I/O 스트림에 사용됩니다.

또한 [`base64decode`](@ref)를 참조하십시오.

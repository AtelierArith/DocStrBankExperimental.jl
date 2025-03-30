```
unmark(s::IO)
```

스트림 `s`에서 마크를 제거합니다. 스트림이 마크되었으면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

또한 [`mark`](@ref), [`reset`](@ref), [`ismarked`](@ref)를 참조하세요.

```
CFunction 구조체
```

`@cfunction`에서 첫 번째 인수가 '$'로 주석 처리된 경우 반환 값에 대한 가비지 수집 핸들입니다. 모든 `cfunction` 핸들과 마찬가지로 `ccall`에 `Ptr{Cvoid}`로 전달되어야 하며, 호출 지점에서 자동으로 적절한 유형으로 변환됩니다.

[`@cfunction`](@ref)를 참조하세요.

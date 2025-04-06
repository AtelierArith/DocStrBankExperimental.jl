```
mktemp(f::Function, parent=tempdir())
```

함수 `f`를 [`mktemp(parent)`](@ref)의 결과에 적용하고 완료 후 임시 파일을 제거합니다.

참고: [`mktempdir`](@ref).

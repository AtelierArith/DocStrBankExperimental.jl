```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

함수 `f`를 [`mktempdir(parent; prefix)`](@ref)의 결과에 적용하고 완료 후 임시 디렉토리와 그 모든 내용을 제거합니다.

참고: [`mktemp`](@ref), [`mkdir`](@ref).

!!! compat "Julia 1.2"
    `prefix` 키워드 인자는 Julia 1.2에서 추가되었습니다.


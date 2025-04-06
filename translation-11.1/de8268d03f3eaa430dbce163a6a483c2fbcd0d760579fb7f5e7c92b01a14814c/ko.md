```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

C 표준 라이브러리에서 `realloc`을 호출합니다.

[`malloc`](@ref)에서 원래 얻은 메모리에서만 사용해야 한다는 경고는 [`free`](@ref) 문서에서 확인하십시오.

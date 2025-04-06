```
nextfloat(x::AbstractFloat, n::Integer)
```

`n`이 0 이상인 경우 `x`에 `nextfloat`을 `n`번 반복 적용한 결과, 또는 `n`이 0 미만인 경우 [`prevfloat`](@ref)을 `-n`번 적용한 결과입니다.

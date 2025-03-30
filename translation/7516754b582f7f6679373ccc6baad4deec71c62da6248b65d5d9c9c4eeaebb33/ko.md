```
LoadError(file::AbstractString, line::Int, error)
```

파일을 [`include`](@ref Base.include), [`require`](@ref Base.require), 또는 [`using`](@ref) 하는 동안 오류가 발생했습니다. 오류 세부정보는 `.error` 필드에서 확인할 수 있어야 합니다.

!!! compat "Julia 1.7"
    Julia 1.7부터 `@macroexpand`, `@macroexpand1`, 및 `macroexpand`에 의해 LoadErrors가 더 이상 발생하지 않습니다.


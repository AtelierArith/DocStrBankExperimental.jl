```
LoadError(file::AbstractString, line::Int, error)
```

Bir dosya [`include`](@ref Base.include) edilirken, [`require`](@ref Base.require) edilirken veya [`using`](@ref) yapılırken bir hata oluştu. Hata ayrıntıları `.error` alanında mevcut olmalıdır.

!!! compat "Julia 1.7"
    `@macroexpand`, `@macroexpand1` ve `macroexpand` tarafından artık LoadErrors üretilmiyor, bu Julia 1.7 itibarıyla geçerlidir.


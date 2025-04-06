```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

类似于 [`dlopen`](@ref)，但返回 `C_NULL` 而不是引发错误。该方法现在已被弃用，建议使用 `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)`。

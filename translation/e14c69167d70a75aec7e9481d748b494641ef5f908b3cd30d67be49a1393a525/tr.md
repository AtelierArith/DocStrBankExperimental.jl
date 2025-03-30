```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

[`dlopen`](@ref) ile benzer, ancak hataları yükseltmek yerine `C_NULL` döner. Bu yöntem artık `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)` lehine kullanımdan kaldırılmıştır.

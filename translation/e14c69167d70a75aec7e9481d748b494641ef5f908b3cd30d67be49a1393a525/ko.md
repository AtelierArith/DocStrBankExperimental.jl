```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

[`dlopen`](@ref)와 유사하지만, 오류를 발생시키는 대신 `C_NULL`을 반환합니다. 이 메서드는 이제 `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)`를 선호하여 사용하지 않도록 권장됩니다.

```
Some{T}
```

`Union{Some{T}, Nothing}` içinde bir değer yokluğunu ([`nothing`](@ref)) ve bir `nothing` değerinin varlığını (yani `Some(nothing)`) ayırt etmek için kullanılan bir sarmalayıcı tür.

Bir `Some` nesnesi tarafından sarılmış değere erişmek için [`something`](@ref) kullanın.

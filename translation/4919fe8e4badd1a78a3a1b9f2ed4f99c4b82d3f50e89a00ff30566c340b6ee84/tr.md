```
stringmime(mime, x; context=nothing)
```

İstenen `mime` türünde `x`'in temsilini içeren bir `AbstractString` döndürür. Bu, ikili verilerin ASCII dizesi olarak base64 kodlandığı [`repr(mime, x)`](@ref) ile benzerdir.

İsteğe bağlı anahtar argümanı `context`, [`show`](@ref) ile geçirilen I/O akışı için kullanılan özelliklere sahip bir `IO` veya [`IOContext`](@ref) nesnesi veya `:key=>value` çiftine ayarlanabilir.

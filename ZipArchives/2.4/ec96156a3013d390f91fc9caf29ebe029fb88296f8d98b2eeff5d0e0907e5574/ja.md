```
zip_readentry(r::ZipReader, i::Union{AbstractString, Integer}, args...; kwargs...)
```

`r`のエントリ`i`の内容を読み取ります。

`i`が文字列の場合、正確に一致する名前の最後のエントリを読み取ります。

`args...; kwargs...`は、エントリ`i`が[`zip_openentry`](@ref)で開かれた後に`read`に渡されます。

`args...`が空または`String`の場合、チェックサムが一致しないとエラーになります。

詳細は[`zip_openentry`](@ref)を参照してください。

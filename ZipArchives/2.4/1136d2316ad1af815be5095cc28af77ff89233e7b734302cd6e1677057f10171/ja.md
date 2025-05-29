```
zip_openentry(r::ZipReader, i::Union{AbstractString, Integer})
zip_openentry(f::Function, r::ZipReader, i::Union{AbstractString, Integer})
```

`r`から読み取り可能なIOとしてエントリ`i`を開きます。

`i`が文字列の場合、正確に一致する名前の最後のエントリを開きます。

読み取りが完了したら、返されたストリームを閉じることを確認してください。doブロックメソッドを使用していない場合は特に注意が必要です。

この関数によって返されるストリームには、一度に1つのスレッドのみがアクセスする必要があります。

[`zip_readentry`](@ref)も参照してください。

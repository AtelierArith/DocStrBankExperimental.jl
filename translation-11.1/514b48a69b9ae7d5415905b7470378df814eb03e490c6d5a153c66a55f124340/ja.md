```
cconvert(T,x)
```

`x`を型`T`としてCコードに渡すための値に変換します。通常は`convert(T, x)`を呼び出すことで行います。

`x`が安全に`T`に変換できない場合、[`convert`](@ref)とは異なり、`cconvert`は`T`とは異なる型のオブジェクトを返すことがありますが、それは[`unsafe_convert`](@ref)が処理するのに適しています。この関数の結果は、[`unsafe_convert`](@ref)の結果が不要になるまで有効である必要があります。これは、`ccall`によってアクセスされるメモリを割り当てるために使用できます。複数のオブジェクトを割り当てる必要がある場合、オブジェクトのタプルを返り値として使用できます。

`convert`も`cconvert`も、Juliaオブジェクトを`Ptr`に変換してはいけません。

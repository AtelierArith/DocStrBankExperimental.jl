```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

[`IOBuffer`](@ref)を使用して、読み取りを行い、追加することで書き込みを行うことができるバッファです。シークやトランケートはサポートされていません。利用可能なコンストラクタについては[`IOBuffer`](@ref)を参照してください。`data`が指定されている場合、データベクター上で操作するための`PipeBuffer`を作成し、基盤となる`Array`が成長できないサイズをオプションで指定します。

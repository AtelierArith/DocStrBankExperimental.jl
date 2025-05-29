```
Message(a::T) where T <: DenseVector
```

配列をバッファとして持つメッセージを作成します（送信用）。注意：[`Message(m::String)`](@ref) と同じ所有権のセマンティクスが適用されます。

通常、`a` は 1D `Array`/`Vector` ですが、Julia 1.11+ では `Memory` も使用できます。

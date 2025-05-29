```
render_params(r::AbstractBlock, params)
```

この関数は、入力パラメータを `r` に消費可能な型にレンダリングします。`params` は数値または `:zero` や `:random` のようなシンボルであることができます。

### 例

```jldoctest; setup=:(using Yao)
julia> collect(render_params(Rx(0.1), :zero))
1-element Vector{Float64}:
 0.0
```

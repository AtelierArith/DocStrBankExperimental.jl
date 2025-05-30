```
tracedist(register1, register2)
```

`register1` と `register2` のトレース距離を返します。

# 定義

トレース距離は次のように定義されます：

$$
\frac{1}{2} || A - B ||_{\rm tr}
$$

値は 0 と 1 の間になります。

### 例

```jldoctest; setup=:(using Yao)
julia> reg1 = uniform_state(3);

julia> reg2 = zero_state(3);

julia> tracedist(reg1, reg2)
0.9354143466934852
```

### 参考文献

  * https://en.wikipedia.org/wiki/Trace_distance

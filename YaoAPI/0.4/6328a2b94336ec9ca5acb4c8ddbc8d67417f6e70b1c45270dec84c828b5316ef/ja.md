```
print_block(io, block)
```

ブロックがテキストとしてどのように印刷されるかを1行で定義します。

### 例

```jldoctest; setup=:(using Yao)
julia> print_block(stdout, X)
X

julia> print_block(stdout, put(2, 1=>X))
put on (1)
```

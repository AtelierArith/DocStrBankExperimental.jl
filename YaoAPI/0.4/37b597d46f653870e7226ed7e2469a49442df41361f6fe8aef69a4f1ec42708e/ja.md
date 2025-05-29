```
chcontent(x, blk) -> block
```

`x`の類似ブロックを作成し、その内容を`blk`に変更します。

### 例

```jldoctest; setup=:(using Yao)
julia> chcontent(2.0 * X, Y)
[scale: 2.0] Y
```

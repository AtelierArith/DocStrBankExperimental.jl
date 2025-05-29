```
chcontent(x, blk) -> block
```

Create a similar block of `x` and change its content to blk.

### Examples

```jldoctest; setup=:(using Yao)
julia> chcontent(2.0 * X, Y)
[scale: 2.0] Y
```

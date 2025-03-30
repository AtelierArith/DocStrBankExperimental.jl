```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

在一次调用中对多个 `values` 进行水平、垂直和 n 维连接。

此函数用于块矩阵语法。第一个参数指定连接的形状，类似于 `hvcat`，作为元组的元组，或者指定沿每个轴的元素数量的维度，并用于确定输出维度。`dims` 形式性能更佳，当连接操作沿每个轴的元素数量相同时（例如，[a b; c d;;; e f ; g h]）默认使用此形式。`shape` 形式用于沿每个轴的元素数量不平衡时（例如，[a b ; c]）。不平衡语法需要额外的验证开销。`dim` 形式是仅沿一个维度连接的优化。`row_first` 指示 `values` 的排序方式。`shape` 的第一个和第二个元素的含义也根据 `row_first` 进行了交换。

# 示例

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# 构造参数的示例

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = 每行的元素数量 (2, 1, 1)
 _______     _
 3           1 = 每列的元素数量 (3, 1)
 _____________
 4             = 每个 3d 切片的元素数量 (4,)
 _____________
 4             = 每个 4d 切片的元素数量 (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) with `row_first` = true
```

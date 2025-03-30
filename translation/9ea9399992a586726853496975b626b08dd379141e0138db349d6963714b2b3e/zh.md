```
writedlm(f, A, delim='\t'; opts)
```

将 `A`（一个向量、矩阵或可迭代的可迭代行集合）作为文本写入 `f`（可以是文件名字符串或 `IO` 流），使用给定的分隔符 `delim`（默认为制表符，但可以是任何可打印的 Julia 对象，通常是 `Char` 或 `AbstractString`）。

例如，两个长度相同的向量 `x` 和 `y` 可以通过 `writedlm(f, [x y])` 或 `writedlm(f, zip(x, y))` 作为两个制表符分隔的文本列写入 `f`。

# 示例

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```

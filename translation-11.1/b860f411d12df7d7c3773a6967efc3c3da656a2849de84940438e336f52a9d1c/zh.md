```
readdlm(source; options...)
```

列假定由一个或多个空格分隔。行结束符被视为 `\n`。如果所有数据都是数字，结果将是一个数字数组。如果某些元素无法解析为数字，则返回一个包含数字和字符串的异构数组。

# 示例

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end;

julia> readdlm("delim_file.txt")
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```

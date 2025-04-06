```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

从源中读取一个矩阵，每行（由 `eol` 分隔）给出一行，元素由给定的分隔符分隔。源可以是文本文件、流或字节数组。可以通过将映射段的字节数组表示作为源来使用内存映射文件。

如果 `T` 是数值类型，则结果是该类型的数组，任何非数值元素对于浮点类型将为 `NaN`，或为零。其他有用的 `T` 值包括 `String`、`AbstractString` 和 `Any`。

如果 `header` 为 `true`，则第一行数据将被读取为标题，并返回元组 `(data_cells, header_cells)` 而不仅仅是 `data_cells`。

指定 `skipstart` 将忽略输入中的相应数量的初始行。

如果 `skipblanks` 为 `true`，则输入中的空行将被忽略。

如果 `use_mmap` 为 `true`，则指定的 `source` 文件将被内存映射，以便在文件较大时可能加快速度。默认值为 `false`。在 Windows 文件系统上，除非文件仅被读取一次且也不被写入，否则不应将 `use_mmap` 设置为 `true`。存在一些边缘情况，其中操作系统是类 Unix 的，但文件系统是类 Windows 的。

如果 `quotes` 为 `true`，则用双引号（"）字符括起来的列允许包含新行和列分隔符。被引用字段中的双引号字符必须用另一个双引号进行转义。将 `dims` 指定为预期的行和列的元组（包括标题，如果有的话）可能会加快大文件的读取。如果 `comments` 为 `true`，则以 `comment_char` 开头的行以及任何行中跟随 `comment_char` 的文本将被忽略。

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

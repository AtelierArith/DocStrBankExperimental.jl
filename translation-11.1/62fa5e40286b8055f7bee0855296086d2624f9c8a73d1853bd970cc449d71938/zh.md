```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

在`s`中搜索给定的模式`pat`，并用`r`替换每个出现的实例。如果提供了`count`，则最多替换`count`个实例。`pat`可以是单个字符、字符向量或字符集合、字符串或正则表达式。如果`r`是一个函数，则每个出现的实例将被替换为`r(s)`，其中`s`是匹配的子字符串（当`pat`是`AbstractPattern`或`AbstractString`时）或字符（当`pat`是`AbstractChar`或`AbstractChar`的集合时）。如果`pat`是正则表达式并且`r`是一个[`SubstitutionString`](@ref)，则`r`中的捕获组引用将被相应的匹配文本替换。要从字符串中删除`pat`的实例，将`r`设置为空`String`（`""`）。

返回值是替换后的新字符串。如果提供了`io::IO`参数，则转换后的字符串将写入`io`（返回`io`）。 （例如，这可以与[`IOBuffer`](@ref)结合使用，以在原地重用预分配的缓冲区数组。）

可以指定多个模式，它们将同时从左到右应用，因此每个字符只会应用一个模式，并且模式只会应用于输入文本，而不是替换。

!!! compat "Julia 1.7"
    对多个模式的支持需要版本1.7。


!!! compat "Julia 1.10"
    `io::IO`参数需要版本1.10。


# 示例

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```

```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

将`s`中每个单词的首字母大写；如果`strict`为真，则其他字符都转换为小写，否则保持不变。默认情况下，所有非字母字符开始的新图形都被视为单词分隔符；可以通过`wordsep`关键字传递一个谓词来确定哪些字符应被视为单词分隔符。另请参见[`uppercasefirst`](@ref)以仅将`s`中的第一个字符大写。

另请参见[`uppercase`](@ref)，[`lowercase`](@ref)，[`uppercasefirst`](@ref)。

# 示例

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```

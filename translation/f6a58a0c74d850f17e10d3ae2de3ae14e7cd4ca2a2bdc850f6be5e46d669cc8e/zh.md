```
skipchars(predicate, io::IO; linecomment=nothing)
```

推进流 `io`，使得下一个读取的字符将是 `predicate` 返回 `false` 的第一个剩余字符。如果指定了关键字参数 `linecomment`，则从该字符开始到下一行的开始之间的所有字符都将被忽略。

# 示例

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```

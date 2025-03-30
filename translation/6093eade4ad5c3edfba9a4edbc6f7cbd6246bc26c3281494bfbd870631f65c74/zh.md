```
MIME
```

表示标准互联网数据格式的类型。“MIME”代表“多用途互联网邮件扩展”，因为该标准最初用于描述电子邮件消息的多媒体附件。

`MIME` 对象可以作为第二个参数传递给 [`show`](@ref)，以请求以该格式输出。

# 示例

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```

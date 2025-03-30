```
@s_str -> SubstitutionString
```

构造一个替换字符串，用于正则表达式替换。在字符串中，形式为 `\N` 的序列指的是正则表达式中的第 N 个捕获组，而 `\g<groupname>` 指的是名称为 `groupname` 的命名捕获组。

# 示例

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```

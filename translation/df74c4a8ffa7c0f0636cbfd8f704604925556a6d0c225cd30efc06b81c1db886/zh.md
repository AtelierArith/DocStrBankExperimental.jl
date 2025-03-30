```
Dates.RFC1123Format
```

描述日期和时间的RFC1123格式。

# 示例

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), RFC1123Format)
"Wed, 08 Aug 2018 12:00:43"
```

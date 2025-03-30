```
Date(d::AbstractString, df::DateFormat=ISODateFormat) -> Date
```

通过解析遵循[`DateFormat`](@ref)对象中给定模式的`d`日期字符串来构造一个`Date`，如果省略，则使用dateformat"yyyy-mm-dd"。

类似于`Date(::AbstractString, ::AbstractString)`，但在重复解析格式相似的日期字符串时，使用预先创建的`DateFormat`对象更高效。

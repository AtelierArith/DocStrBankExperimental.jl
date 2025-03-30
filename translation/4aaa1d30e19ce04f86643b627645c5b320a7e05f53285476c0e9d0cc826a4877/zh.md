```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

通过解析`t`日期时间字符串来构造一个`Time`，遵循[`DateFormat`](@ref)对象中给定的模式，或者如果省略则使用dateformat"HH:MM:SS.s"。

类似于`Time(::AbstractString, ::AbstractString)`，但在重复解析格式相似的时间字符串时，使用预先创建的`DateFormat`对象更高效。

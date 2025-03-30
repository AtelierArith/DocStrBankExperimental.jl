```
RegexMatch <: AbstractMatch
```

一个表示在字符串中找到的单个[`Regex`](@ref)匹配的类型。通常通过[`match`](@ref)函数创建。

`match`字段存储整个匹配字符串的子字符串。`captures`字段存储每个捕获组的子字符串，按编号索引。要按捕获组名称索引，应该索引整个匹配对象，如示例所示。匹配开始的位置存储在`offset`字段中。`offsets`字段存储每个捕获组开始的位置，0表示未捕获的组。

此类型可以用作`Regex`的捕获组的迭代器，生成每个组中捕获的子字符串。因此，匹配的捕获可以被解构。如果某个组未被捕获，则会返回`nothing`而不是子字符串。

接受`RegexMatch`对象的方法定义在[`iterate`](@ref)、[`length`](@ref)、[`eltype`](@ref)、[`keys`](@ref keys(::RegexMatch))、[`haskey`](@ref)和[`getindex`](@ref)中，其中键是捕获组的名称或编号。有关更多信息，请参见[`keys`](@ref keys(::RegexMatch))。

# 示例

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # 通过迭代解构捕获组

julia> hr
"11"
```

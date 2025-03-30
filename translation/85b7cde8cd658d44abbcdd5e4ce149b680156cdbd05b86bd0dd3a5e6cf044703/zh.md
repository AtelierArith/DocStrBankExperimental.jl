```
SubstitutionString(substr) <: AbstractString
```

将给定的字符串 `substr` 存储为 `SubstitutionString`，以便在正则表达式替换中使用。最常通过 [`@s_str`](@ref) 宏构造。

# 示例

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```

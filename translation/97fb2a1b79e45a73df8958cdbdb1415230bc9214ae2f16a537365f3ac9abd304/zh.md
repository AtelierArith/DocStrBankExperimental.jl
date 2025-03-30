```
readeach(io::IO, T)
```

返回一个可迭代对象，生成 [`read(io, T)`](@ref)。

另请参见 [`skipchars`](@ref)，[`eachline`](@ref)，[`readuntil`](@ref)。

!!! compat "Julia 1.6"
    `readeach` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang is a GitHub organization.
```

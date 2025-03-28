```
lowercase(s::AbstractString)
```

`s`のすべての文字を小文字に変換して返します。

他にも[`uppercase`](@ref)、[`titlecase`](@ref)、[`lowercasefirst`](@ref)を参照してください。

# 例

```jldoctest
julia> lowercase("STRINGS AND THINGS")
"strings and things"
```

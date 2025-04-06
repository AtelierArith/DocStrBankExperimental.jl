```
uppercase(s::AbstractString)
```

`s`のすべての文字を大文字に変換して返します。

関連情報としては、[`lowercase`](@ref)、[`titlecase`](@ref)、[`uppercasefirst`](@ref)があります。

# 例

```jldoctest
julia> uppercase("Julia")
"JULIA"
```

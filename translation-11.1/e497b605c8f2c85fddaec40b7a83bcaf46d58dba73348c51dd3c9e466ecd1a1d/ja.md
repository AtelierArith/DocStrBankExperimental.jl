```
uppercasefirst(s::AbstractString) -> String
```

`s`の最初の文字を大文字に変換した文字列を返します（技術的にはUnicodeの「タイトルケース」）。`s`のすべての単語の最初の文字を大文字にするには、[`titlecase`](@ref)を参照してください。

また、[`lowercasefirst`](@ref)、[`uppercase`](@ref)、[`lowercase`](@ref)、[`titlecase`](@ref)も参照してください。

# 例

```jldoctest
julia> uppercasefirst("python")
"Python"
```

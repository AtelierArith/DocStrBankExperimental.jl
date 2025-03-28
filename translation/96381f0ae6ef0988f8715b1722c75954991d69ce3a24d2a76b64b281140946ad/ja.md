```
dirname(path::AbstractString) -> String
```

パスのディレクトリ部分を取得します。パスの末尾の文字（'/' または '\'）はパスの一部としてカウントされます。

# 例

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

関連項目 [`basename`](@ref).

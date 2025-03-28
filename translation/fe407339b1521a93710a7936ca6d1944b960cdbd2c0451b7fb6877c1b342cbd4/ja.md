```
isdir(path) -> Bool
```

`path`がディレクトリであれば`true`を返し、それ以外の場合は`false`を返します。

# 例

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

[`isfile`](@ref)および[`ispath`](@ref)も参照してください。

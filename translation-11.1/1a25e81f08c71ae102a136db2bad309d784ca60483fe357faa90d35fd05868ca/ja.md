```
startswith(s::AbstractString, prefix::Regex)
```

`s`が正規表現パターン`prefix`で始まる場合、`true`を返します。

!!! note
    `startswith`はアンカーを正規表現にコンパイルしませんが、代わりにアンカーを`match_option`としてPCREに渡します。コンパイル時間が amortized される場合、`occursin(r"^...", s)`は`startswith(s, r"...")`よりも速いです。


他に[`occursin`](@ref)や[`endswith`](@ref)も参照してください。

!!! compat "Julia 1.2"
    このメソッドは少なくともJulia 1.2が必要です。


# 例

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```

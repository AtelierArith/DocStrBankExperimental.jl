```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

执行 `f`，同时临时修改 `FACES``.current`，通过零个或多个 `:name => val` 参数 `kv`，或生成 `kv` 形式值的 `kvpair_itr`。

`withfaces` 通常通过 `withfaces(kv...) do ... end` 语法使用。可以使用 `nothing` 的值来临时取消设置一个面（如果它已经被设置）。当 `withfaces` 返回时，原始的 `FACES``.current` 已被恢复。

# 示例

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} 和 {green:blue} 混合成 {magenta:purple}")
       end
red 和 blue 混合成 purple
```

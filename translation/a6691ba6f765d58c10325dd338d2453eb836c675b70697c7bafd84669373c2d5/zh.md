```
addface!(name::Symbol => default::Face)
```

通过名称 `name` 创建一个新面。只要没有以此名称存在的面，`default` 将被添加到 `FACES``.default` 和（一个副本）到 `FACES`.`current`，并返回当前值。

如果面 `name` 已经存在，则返回 `nothing`。

# 示例

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (sample)
         slant: italic
     underline: true
```

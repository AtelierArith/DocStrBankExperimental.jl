```
request(m::AbstractMenu; cursor=1)
```

显示菜单并进入交互模式。`cursor` 表示用于初始光标位置的项目编号。`cursor` 可以是 `Int` 或 `RefValue{Int}`。后者对于从外部观察和控制光标位置非常有用。

返回 `selected(m)`。

!!! compat "Julia 1.6"
    `cursor` 参数需要 Julia 1.6 或更高版本。


```
pick(m::AbstractMenu, cursor::Int)
```

定义了当用户在菜单打开时按下 Enter 键时发生的事情。如果返回 `true`，`request()` 将退出。`cursor` 索引选择的位置。

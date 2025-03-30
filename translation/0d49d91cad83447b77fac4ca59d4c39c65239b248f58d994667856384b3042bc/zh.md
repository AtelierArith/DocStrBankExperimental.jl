```
displayable(mime) -> Bool
displayable(d::AbstractDisplay, mime) -> Bool
```

返回一个布尔值，指示给定的 `mime` 类型（字符串）是否可以被当前显示堆栈中的任何显示器显示，或者在第二个变体中是否可以被显示器 `d` 显示。

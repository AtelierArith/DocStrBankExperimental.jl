```
LibGit2.reftype(ref::GitReference) -> Cint
```

返回一个与 `ref` 类型对应的 `Cint`：

  * 如果引用无效，则返回 `0`
  * 如果引用是对象 ID，则返回 `1`
  * 如果引用是符号引用，则返回 `2`

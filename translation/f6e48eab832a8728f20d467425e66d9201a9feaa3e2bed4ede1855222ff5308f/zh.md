```
splitdrive(path::AbstractString) -> (AbstractString, AbstractString)
```

在Windows上，将路径分割为驱动器字母部分和路径部分。在Unix系统中，第一个组件始终为空字符串。

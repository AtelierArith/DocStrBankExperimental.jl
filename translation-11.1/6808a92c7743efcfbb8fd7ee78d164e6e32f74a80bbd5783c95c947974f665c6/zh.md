```
模块
```

`模块`是一个独立的全局变量工作区。有关详细信息，请参见[`module`](@ref)和[关于模块的手册部分](@ref modules)。

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

返回一个具有指定名称的模块。`baremodule`对应于`Module(:ModuleName, false)`

可以使用`Module(:ModuleName, false, false)`创建一个完全不包含任何名称的空模块。此模块将不导入`Base`或`Core`，并且不包含对自身的引用。

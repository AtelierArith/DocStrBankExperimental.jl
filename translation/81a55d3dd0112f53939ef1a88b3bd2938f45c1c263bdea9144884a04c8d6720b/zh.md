```
@functionloc
```

应用于函数或宏调用时，它会评估指定调用的参数，并返回一个元组 `(filename,line)`，提供将为这些参数调用的方法的位置。它会调用 [`functionloc`](@ref) 函数。

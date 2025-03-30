```
dlclose(::Nothing)
```

对于非常常见的使用模式

```
try
    hdl = dlopen(library_name)
    ... do something
finally
    dlclose(hdl)
end
```

我们定义了一个接受类型为 `Nothing` 的参数的 `dlclose()` 方法，以便用户代码在 `library_name` 未找到的情况下不必改变其行为。

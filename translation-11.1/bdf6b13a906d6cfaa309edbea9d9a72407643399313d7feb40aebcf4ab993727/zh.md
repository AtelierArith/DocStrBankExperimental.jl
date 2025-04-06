```
finally
```

在给定代码块退出时运行一些代码，无论它是如何退出的。例如，以下是我们如何确保打开的文件被关闭：

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

当控制离开[`try`](@ref)块时（例如，由于[`return`](@ref)或正常完成），[`close(f)`](@ref)将被执行。如果`try`块由于异常而退出，异常将继续传播。`catch`块也可以与`try`和`finally`结合使用。在这种情况下，`finally`块将在`catch`处理完错误后运行。

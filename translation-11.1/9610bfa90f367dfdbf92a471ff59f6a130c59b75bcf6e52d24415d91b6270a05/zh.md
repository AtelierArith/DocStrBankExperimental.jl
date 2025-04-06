```
atreplinit(f)
```

注册一个单参数函数，在交互会话中 REPL 接口初始化之前调用；这对于自定义接口非常有用。`f` 的参数是 REPL 对象。此函数应从 `.julia/config/startup.jl` 初始化文件中调用。

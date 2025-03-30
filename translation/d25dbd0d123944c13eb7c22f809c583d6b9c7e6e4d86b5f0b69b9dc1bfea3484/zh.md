```
@everywhere [procs()] expr
```

在所有 `procs` 上执行一个表达式。任何进程上的错误都会被收集到一个 [`CompositeException`](@ref) 中并抛出。例如：

```
@everywhere bar = 1
```

将在所有当前进程中定义 `Main.bar`。任何稍后添加的进程（例如使用 [`addprocs()`](@ref)）将不会定义该表达式。

与 [`@spawnat`](@ref) 不同，`@everywhere` 不捕获任何局部变量。相反，可以使用插值广播局部变量：

```
foo = 1
@everywhere bar = $foo
```

可选参数 `procs` 允许指定一个子集的所有进程来执行该表达式。

类似于调用 `remotecall_eval(Main, procs, expr)`，但有两个额外的功能：

```
- `using` 和 `import` 语句首先在调用进程上运行，以确保
  包已预编译。
- `include` 使用的当前源文件路径会传播到其他进程。
```

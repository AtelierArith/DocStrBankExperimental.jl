```
@distributed
```

一种分布式内存的并行 for 循环形式：

```
@distributed [reducer] for var = range
    body
end
```

指定的范围被划分并在所有工作节点上本地执行。如果指定了可选的 reducer 函数，`@distributed` 会在每个工作节点上执行本地归约，并在调用进程上进行最终归约。

请注意，如果没有 reducer 函数，`@distributed` 会异步执行，即它会在所有可用工作节点上生成独立的任务，并立即返回而不等待完成。要等待完成，请在调用前加上 [`@sync`](@ref)，如：

```
@sync @distributed for var = range
    body
end
```

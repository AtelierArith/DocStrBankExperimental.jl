```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

将分析结果打印到 `io`（默认是 `stdout`）。如果您没有提供 `data` 向量，将使用内部的累积回溯缓冲区。

关键字参数可以是以下任意组合：

  * `format` – 决定回溯是以（默认，`:tree`）还是不带（`:flat`）缩进的方式打印，缩进表示树结构。
  * `C` – 如果为 `true`，则显示来自 C 和 Fortran 代码的回溯（通常会被排除）。
  * `combine` – 如果为 `true`（默认），则合并对应于同一行代码的指令指针。
  * `maxdepth` – 限制在 `:tree` 格式中高于 `maxdepth` 的深度。
  * `sortedby` – 控制 `:flat` 格式中的顺序。`:filefuncline`（默认）按源代码行排序，`:count` 按收集样本的数量排序，`:overhead` 按每个函数自身产生的样本数量排序。
  * `groupby` – 控制任务和线程的分组，或不分组。选项有 `:none`（默认）、`:thread`、`:task`、`[:thread, :task]` 或 `[:task, :thread]`，后两个提供嵌套分组。
  * `noisefloor` – 限制超过样本启发式噪声底线的帧（仅适用于格式 `:tree`）。建议尝试的值为 2.0（默认值为 0）。此参数隐藏 `n <= noisefloor * √N` 的样本，其中 `n` 是该行的样本数量，`N` 是被调用者的样本数量。
  * `mincount` – 限制打印输出仅包含至少有 `mincount` 次出现的行。
  * `recur` – 控制 `:tree` 格式中的递归处理。`:off`（默认）正常打印树。`:flat` 则压缩任何递归（按 ip），显示将任何自我递归转换为迭代器的近似效果。`:flatc` 也执行相同操作，但还包括 C 帧的折叠（可能在 `jl_apply` 周围做奇怪的事情）。
  * `threads::Union{Int,AbstractVector{Int}}` – 指定在报告中包含快照的线程。请注意，这并不控制在哪些线程上收集样本（这些样本也可能在另一台机器上收集）。
  * `tasks::Union{Int,AbstractVector{Int}}` – 指定在报告中包含快照的任务。请注意，这并不控制在哪些任务中收集样本。

!!! compat "Julia 1.8"
    `groupby`、`threads` 和 `tasks` 关键字参数是在 Julia 1.8 中引入的。


!!! note
    在 Windows 上的分析仅限于主线程。其他线程未被采样，因此不会显示在报告中。


```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

使用多个并发任务对集合（或多个相同长度的集合）进行 `f` 的映射。对于多个集合参数，`f` 是逐元素应用的。

`ntasks` 指定要并发运行的任务数量。根据集合的长度，如果未指定 `ntasks`，则最多将使用 100 个任务进行并发映射。

`ntasks` 也可以指定为一个无参数的函数。在这种情况下，在处理每个元素之前会检查并行运行的任务数量，如果 `ntasks_func` 的值大于当前任务数量，则会启动一个新任务。

如果指定了 `batch_size`，则集合将以批处理模式进行处理。此时，`f` 必须是一个接受参数元组的 `Vector` 的函数，并且必须返回一个结果的向量。输入向量的长度将为 `batch_size` 或更少。

以下示例通过返回映射函数执行的任务的 `objectid` 来突出不同任务中的执行。

首先，在 `ntasks` 未定义的情况下，每个元素在不同的任务中处理。

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

当 `ntasks=2` 时，所有元素在 2 个任务中处理。

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

定义 `batch_size` 后，映射函数需要更改为接受参数元组的数组并返回结果的数组。修改后的映射函数中使用 `map` 来实现这一点。

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```

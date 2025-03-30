```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> collection
```

通过对每个元素应用 `f` 来转换集合 `c`，使用可用的工作者和任务。

对于多个集合参数，逐元素应用 `f`。

请注意，`f` 必须对所有工作进程可用；有关详细信息，请参见 [代码可用性和加载包](@ref code-availability)。

如果未指定工作者池，将通过 [`CachingPool`](@ref) 使用所有可用的工作者。

默认情况下，`pmap` 在所有指定的工作者上分配计算。要仅使用本地进程并在任务之间分配，请指定 `distributed=false`。这相当于使用 [`asyncmap`](@ref)。例如，`pmap(f, c; distributed=false)` 相当于 `asyncmap(f,c; ntasks=()->nworkers())`

`pmap` 还可以通过 `batch_size` 参数使用进程和任务的混合。对于大于 1 的批量大小，集合将分成多个批次处理，每个批次的长度为 `batch_size` 或更少。一个批次作为单个请求发送到空闲工作者，在那里本地的 [`asyncmap`](@ref) 使用多个并发任务处理批次中的元素。

任何错误都会阻止 `pmap` 处理集合的其余部分。要覆盖此行为，您可以通过参数 `on_error` 指定一个错误处理函数，该函数接受一个参数，即异常。该函数可以通过重新抛出错误来停止处理，或者为了继续，返回任何值，然后与结果一起返回给调用者。

考虑以下两个示例。第一个示例在线返回异常对象，第二个示例在任何异常的位置返回 0：

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

错误也可以通过重试失败的计算来处理。关键字参数 `retry_delays` 和 `retry_check` 作为关键字参数 `delays` 和 `check` 传递给 [`retry`](@ref)。如果指定了批处理，并且整个批次失败，则批次中的所有项目都会被重试。

请注意，如果同时指定了 `on_error` 和 `retry_delays`，则在重试之前会调用 `on_error` 钩子。如果 `on_error` 不抛出（或重新抛出）异常，则该元素将不会被重试。

示例：在错误发生时，最多重试 `f` 对一个元素 3 次，重试之间没有任何延迟。

```julia
pmap(f, c; retry_delays = zeros(3))
```

示例：仅在异常不是 [`InexactError`](@ref) 类型时重试 `f`，并以指数方式增加延迟，最多重试 3 次。对于所有 `InexactError` 的出现返回 `NaN`。

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```

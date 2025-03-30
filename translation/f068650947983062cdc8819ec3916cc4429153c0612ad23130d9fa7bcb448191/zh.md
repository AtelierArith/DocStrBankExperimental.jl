```
Timer(callback::Function, delay; interval = 0)
```

创建一个定时器，在每次定时器到期时运行函数 `callback`。

等待的任务会被唤醒，函数 `callback` 在初始延迟 `delay` 秒后被调用，然后以给定的间隔（以秒为单位）重复调用。如果 `interval` 等于 `0`，则回调只会运行一次。函数 `callback` 以一个参数被调用，即定时器本身。通过调用 `close` 来停止定时器。如果定时器已经到期，`callback` 可能仍会被最后一次运行。

# 示例

这里第一个数字在延迟两秒后打印，然后后续的数字快速打印。

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```

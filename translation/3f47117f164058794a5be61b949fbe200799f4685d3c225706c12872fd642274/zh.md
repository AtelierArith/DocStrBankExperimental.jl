```
Threads.maxthreadid() -> Int
```

获取可用于 Julia 进程的线程数量的下限（跨所有线程池），具有原子获取语义。结果将始终大于或等于 [`threadid()`](@ref) 以及 `threadid(task)`，对于您在调用 `maxthreadid` 之前能够观察到的任何任务。

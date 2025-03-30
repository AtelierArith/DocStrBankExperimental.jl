```
interrupt(pids::AbstractVector=workers())
```

中断指定工作者上当前正在执行的任务。这相当于在本地机器上按下 Ctrl-C。如果没有给出参数，则所有工作者都会被中断。

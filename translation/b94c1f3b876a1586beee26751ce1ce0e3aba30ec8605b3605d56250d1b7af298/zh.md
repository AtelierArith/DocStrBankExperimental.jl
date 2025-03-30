```
RemoteException(captured)
```

在远程计算中捕获并重新抛出异常。`RemoteException` 包装了工作者的 `pid` 和一个捕获的异常。`CapturedException` 捕获远程异常以及在异常被抛出时调用栈的可序列化形式。

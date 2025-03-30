```
cancel(m::AbstractMenu)
```

定义当用户取消（'q' 或 ctrl-c）菜单时发生的事情。`request()` 在调用此函数后将始终退出。

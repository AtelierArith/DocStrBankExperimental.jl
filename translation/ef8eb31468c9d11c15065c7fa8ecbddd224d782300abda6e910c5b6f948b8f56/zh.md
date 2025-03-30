```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

尝试解析我们的 pidfile 格式，对于任何读取失败的元素，分别替换为 (0, "", 0.0)。

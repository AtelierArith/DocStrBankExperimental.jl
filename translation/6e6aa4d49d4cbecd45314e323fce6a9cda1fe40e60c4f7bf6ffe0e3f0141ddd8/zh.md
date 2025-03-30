```
tryopen_exclusive(path::String, mode::Integer = 0o444) :: Union{Void, File}
```

尝试创建一个新的文件以进行读写建议独占访问，如果文件已存在则返回空。

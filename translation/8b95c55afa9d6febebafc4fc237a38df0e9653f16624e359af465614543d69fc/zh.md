```
devnull
```

用于流重定向，以丢弃写入其中的所有数据。基本上等同于 Unix 上的 `/dev/null` 或 Windows 上的 `NUL`。用法：

```julia
run(pipeline(`cat test.txt`, devnull))
```

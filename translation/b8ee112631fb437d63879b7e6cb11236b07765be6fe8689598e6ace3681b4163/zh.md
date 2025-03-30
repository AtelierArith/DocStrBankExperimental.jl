```
write(filename::AbstractString, content)
```

将 `content` 的规范二进制表示写入文件，如果文件尚不存在，则会创建该文件；如果文件已存在，则会覆盖该文件。

返回写入文件的字节数。

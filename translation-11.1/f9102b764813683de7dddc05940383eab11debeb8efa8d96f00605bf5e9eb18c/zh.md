```
tempdir()
```

获取临时目录的路径。在 Windows 上，`tempdir()` 使用在有序列表 `TMP`、`TEMP`、`USERPROFILE` 中找到的第一个环境变量。在所有其他操作系统上，`tempdir()` 使用在有序列表 `TMPDIR`、`TMP`、`TEMP` 和 `TEMPDIR` 中找到的第一个环境变量。如果没有找到这些，使用路径 `"/tmp"`。

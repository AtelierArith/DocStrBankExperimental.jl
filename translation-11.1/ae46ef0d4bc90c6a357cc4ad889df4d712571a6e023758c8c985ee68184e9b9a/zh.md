```
宏 artifact_str(name)
```

返回磁盘上工件的路径。自动通过名称在项目的 `(Julia)Artifacts.toml` 文件中查找工件。如果请求的工件不存在，则会抛出错误。如果在 REPL 中运行，将从当前目录开始搜索 toml 文件，更多信息请参见 `find_artifacts_toml()`。

如果工件被标记为“懒惰”，并且包中定义了 `using LazyArtifacts`，则在第一次尝试计算路径时，工件将按需使用 `Pkg` 下载。然后，这些文件将保留在本地以供后用。

如果 `name` 包含正斜杠或反斜杠，则第一个斜杠之后的所有元素将被视为索引工件的路径名称，从而允许轻松的一行代码访问工件中的单个文件/目录。示例：

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! 兼容 "Julia 1.3"     此宏至少需要 Julia 1.3。

!!! 兼容 "Julia 1.6"     斜杠索引至少需要 Julia 1.6。

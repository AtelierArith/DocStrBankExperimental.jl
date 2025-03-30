```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

从给定的 url 下载文件，保存到位置 `path`，如果未指定，则保存到临时路径。返回下载文件的路径。

!!! note
    从 Julia 1.6 开始，此函数已被弃用，仅是 `Downloads.download` 的一个薄包装。在新代码中，您应该直接使用该函数，而不是调用这个。


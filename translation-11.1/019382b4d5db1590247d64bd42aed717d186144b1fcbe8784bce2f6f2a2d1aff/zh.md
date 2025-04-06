```
download(url, [ output = tempname() ];
    [ method = "GET", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ downloader = <default>, ]
) -> output

    url        :: AbstractString
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (total::Integer, now::Integer) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    downloader :: Downloader
```

从给定的 url 下载文件，将其保存到 `output`，如果未指定，则保存到临时路径。`output` 也可以是一个 `IO` 句柄，在这种情况下，响应的主体将被流式传输到该句柄，并返回该句柄。如果 `output` 是一个命令，则该命令将被运行，输出将通过 stdin 发送给它。

如果提供了 `downloader` 关键字参数，则它必须是一个 `Downloader` 对象。资源和连接将在由同一 `Downloader` 执行的下载之间共享，并在对象被垃圾回收或在一段宽限期内没有执行下载时自动清理。有关配置和使用的更多信息，请参见 `Downloader`。

如果提供了 `headers` 关键字参数，则它必须是一个向量或字典，其元素都是字符串对。这些对在下载支持它们的协议（如 HTTP/S）的 URL 时作为头部传递。

`timeout` 关键字参数指定下载完成的超时时间（以秒为单位），分辨率为毫秒。默认情况下未设置超时，但也可以通过传递超时值 `Inf` 明确请求。单独地，如果在 20 秒内没有接收到任何数据，则下载将超时。有关如何禁用此超时的扩展帮助，请参见。

如果提供了 `progress` 关键字参数，则它必须是一个回调函数，该函数将在有关正在进行的下载的大小和状态有更新时被调用。回调必须接受两个整数参数：`total` 和 `now`，它们分别是下载的总大小（以字节为单位）和到目前为止已下载的字节数。请注意，`total` 初始为零，并且在服务器给出下载总大小的指示（例如，通过 `Content-Length` 头）之前保持为零，这可能永远不会发生。因此，一个良好的进度回调应该优雅地处理总大小为零的情况。

如果将 `verbose` 选项设置为 true，则用于实现下载功能的 `libcurl` 将向 `stderr` 打印调试信息。如果将 `debug` 选项设置为接受两个 `String` 参数的函数，则将忽略详细选项，而是将本应打印到 `stderr` 的数据传递给 `debug` 回调，参数为 `type` 和 `message`。`type` 参数指示发生了什么类型的事件，可能是：`TEXT`、`HEADER IN`、`HEADER OUT`、`DATA IN`、`DATA OUT`、`SSL DATA IN` 或 `SSL DATA OUT`。`message` 参数是调试事件的描述。

## 扩展帮助

有关进一步的自定义，请使用 [`Downloader`](@ref) 和 [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads)。例如，要在未接收到数据时禁用 20 秒超时，可以使用以下代码：

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```

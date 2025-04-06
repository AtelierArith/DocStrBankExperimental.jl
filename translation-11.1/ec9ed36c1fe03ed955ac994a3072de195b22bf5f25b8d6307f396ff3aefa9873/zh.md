```
request(url;
    [ input = <none>, ]
    [ output = <none>, ]
    [ method = input ? "PUT" : output ? "GET" : "HEAD", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ throw = true, ]
    [ downloader = <default>, ]
    [ interrupt = <none>, ]
) -> Union{Response, RequestError}

    url        :: AbstractString
    input      :: Union{AbstractString, AbstractCmd, IO}
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (dl_total, dl_now, ul_total, ul_now) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    throw      :: Bool
    downloader :: Downloader
    interrupt  :: Base.Event
```

向给定的 URL 发起请求，返回一个 `Response` 对象，捕获状态、头信息和关于响应的其他信息。如果指定了 `output`，响应的主体将被写入 `output`，否则将被丢弃。对于 HTTP/S 请求，如果给定了 `input` 流，则发起 `PUT` 请求；否则如果给定了 `output` 流，则发起 `GET` 请求；如果两者都没有，则发起 `HEAD` 请求。对于其他协议，将根据请求的输入和输出组合使用适当的默认方法。以下选项与 `download` 函数不同：

  * `input` 允许提供请求主体；如果提供，则默认为 `PUT` 请求
  * `progress` 是一个回调，接受四个整数用于上传和下载进度
  * `throw` 控制在请求错误时是抛出异常还是返回 `RequestError`

请注意，与 `download` 不同，如果请求的 URL 无法下载（由非 2xx 状态码指示），`request` 无论响应的状态码是什么都会返回一个 `Response` 对象。如果在获取响应时出现错误，则会抛出或返回 `RequestError`。

如果提供了 `interrupt` 关键字参数，它必须是一个 `Base.Event` 对象。如果在请求进行时触发该事件，请求将被取消并抛出错误。这可以用于中断长时间运行的请求，例如如果用户想要取消下载。

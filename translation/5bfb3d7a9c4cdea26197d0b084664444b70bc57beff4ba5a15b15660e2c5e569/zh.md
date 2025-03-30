```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError` 是一个类型，用于捕获请求失败响应的属性作为异常对象：

  * `url`: 原始请求的 URL，没有任何重定向
  * `code`: libcurl 错误代码；如果发生了仅协议错误，则为 `0`
  * `message`: libcurl 错误消息，指示出了什么问题
  * `response`: 捕获可用响应信息的响应对象

如果请求成功但由于状态代码不在 2xx 范围内而指示存在协议级别错误，则相同的 `RequestError` 类型会被 `download` 抛出，此时 `code` 将为零，`message` 字段将为空字符串。`request` API 仅在 libcurl 错误 `code` 非零时抛出 `RequestError`，在这种情况下，包含的 `response` 对象可能会有 `status` 为零和空消息。然而，也存在由于协议错误而抛出 curl 级别错误的情况，在这种情况下，内部和外部的代码和消息都可能是重要的。

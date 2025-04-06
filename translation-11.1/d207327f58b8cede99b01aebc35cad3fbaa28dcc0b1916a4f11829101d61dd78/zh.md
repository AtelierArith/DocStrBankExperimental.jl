```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response` 是一个类型，捕获了对请求成功响应的属性作为一个对象。它具有以下字段：

  * `proto`: 用于获取响应的协议
  * `url`: 在跟随重定向后最终请求的 URL
  * `status`: 响应的状态码，指示成功、失败等
  * `message`: 描述响应性质的文本消息
  * `headers`: 与响应一起返回的任何头部

这些响应的含义和可用性取决于用于请求的协议。对于许多协议，包括 HTTP/S 和 S/FTP，2xx 状态码表示成功响应。对于不支持头部的协议的响应，头部向量将为空。HTTP/2 不包括状态消息，仅包含状态码，因此消息将为空。

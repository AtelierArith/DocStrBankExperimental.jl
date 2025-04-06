```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Function
```

返回一个匿名函数，该函数调用函数 `f`。如果出现异常，`f` 将在每次 `check` 返回 `true` 后，重复调用，每次等待 `delays` 指定的秒数。`check` 应输入 `delays` 的当前状态和 `Exception`。

!!! compat "Julia 1.2"
    在 Julia 1.2 之前，此签名仅限于 `f::Function`。


# 示例

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```

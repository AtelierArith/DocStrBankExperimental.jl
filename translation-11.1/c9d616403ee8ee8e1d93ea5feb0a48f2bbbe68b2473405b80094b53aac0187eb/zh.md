```
fetch(x::Future)
```

等待并获取[`Future`](@ref)的值。获取的值会被本地缓存。对同一引用的进一步调用`fetch`将返回缓存的值。如果远程值是一个异常，则抛出一个[`RemoteException`](@ref)，该异常捕获远程异常和回溯信息。

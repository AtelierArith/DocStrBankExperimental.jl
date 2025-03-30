```
LibGit2.Buffer
```

用于从 libgit2 导出数据的数据缓冲区。与 [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf) 结构匹配。

从 LibGit2 获取数据时，典型的用法如下：

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# 对 buf_ref 的操作
free(buf_ref)
```

特别注意，之后应该在 `Ref` 对象上调用 `LibGit2.free`。

```
LibGit2.StrArrayStruct
```

LibGit2 的字符串数组表示。与 [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray) 结构匹配。

从 LibGit2 获取数据时，典型的用法如下：

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

特别注意，之后应该在 `Ref` 对象上调用 `LibGit2.free`。

相反，当将字符串向量传递给 LibGit2 时，通常最简单的方法是依赖隐式转换：

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

注意不需要调用 `free`，因为数据是由 Julia 分配的。

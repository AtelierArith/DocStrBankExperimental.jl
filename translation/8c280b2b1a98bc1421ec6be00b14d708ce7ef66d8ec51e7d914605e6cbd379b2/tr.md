```
LibGit2.Buffer
```

libgit2'den veri dışa aktarmak için bir veri tamponu. [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf) yapısıyla eşleşir.

LibGit2'den veri alırken, tipik bir kullanım şöyle görünür:

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# buf_ref üzerinde işlem
free(buf_ref)
```

Özellikle, `Ref` nesnesi üzerinde daha sonra `LibGit2.free` çağrılması gerektiğine dikkat edin.

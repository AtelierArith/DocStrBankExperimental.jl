```
LibGit2.StrArrayStruct
```

Bir LibGit2 temsilidir dizi dizeleri. [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray) yapısıyla eşleşir.

LibGit2'den veri alırken, tipik bir kullanım şöyle görünür:

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

Özellikle, `Ref` nesnesi üzerinde `LibGit2.free` çağrısının yapılması gerektiğini unutmayın.

Tersine, LibGit2'ye bir dizi dize geçirirken, genellikle örtük dönüşüme güvenmek en basit yoldur:

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

Verilerin Julia tarafından tahsis edildiği için `free` çağrısına gerek olmadığını unutmayın.

```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/SharedArrays/docs/src/index.md"
```

# Shared Arrays

`SharedArray` 表示一个数组，该数组在单台机器上的多个进程之间共享。

```@docs
SharedArrays.SharedArray
SharedArrays.SharedVector
SharedArrays.SharedMatrix
SharedArrays.procs(::SharedArray)
SharedArrays.sdata
SharedArrays.indexpids
SharedArrays.localindices
```

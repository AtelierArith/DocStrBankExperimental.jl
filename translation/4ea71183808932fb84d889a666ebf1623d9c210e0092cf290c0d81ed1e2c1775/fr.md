```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/SharedArrays/docs/src/index.md"
```

# Shared Arrays

`SharedArray` représente un tableau, qui est partagé entre plusieurs processus, sur une seule machine.

```@docs
SharedArrays.SharedArray
SharedArrays.SharedVector
SharedArrays.SharedMatrix
SharedArrays.procs(::SharedArray)
SharedArrays.sdata
SharedArrays.indexpids
SharedArrays.localindices
```

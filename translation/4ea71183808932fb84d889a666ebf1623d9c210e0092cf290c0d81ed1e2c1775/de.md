```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/SharedArrays/docs/src/index.md"
```

# Shared Arrays

`SharedArray` stellt ein Array dar, das auf einer einzelnen Maschine über mehrere Prozesse hinweg geteilt wird.

```@docs
SharedArrays.SharedArray
SharedArrays.SharedVector
SharedArrays.SharedMatrix
SharedArrays.procs(::SharedArray)
SharedArrays.sdata
SharedArrays.indexpids
SharedArrays.localindices
```

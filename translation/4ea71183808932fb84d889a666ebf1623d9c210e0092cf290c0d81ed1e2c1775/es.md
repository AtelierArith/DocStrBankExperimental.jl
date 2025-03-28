```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/SharedArrays/docs/src/index.md"
```

# Shared Arrays

`SharedArray` representa un arreglo, que se comparte entre múltiples procesos, en una sola máquina.

```@docs
SharedArrays.SharedArray
SharedArrays.SharedVector
SharedArrays.SharedMatrix
SharedArrays.procs(::SharedArray)
SharedArrays.sdata
SharedArrays.indexpids
SharedArrays.localindices
```

```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/SharedArrays/docs/src/index.md"
```

# Shared Arrays

`SharedArray`는 단일 머신에서 여러 프로세스 간에 공유되는 배열을 나타냅니다.

```@docs
SharedArrays.SharedArray
SharedArrays.SharedVector
SharedArrays.SharedMatrix
SharedArrays.procs(::SharedArray)
SharedArrays.sdata
SharedArrays.indexpids
SharedArrays.localindices
```

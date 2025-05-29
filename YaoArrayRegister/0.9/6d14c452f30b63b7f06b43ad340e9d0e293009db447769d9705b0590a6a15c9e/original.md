```
arrayreg(state; nbatch::Union{Integer,NoBatch}=NoBatch(), nlevel::Integer=2)
```

Create an array register, if nbatch is a integer, it will return a `BatchedArrayReg`.

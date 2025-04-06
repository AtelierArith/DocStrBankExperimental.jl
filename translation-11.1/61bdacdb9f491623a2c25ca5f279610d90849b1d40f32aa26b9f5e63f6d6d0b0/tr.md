```
copy_transpose!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

Matris `A`'nın elemanlarını `B`'ye transpoze ederek verimli bir şekilde kopyalayın:

```
B[ir_dest, jr_dest] = transpose(A)[jr_src, ir_src]
```

`B[ir_dest, jr_dest]` elemanları üzerine yazılır. Ayrıca, indeks aralığı parametreleri `length(ir_dest) == length(jr_src)` ve `length(jr_dest) == length(ir_src)` koşulunu sağlamalıdır.

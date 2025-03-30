```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

`S` boyutları `m x n` olan bir seyrek matris oluşturur ve `S[I[k], J[k]]` konumlarında yapısal sıfırlar içerir.

Bu yöntem, matrisin seyreklik desenini oluşturmak için kullanılabilir ve `sparse(I, J, zeros(length(I)))` gibi yöntemlerden daha verimlidir.

Ek belgeler ve uzman bir sürücü için `SparseArrays.spzeros!`'a bakın.

!!! uyumluluk "Julia 1.10"
    Bu yöntem Julia sürüm 1.10 veya daha yenisini gerektirir.


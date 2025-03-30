```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

Sıkıştırılmış bir matris sütununun yapısal sıfır olmayan değerlerinin indeks aralığını döndürür. Bu, [`nonzeros`](@ref) ve [`rowvals`](@ref) ile birlikte kullanıldığında, sıkıştırılmış bir matris üzerinde rahatça yineleme yapmayı sağlar:

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # sıkıştırılmış sihirbazlık yap...
   end
end
```

!!! uyarı     Matriste sıfır olmayan eleman eklemek veya çıkarmak `nzrange`'i geçersiz kılabilir, bu nedenle yineleme sırasında matrisi değiştirmemek gerekir.

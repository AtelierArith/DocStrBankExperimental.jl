```
oneto(n::Int) -> f(register)
oneto(r::AbstractArrayReg, n::Int=nqudits(r))
```

`1:n` のクディットがアクティブなレジスタを返します。これは一般的な [`focus`](@ref) 関数よりも高速です。

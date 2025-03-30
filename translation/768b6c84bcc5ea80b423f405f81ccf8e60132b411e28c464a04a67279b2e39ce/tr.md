```
transpose(F::Factorization)
```

F faktorizasyonunun tembel transpozunu döndürür. Varsayılan olarak, gerçek `eltype`'a sahip `Factorization`'lar hariç, bir [`TransposeFactorization`](@ref) döndürür; bu durumda bir [`AdjointFactorization`](@ref) döndürür.

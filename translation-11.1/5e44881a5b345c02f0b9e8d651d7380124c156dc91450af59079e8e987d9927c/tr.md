```
isdispatchtuple(T)
```

`T` türünün bir tuple "leaf type" olup olmadığını belirleyin, yani dispatch'te bir tür imzası olarak görünebilir ve bir çağrıda görünebilecek alt türleri (veya üst türleri) yoktur. Eğer `T` bir tür değilse, `false` döndürün.

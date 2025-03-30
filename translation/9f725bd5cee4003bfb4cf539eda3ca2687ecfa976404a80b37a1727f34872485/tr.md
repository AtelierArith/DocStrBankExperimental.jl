```
typeintersect(T::Type, S::Type)
```

`T` ve `S`'nin kesişimini içeren bir tür hesaplayın. Genellikle bu, en küçük böyle bir tür veya ona yakın bir tür olacaktır.

Kesin davranışın garanti edildiği özel bir durum: `T <: S` olduğunda, `typeintersect(S, T) == T == typeintersect(T, S)`.

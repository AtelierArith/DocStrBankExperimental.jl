```
AbstractDict{K, V}
```

Supertipo para tipos similares a diccionarios con claves del tipo `K` y valores del tipo `V`. [`Dict`](@ref), [`IdDict`](@ref) y otros tipos son subtipos de este. Un `AbstractDict{K, V}` debería ser un iterador de `Pair{K, V}`.

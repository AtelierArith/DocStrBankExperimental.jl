```
precompile(f, argtypes::Tuple{Vararg{Any}}, m::Method)
```

Precompilar un método específico para los tipos de argumento dados. Esto puede usarse para precompilar un método diferente al que normalmente sería elegido por el despacho, imitando así `invoke`.

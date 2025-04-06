```
deserialize(stream)
```

Lee un valor escrito por [`serialize`](@ref). `deserialize` asume que los datos binarios leídos de `stream` son correctos y han sido serializados por una implementación compatible de [`serialize`](@ref). `deserialize` está diseñado para simplicidad y rendimiento, por lo que no valida los datos leídos. Los datos malformados pueden resultar en la terminación del proceso. El llamador debe asegurar la integridad y corrección de los datos leídos de `stream`.

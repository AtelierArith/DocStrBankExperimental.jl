```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

Escribe `data` en sintaxis TOML en el flujo `io`. Si el argumento clave `sorted` se establece en `true`, ordena las tablas de acuerdo con la función dada por el argumento clave `by`. Si se proporciona el argumento clave `inline_tables`, debe ser un conjunto de tablas que se deben imprimir "en línea".

Los siguientes tipos de datos son compatibles: `AbstractDict`, `AbstractVector`, `AbstractString`, `Integer`, `AbstractFloat`, `Bool`, `Dates.DateTime`, `Dates.Time`, `Dates.Date`. Ten en cuenta que los enteros y flotantes deben ser convertibles a `Float64` e `Int64` respectivamente. Para otros tipos de datos, pasa la función `to_toml` que toma los tipos de datos y devuelve un valor de un tipo compatible.

```
Parser()
```

Constructor para un `Parser` de TOML. Tenga en cuenta que en la mayoría de los casos no es necesario crear explícitamente un `Parser`, sino que se utiliza directamente [`TOML.parsefile`](@ref) o [`TOML.parse`](@ref). Sin embargo, usar un parser explícito reutilizará algunas estructuras de datos internas, lo que puede ser beneficioso para el rendimiento si se analizan un mayor número de archivos pequeños.

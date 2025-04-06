```
Base.compilecache(module::PkgId)
```

Crea un archivo de caché precompilado para un módulo y todas sus dependencias. Esto se puede usar para reducir los tiempos de carga de paquetes. Los archivos de caché se almacenan en `DEPOT_PATH[1]/compiled`. Consulta [Module initialization and precompilation](@ref) para notas importantes.

```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

Devuelve una tabla en markdown que proporciona información sobre variables globales públicas en un módulo, restringidas opcionalmente a aquellas que coinciden con `pattern`.

La estimación del consumo de memoria es un límite inferior aproximado del tamaño de la estructura interna del objeto.

  * `all` : también lista objetos no públicos definidos en el módulo, objetos obsoletos y objetos generados por el compilador.
  * `imported` : también lista objetos importados explícitamente de otros módulos.
  * `recursive` : incluye recursivamente objetos en sub-módulos, observando la misma configuración en cada uno.
  * `sortby` : la columna por la que ordenar los resultados. Las opciones son `:name` (predeterminado), `:size` y `:summary`.
  * `minsize` : solo incluye objetos con un tamaño de al menos `minsize` bytes. Por defecto es `0`.

La salida de `varinfo` está destinada solo a fines de visualización.  Véase también [`names`](@ref) para obtener un array de símbolos definidos en un módulo, que es adecuado para manipulaciones más generales.

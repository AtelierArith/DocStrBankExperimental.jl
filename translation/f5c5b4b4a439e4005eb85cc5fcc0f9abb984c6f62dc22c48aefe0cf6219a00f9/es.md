```
WeakKeyDict([itr])
```

`WeakKeyDict()` construye una tabla hash donde las claves son referencias débiles a objetos que pueden ser recolectados por el recolector de basura incluso cuando están referenciados en una tabla hash.

Consulta [`Dict`](@ref) para más ayuda. Ten en cuenta que, a diferencia de [`Dict`](@ref), `WeakKeyDict` no convierte las claves al insertarlas, ya que esto implicaría que el objeto clave no estaba referenciado en ningún lugar antes de la inserción.

Consulta también [`WeakRef`](@ref).

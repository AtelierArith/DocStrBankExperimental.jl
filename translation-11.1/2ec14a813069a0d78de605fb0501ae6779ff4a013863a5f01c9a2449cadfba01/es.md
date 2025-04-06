```
propertynames(x, private=false)
```

Obtiene una tupla o un vector de las propiedades (`x.property`) de un objeto `x`. Esto es típicamente lo mismo que [`fieldnames(typeof(x))`](@ref), pero los tipos que sobrecargan [`getproperty`](@ref) generalmente deberían sobrecargar `propertynames` también para obtener las propiedades de una instancia del tipo.

`propertynames(x)` puede devolver solo los nombres de propiedades "públicas" que son parte de la interfaz documentada de `x`. Si deseas que también devuelva los nombres de propiedades "privadas" destinadas para uso interno, pasa `true` como segundo argumento opcional. La finalización de tabulación en el REPL sobre `x.` muestra solo las propiedades `private=false`.

Consulta también: [`hasproperty`](@ref), [`hasfield`](@ref).

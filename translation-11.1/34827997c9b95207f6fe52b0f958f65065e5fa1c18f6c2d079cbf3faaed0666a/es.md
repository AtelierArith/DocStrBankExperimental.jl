```
code_lowered(f, types; generated=true, debuginfo=:default)
```

Devuelve un array de las formas reducidas (IR) para los métodos que coinciden con la función genérica dada y la firma de tipo.

Si `generated` es `false`, las instancias de `CodeInfo` devueltas corresponderán a implementaciones de respaldo. Se lanzará un error si no existe ninguna implementación de respaldo. Si `generated` es `true`, estas instancias de `CodeInfo` corresponderán a los cuerpos de método generados al expandir los generadores.

La palabra clave `debuginfo` controla la cantidad de metadatos de código presentes en la salida.

Ten en cuenta que se lanzará un error si `types` no son tipos hoja cuando `generated` es `true` y cualquiera de los métodos correspondientes es un método `@generated`.

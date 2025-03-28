```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

Escribe una instantánea del montón, en el formato JSON esperado por el visor de instantáneas de montón de Chrome Devtools (extensión .heapsnapshot) a un archivo (`$pid_$timestamp.heapsnapshot`) en el directorio actual por defecto (o en tempdir si el directorio actual no es escribible), o en `dir` si se proporciona, o en la ruta de archivo completa dada, o en un flujo de IO.

Si `all_one` es verdadero, entonces informa el tamaño de cada objeto como uno para que puedan ser contados fácilmente. De lo contrario, informa el tamaño real.

Si `streaming` es verdadero, transmitiremos los datos de la instantánea en cuatro archivos, utilizando filepath como prefijo, para evitar tener que mantener toda la instantánea en memoria. Esta opción debe usarse para cualquier configuración donde tu memoria esté limitada. Estos archivos pueden ser reensamblados llamando a Profile.HeapSnapshot.assemble_snapshot(), lo que se puede hacer fuera de línea.

NOTA: Recomendamos encarecidamente establecer streaming=true por razones de rendimiento. Reconstruir la instantánea a partir de las partes requiere mantener toda la instantánea en memoria, por lo que si la instantánea es grande, puedes quedarte sin memoria mientras la procesas. La transmisión te permite reconstruir la instantánea fuera de línea, después de que tu carga de trabajo haya terminado de ejecutarse. Si intentas recopilar una instantánea con streaming=false (el valor predeterminado, por compatibilidad hacia atrás) y tu proceso es terminado, ten en cuenta que esto siempre guardará las partes en el mismo directorio que tu filepath proporcionado, por lo que aún puedes reconstruir la instantánea después del hecho, a través de `assemble_snapshot()`.

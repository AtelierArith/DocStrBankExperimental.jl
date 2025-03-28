```
serialize(stream::IO, value)
```

Escribe un valor arbitrario en un flujo en un formato opaco, de modo que se pueda leer de nuevo con [`deserialize`](@ref). El valor leído será lo más idéntico posible al original, pero ten en cuenta que los valores `Ptr` se serializan como patrones de bits de cero (`NULL`).

Se escribe primero un encabezado identificador de 8 bytes en el flujo. Para evitar escribir el encabezado, construye un `Serializer` y úsalo como el primer argumento de `serialize`. Consulta también [`Serialization.writeheader`](@ref).

El formato de datos puede cambiar en versiones menores (1.x) de Julia, pero los archivos escritos por versiones anteriores de 1.x seguirán siendo legibles. La principal excepción a esto es cuando la definición de un tipo en un paquete externo cambia. Si eso ocurre, puede ser necesario especificar una versión compatible explícita del paquete afectado en tu entorno. Renombrar funciones, incluso funciones privadas, dentro de los paquetes también puede desincronizar archivos existentes. Las funciones anónimas requieren un cuidado especial: debido a que sus nombres se generan automáticamente, cambios menores en el código pueden hacer que se renombren. Se debe evitar la serialización de funciones anónimas en archivos destinados a almacenamiento a largo plazo.

En algunos casos, el tamaño de palabra (32 o 64 bits) de las máquinas de lectura y escritura debe coincidir. En casos más raros, el sistema operativo o la arquitectura también deben coincidir, por ejemplo, al usar paquetes que contienen código dependiente de la plataforma.

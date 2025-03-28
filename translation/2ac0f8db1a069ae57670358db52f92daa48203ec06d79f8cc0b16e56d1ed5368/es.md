```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

Construye un `SharedArray` de un tipo de bits `T` y tamaño `dims` a través de los procesos especificados por `pids` - todos los cuales deben estar en el mismo host. Si `N` se especifica al llamar a `SharedArray{T,N}(dims)`, entonces `N` debe coincidir con la longitud de `dims`.

Si `pids` se deja sin especificar, el array compartido se mapeará a través de todos los procesos en el host actual, incluyendo el maestro. Sin embargo, `localindices` e `indexpids` solo se referirán a los procesos de trabajo. Esto facilita que el código de distribución de trabajo utilice trabajadores para el cálculo real, con el proceso maestro actuando como un controlador.

Si se especifica una función `init` del tipo `initfn(S::SharedArray)`, se llama en todos los trabajadores participantes.

El array compartido es válido mientras exista una referencia al objeto `SharedArray` en el nodo que creó el mapeo.

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

Construye un `SharedArray` respaldado por el archivo `filename`, con tipo de elemento `T` (debe ser un tipo de bits) y tamaño `dims`, a través de los procesos especificados por `pids` - todos los cuales deben estar en el mismo host. Este archivo se mapea en la memoria del host, con las siguientes consecuencias:

  * Los datos del array deben estar representados en formato binario (por ejemplo, un formato ASCII como CSV no puede ser soportado)
  * Cualquier cambio que realices en los valores del array (por ejemplo, `A[3] = 0`) también cambiará los valores en el disco

Si `pids` se deja sin especificar, el array compartido se mapeará a través de todos los procesos en el host actual, incluyendo el maestro. Sin embargo, `localindices` e `indexpids` solo se referirán a los procesos de trabajo. Esto facilita que el código de distribución de trabajo utilice trabajadores para el cálculo real, con el proceso maestro actuando como un controlador.

`mode` debe ser uno de `"r"`, `"r+"`, `"w+"`, o `"a+"`, y por defecto es `"r+"` si el archivo especificado por `filename` ya existe, o `"w+"` si no. Si se especifica una función `init` del tipo `initfn(S::SharedArray)`, se llama en todos los trabajadores participantes. No puedes especificar una función `init` si el archivo no es escribible.

`offset` te permite omitir el número especificado de bytes al principio del archivo.

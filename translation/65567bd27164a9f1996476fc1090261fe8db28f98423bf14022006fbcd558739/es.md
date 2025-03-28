```
mmap(io::Union{IOStream,AbstractString,Mmap.AnonymousMmap}[, type::Type{Array{T,N}}, dims, offset]; grow::Bool=true, shared::Bool=true)
mmap(type::Type{Array{T,N}}, dims)
```

Crea un `Array` cuyos valores están vinculados a un archivo, utilizando mapeo de memoria. Esto proporciona una forma conveniente de trabajar con datos demasiado grandes para caber en la memoria de la computadora.

El tipo es un `Array{T,N}` con un elemento de tipo bits `T` y dimensión `N` que determina cómo se interpretan los bytes del array. Ten en cuenta que el archivo debe estar almacenado en formato binario, y no se pueden realizar conversiones de formato (esta es una limitación de los sistemas operativos, no de Julia).

`dims` es una tupla o un solo [`Integer`](@ref) que especifica el tamaño o la longitud del array.

El archivo se pasa a través del argumento de flujo, ya sea como un [`IOStream`](@ref) abierto o como una cadena de nombre de archivo. Cuando inicializas el flujo, usa `"r"` para un array de "solo lectura", y `"w+"` para crear un nuevo array utilizado para escribir valores en el disco.

Si no se especifica un argumento `type`, el valor predeterminado es `Vector{UInt8}`.

Opcionalmente, puedes especificar un desplazamiento (en bytes) si, por ejemplo, deseas omitir un encabezado en el archivo. El valor predeterminado para el desplazamiento es la posición actual del flujo para un `IOStream`.

El argumento de palabra clave `grow` especifica si el archivo en disco debe crecer para acomodar el tamaño solicitado del array (si el tamaño total del archivo es < tamaño solicitado del array). Se requieren privilegios de escritura para hacer crecer el archivo.

El argumento de palabra clave `shared` especifica si el `Array` resultante y los cambios realizados en él serán visibles para otros procesos que mapeen el mismo archivo.

Por ejemplo, el siguiente código

```julia
# Crear un archivo para mmapping
# (también podrías usar mmap para hacer este paso)
using Mmap
A = rand(1:20, 5, 30)
s = open("/tmp/mmap.bin", "w+")
# Escribiremos las dimensiones del array como los primeros dos Ints en el archivo
write(s, size(A,1))
write(s, size(A,2))
# Ahora escribe los datos
write(s, A)
close(s)

# Prueba leyéndolo de nuevo
s = open("/tmp/mmap.bin")   # el predeterminado es solo lectura
m = read(s, Int)
n = read(s, Int)
A2 = mmap(s, Matrix{Int}, (m,n))
```

crea un `Matrix{Int}` de `m` por `n`, vinculado al archivo asociado con el flujo `s`.

Un archivo más portátil necesitaría codificar el tamaño de palabra – 32 bits o 64 bits – y la información de orden de bytes en el encabezado. En la práctica, considera codificar datos binarios utilizando formatos estándar como HDF5 (que se puede usar con mapeo de memoria).

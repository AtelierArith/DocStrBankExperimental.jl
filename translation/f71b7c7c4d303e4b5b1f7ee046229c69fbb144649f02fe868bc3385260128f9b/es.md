```
IOContext(io::IO, KV::Pair...)
```

Crea un `IOContext` que envuelve un flujo dado, añadiendo los pares `key=>value` especificados a las propiedades de ese flujo (ten en cuenta que `io` puede ser en sí mismo un `IOContext`).

  * usa `(key => value) in io` para ver si esta combinación particular está en el conjunto de propiedades
  * usa `get(io, key, default)` para recuperar el valor más reciente para una clave particular

Las siguientes propiedades son de uso común:

  * `:compact`: Booleano que especifica que los valores deben imprimirse de manera más compacta, por ejemplo, que los números deben imprimirse con menos dígitos. Esto se establece al imprimir elementos de un array. La salida `:compact` no debe contener saltos de línea.
  * `:limit`: Booleano que especifica que los contenedores deben ser truncados, por ejemplo, mostrando `…` en lugar de la mayoría de los elementos.
  * `:displaysize`: Un `Tuple{Int,Int}` que da el tamaño en filas y columnas a utilizar para la salida de texto. Esto se puede usar para anular el tamaño de visualización para funciones llamadas, pero para obtener el tamaño de la pantalla usa la función `displaysize`.
  * `:typeinfo`: un `Type` que caracteriza la información ya impresa sobre el tipo del objeto que está a punto de ser mostrado. Esto es principalmente útil al mostrar una colección de objetos del mismo tipo, para que se pueda evitar información de tipo redundante (por ejemplo, `[Float16(0)]` puede mostrarse como "Float16[0.0]" en lugar de "Float16[Float16(0.0)]": al mostrar los elementos del array, la propiedad `:typeinfo` se establecerá en `Float16`).
  * `:color`: Booleano que especifica si se admiten/se esperan códigos de color/escape ANSI. Por defecto, esto se determina por si `io` es un terminal compatible y por cualquier bandera de línea de comandos `--color` cuando se lanzó `julia`.

# Ejemplos

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generic function with 1 method)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```

```
show(io::IO, mime, x)
```

Las funciones [`display`](@ref) llaman en última instancia a `show` para escribir un objeto `x` como un tipo `mime` dado en un flujo de E/S `io` (generalmente un búfer de memoria), si es posible. Para proporcionar una representación multimedia rica de un tipo definido por el usuario `T`, solo es necesario definir un nuevo método `show` para `T`, a través de: `show(io, ::MIME"mime", x::T) = ...`, donde `mime` es una cadena de tipo MIME y el cuerpo de la función llama a [`write`](@ref) (o similar) para escribir esa representación de `x` en `io`. (Tenga en cuenta que la notación `MIME""` solo admite cadenas literales; para construir tipos `MIME` de manera más flexible, use `MIME{Symbol("")}`.)

Por ejemplo, si define un tipo `MyImage` y sabe cómo escribirlo en un archivo PNG, podría definir una función `show(io, ::MIME"image/png", x::MyImage) = ...` para permitir que sus imágenes se muestren en cualquier `AbstractDisplay` capaz de PNG (como IJulia). Como de costumbre, asegúrese de `import Base.show` para agregar nuevos métodos a la función incorporada de Julia `show`.

Técnicamente, la macro `MIME"mime"` define un tipo singleton para la cadena `mime` dada, lo que nos permite aprovechar los mecanismos de despacho de Julia para determinar cómo mostrar objetos de cualquier tipo dado.

El tipo MIME predeterminado es `MIME"text/plain"`. Hay una definición de respaldo para la salida `text/plain` que llama a `show` con 2 argumentos, por lo que no siempre es necesario agregar un método para ese caso. Sin embargo, si un tipo se beneficia de una salida personalizada legible por humanos, se debe definir `show(::IO, ::MIME"text/plain", ::T)`. Por ejemplo, el tipo `Day` utiliza `1 day` como salida para el tipo MIME `text/plain`, y `Day(1)` como salida de `show` de 2 argumentos.

# Ejemplos

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

Los tipos contenedores generalmente implementan `show` de 3 argumentos llamando a `show(io, MIME"text/plain"(), x)` para los elementos `x`, con `:compact => true` establecido en un [`IOContext`](@ref) pasado como el primer argumento.

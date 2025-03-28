```
@deprecate old new [export_old=true]
```

Desaprobación del método `old` y especificar la llamada de reemplazo `new`, definiendo un nuevo método `old` con la firma especificada en el proceso.

Para evitar que `old` sea exportado, establece `export_old` en `false`.

Ver también [`Base.depwarn()`](@ref).

!!! compat "Julia 1.5"
    A partir de Julia 1.5, las funciones definidas por `@deprecate` no imprimen advertencias cuando `julia` se ejecuta sin la opción `--depwarn=yes` establecida, ya que el valor predeterminado de la opción `--depwarn` es `no`. Las advertencias se imprimen desde las pruebas ejecutadas por `Pkg.test()`.


# Ejemplos

```jldoctest
julia> @deprecate old(x) new(x)
old (función genérica con 1 método)

julia> @deprecate old(x) new(x) false
old (función genérica con 1 método)
```

Las llamadas a `@deprecate` sin anotaciones de tipo explícitas definirán métodos desaprobados que aceptan cualquier número de argumentos posicionales y de palabras clave de tipo `Any`.

!!! compat "Julia 1.9"
    Los argumentos de palabras clave se reenvían cuando no hay una anotación de tipo explícita a partir de Julia 1.9. Para versiones anteriores, puedes reenviar manualmente los argumentos posicionales y de palabras clave haciendo `@deprecate old(args...; kwargs...) new(args...; kwargs...)`.


Para restringir la desaprobación a una firma específica, anota los argumentos de `old`. Por ejemplo,

```jldoctest; filter = r"@ .*"a
julia> new(x::Int) = x;

julia> new(x::Float64) = 2x;

julia> @deprecate old(x::Int) new(x);

julia> methods(old)
# 1 método para la función genérica "old" de Main:
 [1] old(x::Int64)
     @ deprecated.jl:94
```

definirá y desaprobará un método `old(x::Int)` que refleja `new(x::Int)` pero no definirá ni desaprobará el método `old(x::Float64)`.

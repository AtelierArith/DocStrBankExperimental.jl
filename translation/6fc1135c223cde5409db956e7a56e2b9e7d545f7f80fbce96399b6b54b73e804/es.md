```
invoke(f, argtypes::Type, args...; kwargs...)
```

Invoca un método para la función genérica dada `f` que coincide con los tipos especificados `argtypes` en los argumentos especificados `args` y pasando los argumentos de palabra clave `kwargs`. Los argumentos `args` deben conformarse con los tipos especificados en `argtypes`, es decir, la conversión no se realiza automáticamente. Este método permite invocar un método que no sea el método más específico que coincide, lo cual es útil cuando se necesita explícitamente el comportamiento de una definición más general (a menudo como parte de la implementación de un método más específico de la misma función).

Ten cuidado al usar `invoke` para funciones que no escribes. Qué definición se utiliza para los `argtypes` dados es un detalle de implementación a menos que la función indique explícitamente que llamar con ciertos `argtypes` es parte de la API pública. Por ejemplo, el cambio entre `f1` y `f2` en el ejemplo a continuación se considera generalmente compatible porque el cambio es invisible para el llamador con una llamada normal (no `invoke`). Sin embargo, el cambio es visible si usas `invoke`.

# Ejemplos

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```

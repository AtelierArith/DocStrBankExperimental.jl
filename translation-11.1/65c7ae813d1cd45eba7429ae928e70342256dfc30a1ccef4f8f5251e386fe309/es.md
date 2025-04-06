```
@ncallkw N f kw sym...
```

Genera una expresión de llamada a función con argumentos de palabra clave `kw...`. Como en el caso de [`@ncall`](@ref), `sym` representa cualquier número de argumentos de función, el último de los cuales puede ser una expresión de función anónima y se expande en `N` argumentos.

# Ejemplos

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```

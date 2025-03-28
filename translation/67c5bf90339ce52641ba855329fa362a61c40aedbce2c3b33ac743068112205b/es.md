```
^(x, y)
```

Operador de exponenciación.

Si `x` e `y` son enteros, el resultado puede desbordarse. Para ingresar números en notación científica, utiliza literales de [`Float64`](@ref) como `1.2e3` en lugar de `1.2 * 10^3`.

Si `y` es un literal `Int` (por ejemplo, `2` en `x^2` o `-3` en `x^-3`), el código de Julia `x^y` es transformado por el compilador a `Base.literal_pow(^, x, Val(y))`, para permitir la especialización en tiempo de compilación sobre el valor del exponente. (Como una opción de respaldo por defecto, tenemos `Base.literal_pow(^, x, Val(y)) = ^(x,y)`, donde generalmente `^ == Base.^` a menos que `^` haya sido definido en el espacio de nombres que llama.) Si `y` es un literal entero negativo, entonces `Base.literal_pow` transforma la operación a `inv(x)^-y` por defecto, donde `-y` es positivo.

Ver también [`exp2`](@ref), [`<<`](@ref).

# Ejemplos

```jldoctest
julia> 3^5
243

julia> 3^-1  # utiliza Base.literal_pow
0.3333333333333333

julia> p = -1;

julia> 3^p
ERROR: DomainError with -1:
Cannot raise an integer x to a negative power -1.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # desbordamiento entero
false

julia> big(10)^19 == 1e19
true
```

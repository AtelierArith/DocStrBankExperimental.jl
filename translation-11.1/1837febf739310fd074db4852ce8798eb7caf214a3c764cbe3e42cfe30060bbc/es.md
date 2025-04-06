```
*(x, y...)
```

Operador de multiplicación.

La infija `x*y*z*...` llama a esta función con todos los argumentos, es decir, `*(x, y, z, ...)`, que por defecto luego llama a `(x*y) * z * ...` comenzando desde la izquierda.

La yuxtaposición como `2pi` también llama a `*(2, pi)`. Tenga en cuenta que esta operación tiene una precedencia más alta que un literal `*`. También note que la yuxtaposición "0x..." (cero entero veces una variable cuyo nombre comienza con `x`) está prohibida ya que choca con los literales de enteros sin signo: `0x01 isa UInt8`.

Tenga en cuenta que el desbordamiento es posible para la mayoría de los tipos de enteros, incluido el `Int` por defecto, al multiplicar números grandes.

# Ejemplos

```jldoctest
julia> 2 * 7 * 8
112

julia> *(2, 7, 8)
112

julia> [2 0; 0 3] * [1, 10]  # matriz * vector
Vector de 2 elementos{Int64}:
  2
 30

julia> 1/2pi, 1/2*pi  # la yuxtaposición tiene mayor precedencia
(0.15915494309189535, 1.5707963267948966)

julia> x = [1, 2]; x'x  # vector adjunto * vector
5
```

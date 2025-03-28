```
parse(tipo, str; base)
```

Analiza una cadena como un número. Para los tipos `Integer`, se puede especificar una base (el valor predeterminado es 10). Para los tipos de punto flotante, la cadena se analiza como un número decimal de punto flotante. Los tipos `Complex` se analizan a partir de cadenas decimales de la forma `"R±Iim"` como un `Complex(R,I)` del tipo solicitado; `"i"` o `"j"` también se pueden usar en lugar de `"im"`, y `"R"` o `"Iim"` también son permitidos. Si la cadena no contiene un número válido, se genera un error.

!!! compat "Julia 1.1"
    `parse(Bool, str)` requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```

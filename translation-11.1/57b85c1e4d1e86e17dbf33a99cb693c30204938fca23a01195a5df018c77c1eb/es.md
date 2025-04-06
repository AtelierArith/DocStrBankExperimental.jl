```
escape_raw_string(s::AbstractString, delim='"') -> AbstractString
escape_raw_string(io, s::AbstractString, delim='"')
```

Escapa una cadena de la manera utilizada para analizar literales de cadena en bruto. Para cada carácter de comillas dobles (`"`) en la cadena de entrada `s` (o `delim` si se especifica), esta función cuenta el número *n* de caracteres de barra invertida (`\`) precedentes, y luego aumenta el número de barras invertidas de *n* a 2*n*+1 (incluso para *n* = 0). También duplica una secuencia de barras invertidas al final de la cadena.

Esta convención de escape se utiliza en cadenas en bruto y otros literales de cadena no estándar. (También resulta ser la convención de escape esperada por el tiempo de ejecución del compilador Microsoft C/C++ cuando analiza una cadena de línea de comandos en el arreglo argv[]).

Ver también [`escape_string`](@ref).

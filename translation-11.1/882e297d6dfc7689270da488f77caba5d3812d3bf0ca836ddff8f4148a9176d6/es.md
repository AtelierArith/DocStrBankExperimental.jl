```
join([io::IO,] iterator [, delim [, last]])
```

Une cualquier `iterator` en una sola cadena, insertando el delimitador dado (si lo hay) entre los elementos adyacentes. Si se proporciona `last`, se utilizará en lugar de `delim` entre los dos últimos elementos. Cada elemento de `iterator` se convierte en una cadena a través de `print(io::IOBuffer, x)`. Si se proporciona `io`, el resultado se escribe en `io` en lugar de devolverse como un `String`.

# Ejemplos

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```

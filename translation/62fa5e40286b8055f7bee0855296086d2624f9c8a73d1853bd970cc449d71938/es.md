```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

Busca el patrón dado `pat` en `s`, y reemplaza cada ocurrencia con `r`. Si se proporciona `count`, reemplaza como máximo `count` ocurrencias. `pat` puede ser un solo carácter, un vector o un conjunto de caracteres, una cadena o una expresión regular. Si `r` es una función, cada ocurrencia se reemplaza con `r(s)` donde `s` es la subcadena coincidente (cuando `pat` es un `AbstractPattern` o `AbstractString`) o carácter (cuando `pat` es un `AbstractChar` o una colección de `AbstractChar`). Si `pat` es una expresión regular y `r` es un [`SubstitutionString`](@ref), entonces las referencias de grupos de captura en `r` se reemplazan con el texto coincidente correspondiente. Para eliminar instancias de `pat` de `string`, establece `r` en la cadena vacía (`""`).

El valor de retorno es una nueva cadena después de los reemplazos. Si se proporciona el argumento `io::IO`, la cadena transformada se escribe en su lugar en `io` (devolviendo `io`). (Por ejemplo, esto se puede usar junto con un [`IOBuffer`](@ref) para reutilizar un arreglo de búfer preasignado en su lugar).

Se pueden especificar múltiples patrones, y se aplicarán de izquierda a derecha simultáneamente, por lo que solo se aplicará un patrón a cualquier carácter, y los patrones solo se aplicarán al texto de entrada, no a los reemplazos.

!!! compat "Julia 1.7"
    El soporte para múltiples patrones requiere la versión 1.7.


!!! compat "Julia 1.10"
    El argumento `io::IO` requiere la versión 1.10.


# Ejemplos

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```

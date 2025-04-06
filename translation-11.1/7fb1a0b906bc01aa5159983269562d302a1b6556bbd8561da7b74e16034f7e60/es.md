```
Int
```

Tipo de entero con signo de `Sys.WORD_SIZE` bits, `Int <: Signed <: Integer <: Real`.

Este es el tipo predeterminado de la mayoría de los literales enteros y es un alias para `Int32` o `Int64`, dependiendo de `Sys.WORD_SIZE`. Es el tipo devuelto por funciones como [`length`](@ref), y el tipo estándar para indexar arreglos.

Tenga en cuenta que los enteros desbordarán sin advertencia, por lo que `typemax(Int) + 1 < 0` y `10^19 < 0`. El desbordamiento se puede evitar utilizando [`BigInt`](@ref). Los literales enteros muy grandes utilizarán un tipo más amplio, por ejemplo, `10_000_000_000_000_000_000 isa Int128`.

La división entera es [`div`](@ref) alias `÷`, mientras que [`/`](@ref) que actúa sobre enteros devuelve [`Float64`](@ref).

Véase también [`Int64`](@ref), [`widen`](@ref), [`typemax`](@ref), [`bitstring`](@ref).

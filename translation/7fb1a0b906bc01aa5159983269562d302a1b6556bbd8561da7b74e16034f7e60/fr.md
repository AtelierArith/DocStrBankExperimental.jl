```
Int
```

Type entier signé de `Sys.WORD_SIZE` bits, `Int <: Signed <: Integer <: Real`.

C'est le type par défaut de la plupart des littéraux entiers et c'est un alias pour `Int32` ou `Int64`, selon `Sys.WORD_SIZE`. C'est le type retourné par des fonctions telles que [`length`](@ref), et le type standard pour l'indexation des tableaux.

Notez que les entiers débordent sans avertissement, donc `typemax(Int) + 1 < 0` et `10^19 < 0`. Le débordement peut être évité en utilisant [`BigInt`](@ref). Des littéraux entiers très grands utiliseront un type plus large, par exemple `10_000_000_000_000_000_000 isa Int128`.

La division entière est [`div`](@ref) alias `÷`, tandis que [`/`](@ref) agissant sur des entiers retourne [`Float64`](@ref).

Voir aussi [`Int64`](@ref), [`widen`](@ref), [`typemax`](@ref), [`bitstring`](@ref).

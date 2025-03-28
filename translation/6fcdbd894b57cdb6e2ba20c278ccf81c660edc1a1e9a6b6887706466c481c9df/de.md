```
rand([rng=default_rng()], [S], [dims...])
```

Wählen Sie ein zufälliges Element oder ein Array von zufälligen Elementen aus der Menge von Werten, die durch `S` angegeben sind; `S` kann sein

  * eine indexierbare Sammlung (zum Beispiel `1:9` oder `('x', "y", :z)`)
  * ein `AbstractDict` oder `AbstractSet` Objekt
  * ein String (als Sammlung von Zeichen betrachtet), oder
  * ein Typ aus der untenstehenden Liste, der der angegebenen Menge von Werten entspricht

      * konkrete Ganzzahltypen, die aus `typemin(S):typemax(S)` entnommen werden (außer [`BigInt`](@ref), das nicht unterstützt wird)
      * konkrete Gleitkommatypen, die aus `[0, 1)` entnommen werden
      * konkrete komplexe Typen `Complex{T}`, wenn `T` ein samplbarer Typ ist, nehmen Sie deren reale und imaginäre Komponenten unabhängig aus der Menge von Werten, die `T` entsprechen, werden jedoch nicht unterstützt, wenn `T` nicht samplbar ist.
      * alle `<:AbstractChar` Typen, die aus der Menge gültiger Unicode-Skalare entnommen werden
      * ein benutzerdefinierter Typ und eine Menge von Werten; für Implementierungsanleitungen siehe [Hooking into the `Random` API](@ref rand-api-hook)
      * ein Tupeltyp bekannter Größe, bei dem jeder Parameter von `S` selbst ein samplbarer Typ ist; geben Sie einen Wert des Typs `S` zurück. Beachten Sie, dass Tupeltypen wie `Tuple{Vararg{T}}` (unbekannte Größe) und `Tuple{1:2}` (parametrisiert mit einem Wert) nicht unterstützt werden
      * ein `Pair` Typ, z.B. `Pair{X, Y}`, sodass `rand` für `X` und `Y` definiert ist, in diesem Fall werden zufällige Paare erzeugt.

`S` hat standardmäßig den Wert [`Float64`](@ref). Wenn nur ein Argument neben dem optionalen `rng` übergeben wird und es sich um ein `Tuple` handelt, wird es als Sammlung von Werten (`S`) und nicht als `dims` interpretiert.

Siehe auch [`randn`](@ref) für normalverteilte Zahlen und [`rand!`](@ref) und [`randn!`](@ref) für die In-Place-Äquivalente.

!!! compat "Julia 1.1"
    Die Unterstützung für `S` als Tupel erfordert mindestens Julia 1.1.


!!! compat "Julia 1.11"
    Die Unterstützung für `S` als `Tuple` Typ erfordert mindestens Julia 1.11.


# Beispiele

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    Die Komplexität von `rand(rng, s::Union{AbstractDict,AbstractSet})` ist linear in der Länge von `s`, es sei denn, eine optimierte Methode mit konstanter Komplexität ist verfügbar, was bei `Dict`, `Set` und dichten `BitSet`s der Fall ist. Bei mehr als ein paar Aufrufen verwenden Sie stattdessen `rand(rng, collect(s))` oder entweder `rand(rng, Dict(s))` oder `rand(rng, Set(s))`, je nach Bedarf.


```
@view A[inds...]
```

Transformiere den Indizierungs-Ausdruck `A[inds...]` in den entsprechenden [`view`](@ref) Aufruf.

Dies kann nur direkt auf einen einzelnen Indizierungs-Ausdruck angewendet werden und ist besonders hilfreich für Ausdrücke, die die speziellen Indizierungssyntaxen `begin` oder `end` wie `A[begin, 2:end-1]` enthalten (da diese von der normalen [`view`](@ref) Funktion nicht unterstützt werden).

Beachte, dass `@view` nicht als Ziel einer regulären Zuweisung verwendet werden kann (z. B. `@view(A[1, 2:end]) = ...`), noch würde die un-dekorierte [indizierte Zuweisung](@ref man-indexed-assignment) (`A[1, 2:end] = ...`) oder die broadcastete indizierte Zuweisung (`A[1, 2:end] .= ...`) eine Kopie erstellen. Es kann jedoch nützlich sein, um *aktualisierte* broadcastete Zuweisungen wie `@view(A[1, 2:end]) .+= 1` zu verwenden, da dies eine einfache Syntax für `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1` ist, und der Indizierungs-Ausdruck auf der rechten Seite würde ansonsten ohne das `@view` eine Kopie erstellen.

Siehe auch [`@views`](@ref), um einen gesamten Block von Code auf die Verwendung von Views für nicht-skalare Indizierung umzustellen.

!!! compat "Julia 1.5"
    Die Verwendung von `begin` in einem Indizierungs-Ausdruck, um auf den ersten Index zu verweisen, erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```

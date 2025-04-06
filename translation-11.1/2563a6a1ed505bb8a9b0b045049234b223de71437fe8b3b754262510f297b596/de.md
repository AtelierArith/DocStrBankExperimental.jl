```
ldiv!(A, B)
```

Berechne `A \ B` in-place und überschreibe `B`, um das Ergebnis zu speichern.

Das Argument `A` sollte *keine* Matrix sein. Stattdessen sollte es ein Faktorisierungsobjekt sein (z. B. erzeugt durch [`factorize`](@ref) oder [`cholesky`](@ref)). Der Grund dafür ist, dass die Faktorisierung selbst sowohl teuer ist als auch typischerweise Speicher allokiert (obwohl sie auch in-place durchgeführt werden kann, z. B. durch [`lu!`](@ref)), und leistungs-kritische Situationen, die `ldiv!` erfordern, in der Regel auch eine feinkörnige Kontrolle über die Faktorisierung von `A` benötigen.

!!! Hinweis     Bestimmte strukturierte Matrizenarten, wie `Diagonal` und `UpperTriangular`, sind erlaubt, da diese bereits in einer faktorisierte Form vorliegen.

# Beispiele

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = copy(X);

julia> ldiv!(qr(A), X);

julia> X ≈ A\Y
true
```

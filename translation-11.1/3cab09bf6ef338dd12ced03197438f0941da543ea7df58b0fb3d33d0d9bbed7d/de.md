```
rank(A::AbstractMatrix; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Real)
```

Berechnen Sie den numerischen Rang einer Matrix, indem Sie zählen, wie viele Ausgaben von `svdvals(A)` größer sind als `max(atol, rtol*σ₁)`, wobei `σ₁` der größte berechnete Singularwert von `A` ist. `atol` und `rtol` sind die absoluten und relativen Toleranzen, respectively. Die standardmäßige relative Toleranz ist `n*ϵ`, wobei `n` die Größe der kleinsten Dimension von `A` ist und `ϵ` die [`eps`](@ref) des Elementtyps von `A`.

!!! note
    Der numerische Rang kann eine empfindliche und ungenaue Charakterisierung von schlecht konditionierten Matrizen mit Singularwerten sein, die nahe an der Schwellenwerttoleranz `max(atol, rtol*σ₁)` liegen. In solchen Fällen können geringfügige Störungen bei der Berechnung des Singularwerts oder an der Matrix das Ergebnis von `rank` ändern, indem ein oder mehrere Singularwerte über die Schwelle gedrückt werden. Diese Variationen können sogar aufgrund von Änderungen in den Gleitkommafehlern zwischen verschiedenen Julia-Versionen, Architekturen, Compilern oder Betriebssystemen auftreten.


!!! compat "Julia 1.1"
    Die Schlüsselwortargumente `atol` und `rtol` erfordern mindestens Julia 1.1. In Julia 1.0 ist `rtol` als positionsbasiertes Argument verfügbar, aber dies wird in Julia 2.0 veraltet sein.


# Beispiele

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```

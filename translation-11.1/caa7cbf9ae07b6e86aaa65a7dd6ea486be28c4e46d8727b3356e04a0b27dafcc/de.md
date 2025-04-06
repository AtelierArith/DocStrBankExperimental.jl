```
opnorm(A::AbstractMatrix, p::Real=2)
```

Berechne die Operatornorm (oder Matrizenorm), die durch die Vektor `p`-Norm induziert wird, wobei gültige Werte für `p` `1`, `2` oder `Inf` sind. (Beachte, dass für spärliche Matrizen `p=2` derzeit nicht implementiert ist.) Verwende [`norm`](@ref), um die Frobeniusnorm zu berechnen.

Wenn `p=1`, ist die Operatornorm die maximale absolute Spaltensumme von `A`:

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

mit $a_{ij}$ den Einträgen von `A`, und $m$ und $n$ seinen Dimensionen.

Wenn `p=2`, ist die Operatornorm die spektrale Norm, die dem größten singulären Wert von `A` entspricht.

Wenn `p=Inf`, ist die Operatornorm die maximale absolute Zeilensumme von `A`:

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# Beispiele

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```

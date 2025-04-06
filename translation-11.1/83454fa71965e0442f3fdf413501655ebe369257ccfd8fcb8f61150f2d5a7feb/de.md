```
norm(A, p::Real=2)
```

Für jeden iterierbaren Container `A` (einschließlich Arrays beliebiger Dimension) von Zahlen (oder jedem Elementtyp, für den `norm` definiert ist), berechne die `p`-Norm (standardmäßig `p=2`), als ob `A` ein Vektor der entsprechenden Länge wäre.

Die `p`-Norm ist definiert als

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

wobei $a_i$ die Einträge von `A` sind, $| a_i |$ die [`norm`](@ref) von $a_i$ ist und $n$ die Länge von `A` ist. Da die `p`-Norm unter Verwendung der [`norm`](@ref)s der Einträge von `A` berechnet wird, ist die `p`-Norm eines Vektors von Vektoren im Allgemeinen nicht mit der Interpretation als Blockvektor kompatibel, wenn `p != 2`.

`p` kann jeden numerischen Wert annehmen (auch wenn nicht alle Werte eine mathematisch gültige Vektornorm erzeugen). Insbesondere gibt `norm(A, Inf)` den größten Wert in `abs.(A)` zurück, während `norm(A, -Inf)` den kleinsten zurückgibt. Wenn `A` eine Matrix ist und `p=2`, dann entspricht dies der Frobenius-Norm.

Das zweite Argument `p` ist nicht unbedingt Teil der Schnittstelle für `norm`, d.h. ein benutzerdefinierter Typ kann nur `norm(A)` ohne zweites Argument implementieren.

Verwende [`opnorm`](@ref), um die Operatornorm einer Matrix zu berechnen.

# Beispiele

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```

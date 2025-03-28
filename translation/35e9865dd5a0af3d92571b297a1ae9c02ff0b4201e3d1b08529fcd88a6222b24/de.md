```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

Geben Sie an, dass eine Sortierfunktion den Algorithmus der partiellen schnellen Sortierung verwenden sollte. `PartialQuickSort(k)` ist wie `QuickSort`, muss jedoch nur die Elemente finden und sortieren, die in `v[k]` landen würden, wenn `v` vollständig sortiert wäre.

Eigenschaften:

  * *nicht stabil*: bewahrt nicht die Reihenfolge von Elementen, die gleich sind (z. B. "a" und "A" in einer Sortierung von Buchstaben, die die Groß- und Kleinschreibung ignoriert).
  * *in-place* im Speicher.
  * *teilen und erobern*: Sortierstrategie ähnlich wie [`MergeSort`](@ref).

Beachten Sie, dass `PartialQuickSort(k)` nicht unbedingt das gesamte Array sortiert. Zum Beispiel,

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```

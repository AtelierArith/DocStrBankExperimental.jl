# Sorting and Related Functions

Julia verfügt über eine umfangreiche, flexible API zum Sortieren und Interagieren mit bereits sortierten Arrays von Werten. Standardmäßig wählt Julia angemessene Algorithmen und sortiert in aufsteigender Reihenfolge:

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

Sie können auch in umgekehrter Reihenfolge sortieren:

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort` erstellt eine sortierte Kopie, ohne die Eingabe zu ändern. Verwenden Sie die "Bang"-Version der Sortierfunktion, um ein vorhandenes Array zu verändern:

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

Anstatt ein Array direkt zu sortieren, können Sie eine Permutation der Indizes des Arrays berechnen, die das Array in sortierter Reihenfolge anordnet:

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Arrays können gemäß einer willkürlichen Transformation ihrer Werte sortiert werden:

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

Oder in umgekehrter Reihenfolge durch eine Transformation:

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

Falls erforderlich, kann der Sortieralgorithmus ausgewählt werden:

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Alle Sortier- und ordnungsbezogenen Funktionen basieren auf einer "kleiner als" Relation, die eine [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) der zu manipulierenden Werte definiert. Die `isless`-Funktion wird standardmäßig aufgerufen, aber die Relation kann über das `lt`-Schlüsselwort angegeben werden, eine Funktion, die zwei Array-Elemente entgegennimmt und `true` zurückgibt, wenn und nur wenn das erste Argument "kleiner als" das zweite ist. Siehe [`sort!`](@ref) und [Alternate Orderings](@ref) für weitere Informationen.

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

Derzeit sind vier Sortieralgorithmen öffentlich in der Basis-Julia verfügbar:

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

Standardmäßig verwendet die `sort`-Familie von Funktionen stabile Sortieralgorithmen, die bei den meisten Eingaben schnell sind. Die genaue Wahl des Algorithmus ist ein Implementierungsdetail, um zukünftige Leistungsverbesserungen zu ermöglichen. Derzeit wird ein Hybrid aus `RadixSort`, `ScratchQuickSort`, `InsertionSort` und `CountingSort` basierend auf Eingabetyp, Größe und Zusammensetzung verwendet. Implementierungsdetails können sich ändern, sind aber derzeit in der erweiterten Hilfe von `??Base.DEFAULT_STABLE` und den Docstrings der dort aufgeführten internen Sortieralgorithmen verfügbar.

Sie können Ihren bevorzugten Algorithmus explizit mit dem `alg`-Schlüsselwort angeben (z. B. `sort!(v, alg=PartialQuickSort(10:20))`) oder den Standard-Sortieralgorithmus für benutzerdefinierte Typen neu konfigurieren, indem Sie eine spezialisierte Methode zur Funktion `Base.Sort.defalg` hinzufügen. Zum Beispiel definiert [InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903) die folgende Methode:

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    Der Standard-Sortieralgorithmus (zurückgegeben von `Base.Sort.defalg`) ist seit Julia 1.9 garantiert stabil. Frühere Versionen hatten instabile Randfälle beim Sortieren von numerischen Arrays.


## Alternate Orderings

Standardmäßig verwenden `sort`, `searchsorted` und verwandte Funktionen [`isless`](@ref), um zwei Elemente zu vergleichen und zu bestimmen, welches zuerst kommen sollte. Der [`Base.Order.Ordering`](@ref) abstrakte Typ bietet einen Mechanismus zur Definition alternativer Sortierungen für dasselbe Set von Elementen: Beim Aufrufen einer Sortierfunktion wie `sort!` kann eine Instanz von `Ordering` mit dem Schlüsselwortargument `order` bereitgestellt werden.

Instanzen von `Ordering` definieren eine Ordnung durch die [`Base.Order.lt`](@ref)-Funktion, die als Verallgemeinerung von `isless` fungiert. Das Verhalten dieser Funktion bei benutzerdefinierten `Ordering`s muss alle Bedingungen eines [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) erfüllen. Siehe [`sort!`](@ref) für Details und Beispiele gültiger und ungültiger `lt`-Funktionen.

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```

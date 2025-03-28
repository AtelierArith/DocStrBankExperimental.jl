# Interfaces

Ein großer Teil der Leistungsfähigkeit und Erweiterbarkeit in Julia stammt aus einer Sammlung informeller Schnittstellen. Durch die Erweiterung einiger spezifischer Methoden, um mit einem benutzerdefinierten Typ zu arbeiten, erhalten Objekte dieses Typs nicht nur diese Funktionalitäten, sondern sie können auch in anderen Methoden verwendet werden, die allgemein darauf aufbauen, diese Verhaltensweisen zu nutzen.

## [Iteration](@id man-interface-iteration)

Es gibt zwei Methoden, die immer erforderlich sind:

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

Es gibt mehrere weitere Methoden, die unter bestimmten Umständen definiert werden sollten. Bitte beachten Sie, dass Sie immer mindestens eine der folgenden Methoden definieren sollten: `Base.IteratorSize(IterType)` und `length(iter)`, da die Standarddefinition von `Base.IteratorSize(IterType)` `Base.HasLength()` ist.

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

Die sequenzielle Iteration wird durch die [`iterate`](@ref)-Funktion implementiert. Anstatt Objekte während der Iteration zu verändern, können Julia-Iteratoren den Iterationsstatus extern vom Objekt verfolgen. Der Rückgabewert von iterate ist immer entweder ein Tupel aus einem Wert und einem Status oder `nothing`, wenn keine Elemente mehr vorhanden sind. Das Statusobjekt wird bei der nächsten Iteration an die iterate-Funktion zurückgegeben und wird im Allgemeinen als Implementierungsdetail betrachtet, das privat zum iterierbaren Objekt gehört.

Jedes Objekt, das diese Funktion definiert, ist iterierbar und kann in der [many functions that rely upon iteration](@ref lib-collections-iteration) verwendet werden. Es kann auch direkt in einer [`for`](@ref) Schleife verwendet werden, da die Syntax:

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

ist übersetzt in:

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

Ein einfaches Beispiel ist eine iterierbare Sequenz von Quadrat-Zahlen mit einer definierten Länge:

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

Mit nur der Definition [`iterate`](@ref) ist der `Squares`-Typ bereits ziemlich leistungsfähig. Wir können über alle Elemente iterieren:

```jldoctest squaretype
julia> for item in Squares(7)
           println(item)
       end
1
4
9
16
25
36
49
```

Wir können viele der eingebauten Methoden verwenden, die mit Iterables arbeiten, wie [`in`](@ref) oder [`sum`](@ref):

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

Es gibt noch einige weitere Methoden, die wir erweitern können, um Julia mehr Informationen über diese iterable Sammlung zu geben. Wir wissen, dass die Elemente in einer `Squares`-Sequenz immer `Int` sein werden. Indem wir die [`eltype`](@ref)-Methode erweitern, können wir Julia diese Informationen geben und ihr helfen, spezialisierteren Code in den komplizierteren Methoden zu erstellen. Wir wissen auch die Anzahl der Elemente in unserer Sequenz, also können wir auch [`length`](@ref) erweitern:

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

Jetzt, wenn wir Julia bitten, [`collect`](@ref) alle Elemente in ein Array zu packen, kann sie einen `Vector{Int}` der richtigen Größe vorab zuweisen, anstatt naiv [`push!`](@ref) jedes Element in einen `Vector{Any}` zu packen:

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

Während wir uns auf generische Implementierungen verlassen können, können wir auch spezifische Methoden erweitern, wenn wir wissen, dass es einen einfacheren Algorithmus gibt. Zum Beispiel gibt es eine Formel zur Berechnung der Summe der Quadrate, sodass wir die generische iterative Version mit einer leistungsfähigeren Lösung überschreiben können:

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

Dies ist ein sehr häufiges Muster in Julia Base: Eine kleine Menge erforderlicher Methoden definiert ein informelles Interface, das viele ausgefeiltere Verhaltensweisen ermöglicht. In einigen Fällen möchten Typen zusätzlich diese zusätzlichen Verhaltensweisen spezialisieren, wenn sie wissen, dass ein effizienterer Algorithmus in ihrem spezifischen Fall verwendet werden kann.

Es ist auch oft nützlich, die Iteration über eine Sammlung in *umgekehrter Reihenfolge* zu ermöglichen, indem man über [`Iterators.reverse(iterator)`](@ref) iteriert. Um jedoch die Iteration in umgekehrter Reihenfolge tatsächlich zu unterstützen, muss ein Iterator-Typ `T` `iterate` für `Iterators.Reverse{T}` implementieren. (Gegeben `r::Iterators.Reverse{T}` ist der zugrunde liegende Iterator vom Typ `T` `r.itr`.) In unserem Beispiel `Squares` würden wir die Methoden `Iterators.Reverse{Squares}` implementieren:

```jldoctest squaretype
julia> Base.iterate(rS::Iterators.Reverse{Squares}, state=rS.itr.count) = state < 1 ? nothing : (state*state, state-1)

julia> collect(Iterators.reverse(Squares(4)))
4-element Vector{Int64}:
 16
  9
  4
  1
```

## Indexing

| Methods to implement | Brief description                                             |
|:-------------------- |:------------------------------------------------------------- |
| `getindex(X, i)`     | `X[i]`, indexed access, non-scalar `i` should allocate a copy |
| `setindex!(X, v, i)` | `X[i] = v`, indexed assignment                                |
| `firstindex(X)`      | The first index, used in `X[begin]`                           |
| `lastindex(X)`       | The last index, used in `X[end]`                              |

Für das `Squares`-Iterable oben können wir das `i`te Element der Sequenz leicht berechnen, indem wir es quadrieren. Wir können dies als einen Indexausdruck `S[i]` bereitstellen. Um dieses Verhalten zu aktivieren, muss `Squares` einfach [`getindex`](@ref) definieren:

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

Zusätzlich müssen wir zur Unterstützung der Syntax `S[begin]` und `S[end]` [`firstindex`](@ref) und [`lastindex`](@ref) definieren, um die ersten und letzten gültigen Indizes anzugeben.

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

Für mehrdimensionale `begin`/`end` Indizierung wie in `a[3, begin, 7]`, sollten Sie `firstindex(a, dim)` und `lastindex(a, dim)` definieren (die standardmäßig `first` und `last` auf `axes(a, dim)` aufrufen).

Beachten Sie jedoch, dass das Obige *nur* [`getindex`](@ref) mit einem ganzzahligen Index definiert. Das Indizieren mit etwas anderem als einem `Int` führt zu einer [`MethodError`](@ref), die besagt, dass keine übereinstimmende Methode gefunden wurde. Um das Indizieren mit Bereichen oder Vektoren von `Int`s zu unterstützen, müssen separate Methoden geschrieben werden:

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

Während dies beginnt, mehr von den [indexing operations supported by some of the builtin types](@ref man-array-indexing) zu unterstützen, fehlen immer noch eine ganze Reihe von Verhaltensweisen. Diese `Squares`-Sequenz beginnt, immer mehr wie ein Vektor auszusehen, da wir Verhaltensweisen hinzugefügt haben. Anstatt all diese Verhaltensweisen selbst zu definieren, können wir es offiziell als einen Untertyp von [`AbstractArray`](@ref) definieren.

## [Abstract Arrays](@id man-interface-array)

| Methods to implement                     |                                        | Brief description                                                                                                                                                |
|:---------------------------------------- |:-------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `size(A)`                                |                                        | Returns a tuple containing the dimensions of `A`                                                                                                                 |
| `getindex(A, i::Int)`                    |                                        | (if `IndexLinear`) Linear scalar indexing                                                                                                                        |
| `getindex(A, I::Vararg{Int, N})`         |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexing                                                                                        |
| **Optional methods**                     | **Default definition**                 | **Brief description**                                                                                                                                            |
| `IndexStyle(::Type)`                     | `IndexCartesian()`                     | Returns either `IndexLinear()` or `IndexCartesian()`. See the description below.                                                                                 |
| `setindex!(A, v, i::Int)`                |                                        | (if `IndexLinear`) Scalar indexed assignment                                                                                                                     |
| `setindex!(A, v, I::Vararg{Int, N})`     |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexed assignment                                                                              |
| `getindex(A, I...)`                      | defined in terms of scalar `getindex`  | [Multidimensional and nonscalar indexing](@ref man-array-indexing)                                                                                               |
| `setindex!(A, X, I...)`                  | defined in terms of scalar `setindex!` | [Multidimensional and nonscalar indexed assignment](@ref man-array-indexing)                                                                                     |
| `iterate`                                | defined in terms of scalar `getindex`  | Iteration                                                                                                                                                        |
| `length(A)`                              | `prod(size(A))`                        | Number of elements                                                                                                                                               |
| `similar(A)`                             | `similar(A, eltype(A), size(A))`       | Return a mutable array with the same shape and element type                                                                                                      |
| `similar(A, ::Type{S})`                  | `similar(A, S, size(A))`               | Return a mutable array with the same shape and the specified element type                                                                                        |
| `similar(A, dims::Dims)`                 | `similar(A, eltype(A), dims)`          | Return a mutable array with the same element type and size *dims*                                                                                                |
| `similar(A, ::Type{S}, dims::Dims)`      | `Array{S}(undef, dims)`                | Return a mutable array with the specified element type and size                                                                                                  |
| **Non-traditional indices**              | **Default definition**                 | **Brief description**                                                                                                                                            |
| `axes(A)`                                | `map(OneTo, size(A))`                  | Return a tuple of `AbstractUnitRange{<:Integer}` of valid indices. The axes should be their own axes, that is `axes.(axes(A),1) == axes(A)` should be satisfied. |
| `similar(A, ::Type{S}, inds)`            | `similar(A, S, Base.to_shape(inds))`   | Return a mutable array with the specified indices `inds` (see below)                                                                                             |
| `similar(T::Union{Type,Function}, inds)` | `T(Base.to_shape(inds))`               | Return an array similar to `T` with the specified indices `inds` (see below)                                                                                     |

Wenn ein Typ als Untertyp von `AbstractArray` definiert ist, erbt er eine sehr große Menge an reichhaltigen Verhaltensweisen, einschließlich Iteration und mehrdimensionalem Indexing, das auf dem Zugriff auf einzelne Elemente basiert. Siehe die [arrays manual page](@ref man-multi-dim-arrays) und die [Julia Base section](@ref lib-arrays) für weitere unterstützte Methoden.

Ein wichtiger Bestandteil bei der Definition eines `AbstractArray`-Untertyps ist [`IndexStyle`](@ref). Da das Indizieren ein so wichtiger Teil eines Arrays ist und oft in heißen Schleifen vorkommt, ist es wichtig, sowohl das Indizieren als auch die indizierte Zuweisung so effizient wie möglich zu gestalten. Array-Datenstrukturen werden typischerweise auf eine von zwei Arten definiert: Entweder greift sie am effizientesten mit nur einem Index auf ihre Elemente zu (lineares Indizieren) oder sie greift intrinsisch mit für jede Dimension angegebenen Indizes auf die Elemente zu. Diese beiden Modalitäten werden von Julia als `IndexLinear()` und `IndexCartesian()` identifiziert. Die Umwandlung eines linearen Index in mehrere Indizierungsunterskripte ist typischerweise sehr kostspielig, daher bietet dies einen traits-basierten Mechanismus, um effizienten generischen Code für alle Array-Typen zu ermöglichen.

Diese Unterscheidung bestimmt, welche skalaren Indexierungsmethoden der Typ definieren muss. `IndexLinear()`-Arrays sind einfach: Definieren Sie einfach `getindex(A::ArrayType, i::Int)`. Wenn das Array anschließend mit einer mehrdimensionalen Menge von Indizes indiziert wird, konvertiert die Fallback-Methode `getindex(A::AbstractArray, I...)` die Indizes effizient in einen linearen Index und ruft dann die oben genannte Methode auf. `IndexCartesian()`-Arrays hingegen erfordern, dass Methoden für jede unterstützte Dimensionalität mit `ndims(A)` `Int`-Indizes definiert werden. Zum Beispiel unterstützt [`SparseMatrixCSC`](@ref) aus dem Standardbibliotheksmodul `SparseArrays` nur zwei Dimensionen, daher definiert es nur `getindex(A::SparseMatrixCSC, i::Int, j::Int)`. Das Gleiche gilt für [`setindex!`](@ref).

Zurück zur oben genannten Sequenz der Quadrate könnten wir sie stattdessen als eine Unterart von `AbstractArray{Int, 1}` definieren:

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

Beachten Sie, dass es sehr wichtig ist, die beiden Parameter des `AbstractArray` anzugeben; der erste definiert die [`eltype`](@ref), und der zweite definiert die [`ndims`](@ref). Dieser Supertyp und diese drei Methoden sind alles, was es braucht, damit `SquaresVector` ein durchlaufbares, indizierbares und vollständig funktionales Array ist:

```jldoctest squarevectype
julia> s = SquaresVector(4)
4-element SquaresVector:
  1
  4
  9
 16

julia> s[s .> 8]
2-element Vector{Int64}:
  9
 16

julia> s + s
4-element Vector{Int64}:
  2
  8
 18
 32

julia> sin.(s)
4-element Vector{Float64}:
  0.8414709848078965
 -0.7568024953079282
  0.4121184852417566
 -0.2879033166650653
```

Als ein komplizierteres Beispiel definieren wir unseren eigenen Spielzeug-N-dimensionalen spärlichen Array-Typ, der auf [`Dict`](@ref) basiert:

```jldoctest squarevectype
julia> struct SparseArray{T,N} <: AbstractArray{T,N}
           data::Dict{NTuple{N,Int}, T}
           dims::NTuple{N,Int}
       end

julia> SparseArray(::Type{T}, dims::Int...) where {T} = SparseArray(T, dims);

julia> SparseArray(::Type{T}, dims::NTuple{N,Int}) where {T,N} = SparseArray{T,N}(Dict{NTuple{N,Int}, T}(), dims);

julia> Base.size(A::SparseArray) = A.dims

julia> Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where {T} = SparseArray(T, dims)

julia> Base.getindex(A::SparseArray{T,N}, I::Vararg{Int,N}) where {T,N} = get(A.data, I, zero(T))

julia> Base.setindex!(A::SparseArray{T,N}, v, I::Vararg{Int,N}) where {T,N} = (A.data[I] = v)
```

Beachten Sie, dass dies ein `IndexCartesian`-Array ist, daher müssen wir [`getindex`](@ref) und [`setindex!`](@ref) manuell in der Dimensionalität des Arrays definieren. Im Gegensatz zum `SquaresVector` sind wir in der Lage, `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566` zu definieren, und so können wir das Array mutieren:

```jldoctest squarevectype
julia> A = SparseArray(Float64, 3, 3)
3×3 SparseArray{Float64, 2}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2)
3×3 SparseArray{Float64, 2}:
 2.0  2.0  2.0
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> A[:] = 1:length(A); A
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

The result of indexing an `AbstractArray` can itself be an array (for instance when indexing by an `AbstractRange`). The `AbstractArray` fallback methods use [`similar`](@ref) to allocate an `Array` of the appropriate size and element type, which is filled in using the basic indexing method described above. However, when implementing an array wrapper you often want the result to be wrapped as well:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

In diesem Beispiel wird dies erreicht, indem `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where T` definiert wird, um das entsprechende umschlossene Array zu erstellen. (Beachten Sie, dass `similar` 1- und 2-Argument-Formen unterstützt, Sie in den meisten Fällen jedoch nur die 3-Argument-Form spezialisieren müssen.) Damit dies funktioniert, ist es wichtig, dass `SparseArray` veränderlich ist (unterstützt `setindex!`). Die Definition von `similar`, `getindex` und `setindex!` für `SparseArray` macht es auch möglich, das Array zu [`copy`](@ref) zu bearbeiten:

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

Neben all den oben genannten iterierbaren und indexierbaren Methoden können diese Typen auch miteinander interagieren und die meisten der in Julia Base für `AbstractArrays` definierten Methoden verwenden:

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

Wenn Sie einen Array-Typ definieren, der nicht-traditionelle Indizes (Indizes, die nicht bei 1 beginnen) zulässt, sollten Sie [`axes`](@ref) spezialisieren. Sie sollten auch [`similar`](@ref) spezialisieren, damit das Argument `dims` (gewöhnlich ein `Dims`-Größentupel) `AbstractUnitRange`-Objekte akzeptieren kann, möglicherweise Bereichs-Typen `Ind` Ihres eigenen Designs. Für weitere Informationen siehe [Arrays with custom indices](@ref man-custom-indices).

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

Ein gestreutes Array ist ein Untertyp von `AbstractArray`, dessen Einträge im Speicher mit festen Schritten gespeichert sind. Vorausgesetzt, der Elementtyp des Arrays ist mit BLAS kompatibel, kann ein gestreutes Array BLAS- und LAPACK-Routinen für effizientere lineare Algebra-Routinen nutzen. Ein typisches Beispiel für ein benutzerdefiniertes gestreutes Array ist eines, das ein Standard-`Array` mit zusätzlicher Struktur umschließt.

Warnung: Implementieren Sie diese Methoden nicht, wenn der zugrunde liegende Speicher nicht tatsächlich gestreift ist, da dies zu falschen Ergebnissen oder Segmentierungsfehlern führen kann.

Hier sind einige Beispiele, um zu demonstrieren, welche Arten von Arrays gestreckt sind und welche nicht:

```julia
1:5   # not strided (there is no storage associated with this array.)
Vector(1:5)  # is strided with strides (1,)
A = [1 5; 2 6; 3 7; 4 8]  # is strided with strides (1,4)
V = view(A, 1:2, :)   # is strided with strides (1,4)
V = view(A, 1:2:3, 1:2)   # is strided with strides (2,4)
V = view(A, [1,2,4], :)   # is not strided, as the spacing between rows is not fixed.
```

## [Customizing broadcasting](@id man-interfaces-broadcasting)

| Methods to implement                                       | Brief description                                                  |
|:---------------------------------------------------------- |:------------------------------------------------------------------ |
| `Base.BroadcastStyle(::Type{SrcType}) = SrcStyle()`        | Broadcasting behavior of `SrcType`                                 |
| `Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})` | Allocation of output container                                     |
| **Optional methods**                                       |                                                                    |
| `Base.BroadcastStyle(::Style1, ::Style2) = Style12()`      | Precedence rules for mixing styles                                 |
| `Base.axes(x)`                                             | Declaration of the indices of `x`, as per [`axes(x)`](@ref).       |
| `Base.broadcastable(x)`                                    | Convert `x` to an object that has `axes` and supports indexing     |
| **Bypassing default machinery**                            |                                                                    |
| `Base.copy(bc::Broadcasted{DestStyle})`                    | Custom implementation of `broadcast`                               |
| `Base.copyto!(dest, bc::Broadcasted{DestStyle})`           | Custom implementation of `broadcast!`, specializing on `DestStyle` |
| `Base.copyto!(dest::DestType, bc::Broadcasted{Nothing})`   | Custom implementation of `broadcast!`, specializing on `DestType`  |
| `Base.Broadcast.broadcasted(f, args...)`                   | Override the default lazy behavior within a fused expression       |
| `Base.Broadcast.instantiate(bc::Broadcasted{DestStyle})`   | Override the computation of the lazy broadcast's axes              |

[Broadcasting](@ref) wird durch einen expliziten Aufruf von `broadcast` oder `broadcast!` ausgelöst, oder implizit durch "Punkt"-Operationen wie `A .+ b` oder `f.(x, y)`. Jedes Objekt, das [`axes`](@ref) hat und Indizierung unterstützt, kann als Argument beim Broadcasting teilnehmen, und standardmäßig wird das Ergebnis in einem `Array` gespeichert. Dieses grundlegende Framework ist auf drei Hauptarten erweiterbar:

  * Sicherstellen, dass alle Argumente Broadcast unterstützen
  * Auswahl eines geeigneten Ausgabearrays für die gegebene Argumentenmenge
  * Auswahl einer effizienten Implementierung für die gegebene Argumentenmenge

Nicht alle Typen unterstützen `axes` und Indizierung, aber viele sind praktisch, um im Broadcast zuzulassen. Die Funktion [`Base.broadcastable`](@ref) wird auf jedes Argument angewendet, um zu broadcasten, wodurch sie etwas zurückgeben kann, das `axes` und Indizierung unterstützt. Standardmäßig ist dies die Identitätsfunktion für alle `AbstractArray`s und `Number`s — sie unterstützen bereits `axes` und Indizierung.

Wenn ein Typ dazu gedacht ist, wie ein "0-dimensionaler Skalar" (ein einzelnes Objekt) zu agieren, anstatt als Container für Broadcasting zu fungieren, sollte die folgende Methode definiert werden:

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

das gibt das Argument zurück, das in einem 0-dimensionalen [`Ref`](@ref) Container eingewickelt ist. Zum Beispiel ist eine solche Wrapper-Methode für Typen selbst, Funktionen, spezielle Singletons wie [`missing`](@ref) und [`nothing`](@ref) sowie für Daten definiert.

Benutzerdefinierte array-ähnliche Typen können `Base.broadcastable` spezialisieren, um ihre Form zu definieren, sollten jedoch der Konvention folgen, dass `collect(Base.broadcastable(x)) == collect(x)`. Eine bemerkenswerte Ausnahme ist `AbstractString`; Strings sind speziell behandelt, um sich für die Zwecke des Broadcasts wie Skalare zu verhalten, obwohl sie iterable Sammlungen ihrer Zeichen sind (siehe [Strings](@ref) für mehr).

Die nächsten beiden Schritte (die Auswahl des Ausgabearrays und die Implementierung) hängen davon ab, eine einzige Antwort für eine gegebene Menge von Argumenten zu bestimmen. Broadcast muss alle unterschiedlichen Typen seiner Argumente nehmen und sie auf nur ein Ausgabearray und eine Implementierung reduzieren. Broadcast nennt diese einzelne Antwort einen "Stil". Jedes broadcastbare Objekt hat seinen eigenen bevorzugten Stil, und ein systemähnliches Promotionssystem wird verwendet, um diese Stile zu einer einzigen Antwort zu kombinieren — dem "Zielstil".

### Broadcast Styles

`Base.BroadcastStyle` ist der abstrakte Typ, von dem alle Broadcast-Stile abgeleitet sind. Wenn er als Funktion verwendet wird, hat er zwei mögliche Formen, unär (einzelnes Argument) und binär. Die unäre Variante besagt, dass Sie beabsichtigen, ein spezifisches Broadcast-Verhalten und/oder einen spezifischen Ausgabetyp zu implementieren und nicht auf den Standard-Fallback [`Broadcast.DefaultArrayStyle`](@ref) angewiesen sein möchten.

Um diese Standardwerte zu überschreiben, können Sie einen benutzerdefinierten `BroadcastStyle` für Ihr Objekt definieren:

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

In einigen Fällen kann es praktisch sein, `MyStyle` nicht definieren zu müssen, in diesem Fall können Sie einen der allgemeinen Broadcast-Wrapper nutzen:

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()` kann für beliebige Typen verwendet werden.
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()` wird bevorzugt, wenn `MyType` ein `AbstractArray` ist.
  * Für `AbstractArrays`, die nur eine bestimmte Dimensionalität unterstützen, erstellen Sie einen Untertyp von `Broadcast.AbstractArrayStyle{N}` (siehe unten).

Wenn Ihr Broadcast-Vorgang mehrere Argumente umfasst, werden die einzelnen Argumentstile kombiniert, um einen einzelnen `DestStyle` zu bestimmen, der den Typ des Ausgabebehälters steuert. Für weitere Details siehe [below](@ref writing-binary-broadcasting-rules).

### Selecting an appropriate output array

Der Broadcast-Stil wird für jede Broadcast-Operation berechnet, um die Ausführung und Spezialisierung zu ermöglichen. Die tatsächliche Zuweisung des Ergebnisarrays wird von `similar` übernommen, wobei das Broadcasted-Objekt als erstes Argument verwendet wird.

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

Die Fallback-Definition ist

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

Wenn nötig, können Sie sich jedoch auf eines oder alle diese Argumente spezialisieren. Das letzte Argument `bc` ist eine faule Darstellung einer (potenziell fusionierten) Broadcast-Operation, ein `Broadcasted`-Objekt. Für diese Zwecke sind die wichtigsten Felder des Wrappers `f` und `args`, die die Funktion und die Argumentliste beschreiben. Beachten Sie, dass die Argumentliste andere geschachtelte `Broadcasted`-Wrapper enthalten kann – und dies oft auch tut.

Für ein vollständiges Beispiel nehmen wir an, dass Sie einen Typ `ArrayAndChar` erstellt haben, der ein Array und ein einzelnes Zeichen speichert:

```jldoctest ArrayAndChar; output = false
struct ArrayAndChar{T,N} <: AbstractArray{T,N}
    data::Array{T,N}
    char::Char
end
Base.size(A::ArrayAndChar) = size(A.data)
Base.getindex(A::ArrayAndChar{T,N}, inds::Vararg{Int,N}) where {T,N} = A.data[inds...]
Base.setindex!(A::ArrayAndChar{T,N}, val, inds::Vararg{Int,N}) where {T,N} = A.data[inds...] = val
Base.showarg(io::IO, A::ArrayAndChar, toplevel) = print(io, typeof(A), " with char '", A.char, "'")
# output

```

Sie möchten möglicherweise, dass das Broadcasting die `char` "Metadaten" beibehält. Zuerst definieren wir

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

Das bedeutet, dass wir auch eine entsprechende `similar`-Methode definieren müssen:

```jldoctest ArrayAndChar; output = false
function Base.similar(bc::Broadcast.Broadcasted{Broadcast.ArrayStyle{ArrayAndChar}}, ::Type{ElType}) where ElType
    # Scan the inputs for the ArrayAndChar:
    A = find_aac(bc)
    # Use the char field of A to create the output
    ArrayAndChar(similar(Array{ElType}, axes(bc)), A.char)
end

"`A = find_aac(As)` returns the first ArrayAndChar among the arguments."
find_aac(bc::Base.Broadcast.Broadcasted) = find_aac(bc.args)
find_aac(args::Tuple) = find_aac(find_aac(args[1]), Base.tail(args))
find_aac(x) = x
find_aac(::Tuple{}) = nothing
find_aac(a::ArrayAndChar, rest) = a
find_aac(::Any, rest) = find_aac(rest)
# output
find_aac (generic function with 6 methods)
```

Aus diesen Definitionen ergibt sich folgendes Verhalten:

```jldoctest ArrayAndChar
julia> a = ArrayAndChar([1 2; 3 4], 'x')
2×2 ArrayAndChar{Int64, 2} with char 'x':
 1  2
 3  4

julia> a .+ 1
2×2 ArrayAndChar{Int64, 2} with char 'x':
 2  3
 4  5

julia> a .+ [5,10]
2×2 ArrayAndChar{Int64, 2} with char 'x':
  6   7
 13  14
```

### [Extending broadcast with custom implementations](@id extending-in-place-broadcast)

Im Allgemeinen wird eine Broadcast-Operation durch einen faulen `Broadcasted`-Container dargestellt, der die anzuwendende Funktion zusammen mit ihren Argumenten speichert. Diese Argumente können selbst weitere verschachtelte `Broadcasted`-Container sein, die einen großen Ausdrucksbaum bilden, der ausgewertet werden soll. Ein verschachtelter Baum von `Broadcasted`-Containern wird direkt durch die implizite Punkt-Syntax konstruiert; `5 .+ 2.*x` wird vorübergehend durch `Broadcasted(+, 5, Broadcasted(*, 2, x))` dargestellt, zum Beispiel. Dies ist für die Benutzer unsichtbar, da es sofort durch einen Aufruf von `copy` realisiert wird, aber es ist dieser Container, der die Grundlage für die Erweiterbarkeit des Broadcasts für Autoren benutzerdefinierter Typen bietet. Die integrierte Broadcast-Mechanik bestimmt dann den Ergebnistyp und die Größe basierend auf den Argumenten, allokiert sie und kopiert schließlich die Realisierung des `Broadcasted`-Objekts mit einer Standardmethode `copyto!(::AbstractArray, ::Broadcasted)` hinein. Die integrierten Fallback-Methoden `broadcast` und `broadcast!` konstruieren ebenfalls eine vorübergehende `Broadcasted`-Darstellung der Operation, damit sie denselben Codepfad folgen können. Dies ermöglicht benutzerdefinierten Array-Implementierungen, ihre eigene `copyto!`-Spezialisierung bereitzustellen, um das Broadcasting anzupassen und zu optimieren. Dies wird wiederum durch den berechneten Broadcast-Stil bestimmt. Dies ist ein so wichtiger Teil der Operation, dass er als erster Typ-Parameter des `Broadcasted`-Typs gespeichert wird, was Dispatch und Spezialisierung ermöglicht.

Für einige Typen ist die Maschine, um Operationen über verschachtelte Ebenen der Broadcasting zu "fusionieren", nicht verfügbar oder könnte effizienter inkrementell durchgeführt werden. In solchen Fällen müssen Sie möglicherweise oder möchten `x .* (x .+ 1)` so auswerten, als wäre es geschrieben worden als `broadcast(*, x, broadcast(+, x, 1))`, wobei die innere Operation vor der äußeren Operation ausgewertet wird. Diese Art von eifriger Operation wird durch ein wenig Indirektion direkt unterstützt; anstatt direkt `Broadcasted`-Objekte zu konstruieren, senkt Julia den fusionierten Ausdruck `x .* (x .+ 1)` auf `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))`. Jetzt ruft `broadcasted` standardmäßig einfach den `Broadcasted`-Konstruktor auf, um die faule Darstellung des fusionierten Ausdrucksbaums zu erstellen, aber Sie können wählen, ihn für eine bestimmte Kombination von Funktion und Argumenten zu überschreiben.

Als Beispiel verwenden die eingebauten `AbstractRange`-Objekte diese Mechanik, um Teile von broadcasteten Ausdrücken zu optimieren, die rein in Bezug auf den Start, den Schritt und die Länge (oder den Stopp) eifrig ausgewertet werden können, anstatt jedes einzelne Element zu berechnen. Genau wie die gesamte andere Mechanik berechnet und gibt `broadcasted` auch den kombinierten Broadcast-Stil seiner Argumente an, sodass Sie anstelle von `broadcasted(f, args...)` auf `broadcasted(::DestStyle, f, args...)` für jede Kombination aus Stil, Funktion und Argumenten spezialisieren können.

Zum Beispiel unterstützt die folgende Definition die Negation von Bereichen:

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

In-Place-Broadcasting kann unterstützt werden, indem die entsprechende `copyto!(dest, bc::Broadcasted)`-Methode definiert wird. Da Sie möglicherweise entweder auf `dest` oder den spezifischen Untertyp von `bc` spezialisieren möchten, empfehlen wir zur Vermeidung von Mehrdeutigkeiten zwischen Paketen die folgende Konvention.

Wenn Sie sich auf einen bestimmten Stil `DestStyle` spezialisieren möchten, definieren Sie eine Methode für

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

Optional können Sie mit diesem Formular auch auf den Typ von `dest` spezialisieren.

Wenn Sie stattdessen auf den Zieltyp `DestType` spezialisieren möchten, ohne sich auf `DestStyle` zu spezialisieren, sollten Sie eine Methode mit der folgenden Signatur definieren:

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

Dies nutzt eine Fallback-Implementierung von `copyto!`, die den Wrapper in ein `Broadcasted{Nothing}` umwandelt. Folglich hat die Spezialisierung auf `DestType` eine geringere Priorität als Methoden, die auf `DestStyle` spezialisiert sind.

Ähnlich können Sie das fehlplatzierte Broadcasting vollständig mit einer `copy(::Broadcasted)`-Methode überschreiben.

#### Working with `Broadcasted` objects

Um eine solche `copy` oder `copyto!` Methode zu implementieren, müssen Sie natürlich mit dem `Broadcasted` Wrapper arbeiten, um jedes Element zu berechnen. Es gibt zwei Hauptwege, dies zu tun:

  * `Broadcast.flatten` berechnet die potenziell geschachtelte Operation in eine einzelne Funktion und eine flache Liste von Argumenten um. Sie sind selbst dafür verantwortlich, die Regeln für die Broadcasting-Formate zu implementieren, aber dies kann in bestimmten Situationen hilfreich sein.
  * Iterieren über die `CartesianIndices` der `axes(::Broadcasted)` und die Verwendung von Indizes mit dem resultierenden `CartesianIndex`-Objekt zur Berechnung des Ergebnisses.

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

Die Vorrangregeln werden durch binäre `BroadcastStyle`-Aufrufe definiert:

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

wo `Style12` der `BroadcastStyle` ist, den Sie für Ausgaben wählen möchten, die Argumente von `Style1` und `Style2` betreffen. Zum Beispiel,

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

zeigt an, dass `Tuple` über null-dimensionale Arrays "gewinnt" (der Ausgabebehälter wird ein Tuple sein). Es ist erwähnenswert, dass Sie nicht beide Argumentreihenfolgen dieses Aufrufs definieren müssen (und sollten); es reicht aus, eine zu definieren, egal in welcher Reihenfolge der Benutzer die Argumente bereitstellt.

Für `AbstractArray`-Typen ersetzt die Definition eines `BroadcastStyle` die Fallback-Wahl, [`Broadcast.DefaultArrayStyle`](@ref). `DefaultArrayStyle` und der abstrakte Supertyp `AbstractArrayStyle` speichern die Dimensionalität als Typ-Parameter, um spezialisierte Array-Typen zu unterstützen, die feste Dimensionalitätsanforderungen haben.

`DefaultArrayStyle` "verliert" gegen jede andere `AbstractArrayStyle`, die definiert wurde, aufgrund der folgenden Methoden:

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

Sie müssen keine binären `BroadcastStyle`-Regeln schreiben, es sei denn, Sie möchten eine Reihenfolge für zwei oder mehr nicht-`DefaultArrayStyle`-Typen festlegen.

Wenn Ihr Array-Typ feste Dimensionierungsanforderungen hat, sollten Sie `AbstractArrayStyle` untertypen. Zum Beispiel hat der Sparse-Array-Code die folgenden Definitionen:

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

Wann immer Sie `AbstractArrayStyle` untertypen, müssen Sie auch Regeln für die Kombination von Dimensionen definieren, indem Sie einen Konstruktor für Ihren Stil erstellen, der ein `Val(N)`-Argument akzeptiert. Zum Beispiel:

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

Diese Regeln besagen, dass die Kombination eines `SparseVecStyle` mit 0- oder 1-dimensionalen Arrays einen weiteren `SparseVecStyle` ergibt, dass seine Kombination mit einem 2-dimensionalen Array einen `SparseMatStyle` ergibt und alles mit höherer Dimensionalität auf das dichte, beliebig dimensionale Framework zurückfällt. Diese Regeln ermöglichen es dem Broadcasting, die spärliche Darstellung für Operationen beizubehalten, die ein- oder zweidimensionale Ausgaben ergeben, aber ein `Array` für jede andere Dimensionalität zu erzeugen.

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

Manchmal ist es wünschenswert, die Interaktion des Endbenutzers mit den Feldern eines Objekts zu ändern. Anstatt direkten Zugriff auf die Typfelder zu gewähren, kann eine zusätzliche Abstraktionsebene zwischen dem Benutzer und dem Code bereitgestellt werden, indem `object.field` überladen wird. Eigenschaften sind das, was der Benutzer *vom* Objekt *sieht*, Felder sind das, was das Objekt *tatsächlich ist*.

Standardmäßig sind Eigenschaften und Felder gleich. Dieses Verhalten kann jedoch geändert werden. Zum Beispiel, nehmen Sie diese Darstellung eines Punktes in einer Ebene in [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system):

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

Wie in der obigen Tabelle beschrieben, ist der Punktzugriff `p.r` dasselbe wie `getproperty(p, :r)`, was standardmäßig dasselbe ist wie `getfield(p, :r)`:

```jldoctest polartype
julia> propertynames(p)
(:r, :ϕ)

julia> getproperty(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)

julia> p.r, p.ϕ
(7.0, 0.7853981633974483)

julia> getfield(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)
```

Wir möchten jedoch, dass die Benutzer nicht wissen, dass `Point` die Koordinaten als `r` und `ϕ` (Felder) speichert, und stattdessen mit `x` und `y` (Eigenschaften) interagieren. Die Methoden in der ersten Spalte können definiert werden, um neue Funktionalitäten hinzuzufügen:

```jldoctest polartype
julia> Base.propertynames(::Point, private::Bool=false) = private ? (:x, :y, :r, :ϕ) : (:x, :y)

julia> function Base.getproperty(p::Point, s::Symbol)
           if s === :x
               return getfield(p, :r) * cos(getfield(p, :ϕ))
           elseif s === :y
               return getfield(p, :r) * sin(getfield(p, :ϕ))
           else
               # This allows accessing fields with p.r and p.ϕ
               return getfield(p, s)
           end
       end

julia> function Base.setproperty!(p::Point, s::Symbol, f)
           if s === :x
               y = p.y
               setfield!(p, :r, sqrt(f^2 + y^2))
               setfield!(p, :ϕ, atan(y, f))
               return f
           elseif s === :y
               x = p.x
               setfield!(p, :r, sqrt(x^2 + f^2))
               setfield!(p, :ϕ, atan(f, x))
               return f
           else
               # This allow modifying fields with p.r and p.ϕ
               return setfield!(p, s, f)
           end
       end
```

Es ist wichtig, dass `getfield` und `setfield` innerhalb von `getproperty` und `setproperty!` anstelle der Punkt-Syntax verwendet werden, da die Punkt-Syntax die Funktionen rekursiv machen würde, was zu Problemen bei der Typinferenz führen kann. Wir können jetzt die neue Funktionalität ausprobieren:

```jldoctest polartype
julia> propertynames(p)
(:x, :y)

julia> p.x
4.949747468305833

julia> p.y = 4.0
4.0

julia> p.r
6.363961030678928
```

Schließlich ist es erwähnenswert, dass das Hinzufügen von Instanz-Eigenschaften auf diese Weise in Julia ziemlich selten vorkommt und im Allgemeinen nur dann erfolgen sollte, wenn es einen guten Grund dafür gibt.

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

Um das Runden für einen neuen Typ zu unterstützen, ist es typischerweise ausreichend, die einzelne Methode `round(x::ObjType, r::RoundingMode)` zu definieren. Der übergebene Rundungsmodus bestimmt, in welche Richtung der Wert gerundet werden soll. Die am häufigsten verwendeten Rundungsmodi sind `RoundNearest`, `RoundToZero`, `RoundDown` und `RoundUp`, da diese Rundungsmodi in den Definitionen der einargigen `round`-Methode sowie von `trunc`, `floor` und `ceil` verwendet werden.

In einigen Fällen ist es möglich, eine dre argumentige `round`-Methode zu definieren, die genauer oder leistungsfähiger ist als die zwe argumentige Methode, gefolgt von einer Konvertierung. In diesem Fall ist es akzeptabel, die dre argumentige Methode zusätzlich zur zwe argumentigen Methode zu definieren. Wenn es unmöglich ist, das gerundete Ergebnis als ein Objekt des Typs `T` darzustellen, sollte die dre argumentige Methode einen `InexactError` auslösen.

Zum Beispiel, wenn wir einen `Interval`-Typ haben, der einen Bereich möglicher Werte darstellt, ähnlich wie https://github.com/JuliaPhysics/Measurements.jl, können wir das Runden für diesen Typ wie folgt definieren:

```jldoctest
julia> struct Interval{T}
           min::T
           max::T
       end

julia> Base.round(x::Interval, r::RoundingMode) = Interval(round(x.min, r), round(x.max, r))

julia> x = Interval(1.7, 2.2)
Interval{Float64}(1.7, 2.2)

julia> round(x)
Interval{Float64}(2.0, 2.0)

julia> floor(x)
Interval{Float64}(1.0, 2.0)

julia> ceil(x)
Interval{Float64}(2.0, 3.0)

julia> trunc(x)
Interval{Float64}(1.0, 2.0)
```

```
=
```

`=` ist der Zuweisungsoperator.

  * Für die Variable `a` und den Ausdruck `b` bewirkt `a = b`, dass `a` auf den Wert von `b` verweist.
  * Für Funktionen `f(x)` definiert `f(x) = x` eine neue Funktionskonstante `f` oder fügt `f` eine neue Methode hinzu, wenn `f` bereits definiert ist; diese Verwendung entspricht `function f(x); x; end`.
  * `a[i] = v` ruft [`setindex!`](@ref)`(a,v,i)` auf.
  * `a.b = c` ruft [`setproperty!`](@ref)`(a,:b,c)` auf.
  * Innerhalb eines Funktionsaufrufs übergibt `f(a=b)` `b` als den Wert des Schlüsselwortarguments `a`.
  * Innerhalb von Klammern mit Kommas konstruiert `(a=1,)` ein [`NamedTuple`](@ref).

# Beispiele

Die Zuweisung von `a` zu `b` erstellt keine Kopie von `b`; stattdessen verwenden Sie [`copy`](@ref) oder [`deepcopy`](@ref).

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

Sammlungen, die an Funktionen übergeben werden, werden ebenfalls nicht kopiert. Funktionen können den Inhalt der Objekte, auf die ihre Argumente verweisen, ändern (mutieren). (Die Namen von Funktionen, die dies tun, enden konventionell mit '!'.)

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generische Funktion mit 1 Methode)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

Die Zuweisung kann parallel auf mehrere Variablen wirken und Werte aus einem iterierbaren Objekt übernehmen:

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

Die Zuweisung kann seriell auf mehrere Variablen wirken und gibt den Wert des am weitesten rechts stehenden Ausdrucks zurück:

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

Die Zuweisung an Indizes außerhalb der Grenzen vergrößert eine Sammlung nicht. Wenn die Sammlung ein [`Vector`](@ref) ist, kann sie stattdessen mit [`push!`](@ref) oder [`append!`](@ref) vergrößert werden.

```jldoctest
julia> a = [1, 1]; a[3] = 2
ERROR: BoundsError: Versuch, auf 2-element Array{Int64, 1} an Index [3] zuzugreifen
[...]

julia> push!(a, 2, 3)
4-element Array{Int64, 1}:
 1
 1
 2
 3

```

Die Zuweisung von `[]` entfernt keine Elemente aus einer Sammlung; stattdessen verwenden Sie [`filter!`](@ref).

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
ERROR: DimensionMismatch: Versuch, 0 Elemente an 1 Ziel zuzuweisen
[...]

julia> filter!(x -> x > 1, a) # in-place & somit effizienter als a = a[a .> 1]
2-element Array{Int64, 1}:
 2
 3

```

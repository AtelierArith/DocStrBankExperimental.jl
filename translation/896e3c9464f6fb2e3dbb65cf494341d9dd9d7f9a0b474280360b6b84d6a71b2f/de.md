```
Stateful(itr)
```

Es gibt mehrere verschiedene Möglichkeiten, über diesen Iterator-Wrap zu denken:

1. Es bietet einen veränderbaren Wrapper um einen Iterator und seinen Iterationszustand.
2. Es verwandelt eine iteratorähnliche Abstraktion in eine `Channel`-ähnliche Abstraktion.
3. Es ist ein Iterator, der sich verändert, um sein eigener Rest-Iterator zu werden, wann immer ein Element produziert wird.

`Stateful` bietet die reguläre Iterator-Schnittstelle. Wie andere veränderbare Iteratoren (z.B. [`Base.Channel`](@ref)), kann die Iteration, wenn sie vorzeitig gestoppt wird (z.B. durch ein [`break`](@ref) in einer [`for`](@ref) Schleife), von derselben Stelle aus fortgesetzt werden, indem man weiterhin über dasselbe Iterator-Objekt iteriert (im Gegensatz dazu würde ein unveränderlicher Iterator von Anfang an neu starten).

# Beispiele

```jldoctest
julia> a = Iterators.Stateful("abcdef");

julia> isempty(a)
false

julia> popfirst!(a)
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> collect(Iterators.take(a, 3))
3-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'c': ASCII/Unicode U+0063 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'd': ASCII/Unicode U+0064 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> collect(a)
2-element Vector{Char}:
 'e': ASCII/Unicode U+0065 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'f': ASCII/Unicode U+0066 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> Iterators.reset!(a); popfirst!(a)
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> Iterators.reset!(a, "hello"); popfirst!(a)
'h': ASCII/Unicode U+0068 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```

```jldoctest
julia> a = Iterators.Stateful([1,1,1,2,3,4]);

julia> for x in a; x == 1 || break; end

julia> peek(a)
3

julia> sum(a) # Summe der verbleibenden Elemente
7
```

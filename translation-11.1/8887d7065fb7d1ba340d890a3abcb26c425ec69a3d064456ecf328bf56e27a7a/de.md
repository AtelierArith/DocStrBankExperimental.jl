```
@kwdef typedef
```

Dies ist ein Hilfsmakro, das automatisch einen konstruktorspezifischen Konstruktor für den in dem Ausdruck `typedef` deklarierten Typ definiert, der ein `struct` oder `mutable struct` Ausdruck sein muss. Das Standardargument wird bereitgestellt, indem Felder der Form `field::T = default` oder `field = default` deklariert werden. Wenn kein Standard bereitgestellt wird, wird das Schlüsselwortargument zu einem erforderlichen Schlüsselwortargument im resultierenden Typkonstruktor.

Innere Konstruktoren können weiterhin definiert werden, aber mindestens einer sollte Argumente in derselben Form wie der Standardinnere Konstruktor akzeptieren (d.h. ein positionsbasiertes Argument pro Feld), um korrekt mit dem äußeren Schlüsselwortkonstruktor zu funktionieren.

!!! compat "Julia 1.1"
    `Base.@kwdef` für parametrische Strukturen und Strukturen mit Supertypen erfordert mindestens Julia 1.1.


!!! compat "Julia 1.9"
    Dieses Makro wird seit Julia 1.9 exportiert.


# Beispiele

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # spezifiziertes Standard
           b::String          # erforderliches Schlüsselwort
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
ERROR: UndefKeywordError: Schlüsselwortargument `b` nicht zugewiesen
Stacktrace:
[...]
```

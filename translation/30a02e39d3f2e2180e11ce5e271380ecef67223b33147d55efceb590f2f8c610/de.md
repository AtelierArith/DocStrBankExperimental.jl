```
a ? b : c
```

Kurze Form für Bedingungen; lese "wenn `a`, bewerte `b`, andernfalls bewerte `c`". Auch bekannt als der [ternäre Operator](https://en.wikipedia.org/wiki/%3F:).

Diese Syntax ist äquivalent zu `if a; b else c end`, wird jedoch oft verwendet, um den Wert `b`-oder-`c` zu betonen, der als Teil eines größeren Ausdrucks verwendet wird, anstatt die Nebenwirkungen, die die Bewertung von `b` oder `c` haben kann.

Siehe den Handbuchabschnitt über [Kontrollfluss](@ref man-conditional-evaluation) für weitere Details.

# Beispiele

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x ist größer") : println("x ist nicht größer")
x ist nicht größer

julia> x > y ? "x ist größer" : x == y ? "x und y sind gleich" : "y ist größer"
"y ist größer"
```

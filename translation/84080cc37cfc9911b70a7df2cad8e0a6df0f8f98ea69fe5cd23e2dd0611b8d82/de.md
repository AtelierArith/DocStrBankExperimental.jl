```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

Verkettet Zeichenfolgen und/oder Zeichen und erzeugt eine [`String`](@ref) oder [`AnnotatedString`](@ref) (je nach Bedarf). Dies entspricht dem Aufruf der Funktion [`string`](@ref) oder [`annotatedstring`](@ref) mit den Argumenten. Die Verkettung von eingebauten Zeichenfolgen-Typen erzeugt immer einen Wert des Typs `String`, aber andere Zeichenfolgen-Typen können wählen, eine Zeichenfolge eines anderen Typs zurückzugeben, wenn dies angemessen ist.

# Beispiele

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```

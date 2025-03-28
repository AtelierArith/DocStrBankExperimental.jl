```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

Konvertiere ein iterierbares `itr` von Bytes, das einen hexadezimalen String darstellt, in seine binäre Darstellung, ähnlich wie [`hex2bytes`](@ref), mit dem Unterschied, dass die Ausgabe in-place in `dest` geschrieben wird. Die Länge von `dest` muss die Hälfte der Länge von `itr` sein.

!!! compat "Julia 1.7"
    Der Aufruf von hex2bytes! mit Iteratoren, die UInt8 erzeugen, erfordert Version 1.7. In früheren Versionen kannst du das Iterable vor dem Aufruf sammeln.


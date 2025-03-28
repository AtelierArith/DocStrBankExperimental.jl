```
@cfunction(callable, Rückgabetyp, (ArgumentTypen...,)) -> Ptr{Cvoid}
@cfunction($callable, Rückgabetyp, (ArgumentTypen...,)) -> CFunction
```

Generieren Sie einen C-aufrufbaren Funktionszeiger aus der Julia-Funktion `callable` für die angegebene Typ-Signatur. Um den Rückgabewert an einen `ccall` zu übergeben, verwenden Sie den Argumenttyp `Ptr{Cvoid}` in der Signatur.

Beachten Sie, dass das Argumenttyp-Tupel ein literales Tupel sein muss und keine Tupel-Variable oder -Ausdruck (obwohl es einen Splat-Ausdruck enthalten kann). Und dass diese Argumente zur Compile-Zeit im globalen Gültigkeitsbereich ausgewertet werden (nicht bis zur Laufzeit verschoben). Ein '$' vor dem Funktionsargument ändert dies, um stattdessen eine Laufzeit-Closure über die lokale Variable `callable` zu erstellen (dies wird nicht auf allen Architekturen unterstützt).

Siehe [Handbuchabschnitt zu ccall und cfunction Verwendung](@ref Calling-C-and-Fortran-Code).

# Beispiele

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```

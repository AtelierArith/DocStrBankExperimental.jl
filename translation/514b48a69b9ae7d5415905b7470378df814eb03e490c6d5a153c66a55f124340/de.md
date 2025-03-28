```
cconvert(T,x)
```

Konvertiere `x` in einen Wert, der als Typ `T` an C-Code übergeben werden kann, typischerweise durch Aufruf von `convert(T, x)`.

In Fällen, in denen `x` nicht sicher in `T` konvertiert werden kann, kann `cconvert`, im Gegensatz zu [`convert`](@ref), ein Objekt eines Typs zurückgeben, der sich von `T` unterscheidet, das jedoch für [`unsafe_convert`](@ref) geeignet ist. Das Ergebnis dieser Funktion sollte gültig gehalten werden (für den GC), bis das Ergebnis von [`unsafe_convert`](@ref) nicht mehr benötigt wird. Dies kann verwendet werden, um Speicher zuzuweisen, der vom `ccall` verwendet wird. Wenn mehrere Objekte zugewiesen werden müssen, kann ein Tupel der Objekte als Rückgabewert verwendet werden.

Weder `convert` noch `cconvert` sollten ein Julia-Objekt nehmen und es in einen `Ptr` umwandeln.

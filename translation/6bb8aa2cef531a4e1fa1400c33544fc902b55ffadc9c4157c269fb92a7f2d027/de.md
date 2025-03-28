```
ccall((function_name, library), returntype, (argtype1, ...), argvalue1, ...)
ccall(function_name, returntype, (argtype1, ...), argvalue1, ...)
ccall(function_pointer, returntype, (argtype1, ...), argvalue1, ...)
```

Rufen Sie eine Funktion in einer C-exportierten Shared Library auf, die durch das Tupel `(function_name, library)` angegeben ist, wobei jede Komponente entweder eine Zeichenkette oder ein Symbol ist. Anstelle der Angabe einer Bibliothek kann auch ein `function_name`-Symbol oder eine Zeichenkette verwendet werden, das im aktuellen Prozess aufgelöst wird. Alternativ kann `ccall` auch verwendet werden, um einen Funktionszeiger `function_pointer` aufzurufen, wie er beispielsweise von `dlsym` zurückgegeben wird.

Beachten Sie, dass das Tupel der Argumenttypen ein literales Tupel sein muss und keine Tupel-Variable oder -Ausdruck.

Jeder `argvalue`, der an den `ccall` übergeben wird, wird in den entsprechenden `argtype` umgewandelt, indem automatisch Aufrufe von `unsafe_convert(argtype, cconvert(argtype, argvalue))` eingefügt werden. (Siehe auch die Dokumentation für [`unsafe_convert`](@ref Base.unsafe_convert) und [`cconvert`](@ref Base.cconvert) für weitere Details.) In den meisten Fällen führt dies einfach zu einem Aufruf von `convert(argtype, argvalue)`.

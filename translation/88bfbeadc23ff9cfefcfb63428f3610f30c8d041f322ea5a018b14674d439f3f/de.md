```
pointer(array [, index])
```

Holen Sie sich die native Adresse eines Arrays oder Strings, optional an einem bestimmten Ort `index`.

Diese Funktion ist "unsicher". Seien Sie vorsichtig, um sicherzustellen, dass eine Julia-Referenz auf `array` existiert, solange dieser Zeiger verwendet wird. Das [`GC.@preserve`](@ref) Makro sollte verwendet werden, um das `array`-Argument innerhalb eines bestimmten Codeblocks vor der Garbage Collection zu schützen.

Das Aufrufen von [`Ref(array[, index])`](@ref Ref) ist im Allgemeinen vorzuziehen, da es die Gültigkeit garantiert.

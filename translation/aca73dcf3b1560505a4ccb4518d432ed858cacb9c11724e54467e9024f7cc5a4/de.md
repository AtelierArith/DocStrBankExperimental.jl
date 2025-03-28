```
unsafe_pointer_to_objref(p::Ptr)
```

Konvertiert einen `Ptr` in eine Objektreferenz. Geht davon aus, dass der Zeiger auf ein gültiges, im Heap zugewiesenes Julia-Objekt verweist. Wenn dies nicht der Fall ist, führt dies zu undefiniertem Verhalten, weshalb diese Funktion als "unsicher" gilt und mit Vorsicht verwendet werden sollte.

Siehe auch [`pointer_from_objref`](@ref).

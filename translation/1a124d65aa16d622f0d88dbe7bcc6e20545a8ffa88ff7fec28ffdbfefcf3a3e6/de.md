```
reset(s::IO)
```

Setzt einen Stream `s` auf eine zuvor markierte Position zurück und entfernt die Markierung. Gibt die zuvor markierte Position zurück. Wirft einen Fehler, wenn der Stream nicht markiert ist.

Siehe auch [`mark`](@ref), [`unmark`](@ref), [`ismarked`](@ref).

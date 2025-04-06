```
isready(rr::RemoteChannel, args...)
```

Bestimmen Sie, ob ein [`RemoteChannel`](@ref) einen Wert gespeichert hat. Beachten Sie, dass diese Funktion zu Wettlaufbedingungen führen kann, da es sein kann, dass es nicht mehr zutrifft, bis Sie das Ergebnis erhalten. Es kann jedoch sicher auf einem [`Future`](@ref) verwendet werden, da diese nur einmal zugewiesen werden.

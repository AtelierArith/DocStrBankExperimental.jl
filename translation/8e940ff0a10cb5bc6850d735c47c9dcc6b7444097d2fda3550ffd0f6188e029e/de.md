```
@inbounds(blk)
```

Eliminiert die Überprüfung der Array-Grenzen innerhalb von Ausdrücken.

Im folgenden Beispiel wird die Überprüfung, ob der Index `i` des Arrays `A` im gültigen Bereich liegt, übersprungen, um die Leistung zu verbessern.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! warning
    Die Verwendung von `@inbounds` kann zu falschen Ergebnissen/Abstürzen/Korruption für Indizes außerhalb der Grenzen führen. Der Benutzer ist verantwortlich für die manuelle Überprüfung. Verwenden Sie `@inbounds` nur, wenn sicher ist, dass alle Zugriffe im gültigen Bereich liegen, basierend auf den lokal verfügbaren Informationen. Insbesondere ist die Verwendung von `1:length(A)` anstelle von `eachindex(A)` in einer Funktion wie der obigen *nicht* sicher in den Grenzen, da der erste Index von `A` für alle benutzerdefinierten Typen, die von `AbstractArray` abgeleitet sind, möglicherweise nicht `1` ist.


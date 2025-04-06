```
__init__
```

Die Funktion `__init__()` in einem Modul wird sofort *nachdem* das Modul zur Laufzeit zum ersten Mal geladen wird, ausgeführt. Sie wird einmal aufgerufen, nachdem alle anderen Anweisungen im Modul ausgeführt wurden. Da sie nach dem vollständigen Import des Moduls aufgerufen wird, werden die `__init__`-Funktionen der Untermodule zuerst ausgeführt. Zwei typische Verwendungen von `__init__` sind das Aufrufen von Laufzeitinitialisierungsfunktionen externer C-Bibliotheken und das Initialisieren globaler Konstanten, die Zeiger enthalten, die von externen Bibliotheken zurückgegeben werden. Siehe den [Handbuchabschnitt über Module](@ref modules) für weitere Details.

# Beispiele

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

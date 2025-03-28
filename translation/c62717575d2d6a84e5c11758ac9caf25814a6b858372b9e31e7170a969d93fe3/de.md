```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Funktion
```

Gibt eine anonyme Funktion zurück, die die Funktion `f` aufruft. Wenn eine Ausnahme auftritt, wird `f` wiederholt aufgerufen, jedes Mal, wenn `check` `true` zurückgibt, nachdem die Anzahl der Sekunden gewartet wurde, die in `delays` angegeben sind. `check` sollte den aktuellen Zustand von `delays` und die `Exception` eingeben.

!!! compat "Julia 1.2"
    Vor Julia 1.2 war diese Signatur auf `f::Function` beschränkt.


# Beispiele

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```

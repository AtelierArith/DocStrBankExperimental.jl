```
uuid4([rng::AbstractRNG]) -> UUID
```

Generiert einen Version 4 (zufälligen oder pseudo-zufälligen) universell eindeutigen Bezeichner (UUID), wie in RFC 4122 angegeben.

Der standardmäßige rng, der von `uuid4` verwendet wird, ist nicht `Random.default_rng()` und jede Aufruf von `uuid4()` ohne Argument sollte erwartet werden, einen eindeutigen Bezeichner zurückzugeben. Wichtig ist, dass die Ausgaben von `uuid4` sich nicht wiederholen, selbst wenn `Random.seed!(seed)` aufgerufen wird. Derzeit (Stand Julia 1.6) verwendet `uuid4` `Random.RandomDevice` als den standardmäßigen rng. Dies ist jedoch ein Implementierungsdetail, das sich in Zukunft ändern kann.

!!! compat "Julia 1.6"
    Die Ausgabe von `uuid4` hängt nicht von `Random.default_rng()` ab, seit Julia 1.6.


# Beispiele

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```

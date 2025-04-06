```
uuid1([rng::AbstractRNG]) -> UUID
```

Generiert einen Version 1 (zeitbasierten) universell eindeutigen Bezeichner (UUID), wie in RFC 4122 spezifiziert. Beachten Sie, dass die Node-ID zufällig generiert wird (identifiziert nicht den Host) gemäß Abschnitt 4.5 des RFC.

Der standardmäßige rng, der von `uuid1` verwendet wird, ist nicht `Random.default_rng()` und jede Aufruf von `uuid1()` ohne Argument sollte als Rückgabe eines eindeutigen Bezeichners erwartet werden. Wichtig ist, dass die Ausgaben von `uuid1` sich nicht wiederholen, selbst wenn `Random.seed!(seed)` aufgerufen wird. Derzeit (Stand Julia 1.6) verwendet `uuid1` `Random.RandomDevice` als den standardmäßigen rng. Dies ist jedoch ein Implementierungsdetail, das sich in Zukunft ändern kann.

!!! compat "Julia 1.6"
    Die Ausgabe von `uuid1` hängt nicht von `Random.default_rng()` ab, Stand Julia 1.6.


# Beispiele

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```

```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

Suchen Sie nach dem angegebenen Muster `pat` in `s` und ersetzen Sie jede Vorkommen durch `r`. Wenn `count` angegeben ist, ersetzen Sie höchstens `count` Vorkommen. `pat` kann ein einzelnes Zeichen, ein Vektor oder eine Menge von Zeichen, eine Zeichenkette oder ein regulärer Ausdruck sein. Wenn `r` eine Funktion ist, wird jedes Vorkommen durch `r(s)` ersetzt, wobei `s` der übereinstimmende Teilstring ist (wenn `pat` ein `AbstractPattern` oder `AbstractString` ist) oder Zeichen (wenn `pat` ein `AbstractChar` oder eine Sammlung von `AbstractChar` ist). Wenn `pat` ein regulärer Ausdruck ist und `r` eine [`SubstitutionString`](@ref) ist, werden die Erfassungsgruppenreferenzen in `r` durch den entsprechenden übereinstimmenden Text ersetzt. Um Instanzen von `pat` aus `string` zu entfernen, setzen Sie `r` auf die leere `String` (`""`).

Der Rückgabewert ist ein neuer String nach den Ersetzungen. Wenn das Argument `io::IO` bereitgestellt wird, wird der transformierte String stattdessen in `io` geschrieben (Rückgabe von `io`). (Zum Beispiel kann dies in Verbindung mit einem [`IOBuffer`](@ref) verwendet werden, um ein vorab zugewiesenes Pufferarray vor Ort wiederzuverwenden.)

Mehrere Muster können angegeben werden, und sie werden gleichzeitig von links nach rechts angewendet, sodass nur ein Muster auf ein beliebiges Zeichen angewendet wird, und die Muster werden nur auf den Eingabetext und nicht auf die Ersetzungen angewendet.

!!! compat "Julia 1.7"
    Die Unterstützung für mehrere Muster erfordert Version 1.7.


!!! compat "Julia 1.10"
    Das Argument `io::IO` erfordert Version 1.10.


# Beispiele

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```

```
@assert cond [text]
```

Wirft einen [`AssertionError`](@ref), wenn `cond` `false` ist. Dies ist die bevorzugte Syntax zum Schreiben von Assertions, die Bedingungen sind, von denen angenommen wird, dass sie wahr sind, die der Benutzer jedoch trotzdem überprüfen könnte, um beim Debuggen zu helfen, falls sie fehlschlagen. Die optionale Nachricht `text` wird bei einem Assertion-Fehler angezeigt.

!!! warning
    Eine Assertion könnte auf einigen Optimierungsstufen deaktiviert sein. Assertions sollten daher nur als Debugging-Tool verwendet werden und nicht zur Überprüfung von Authentifizierungen (z. B. zur Überprüfung von Passwörtern oder zur Überprüfung von Array-Grenzen). Der Code darf nicht von den Nebenwirkungen des Ausführens von `cond` für das korrekte Verhalten einer Funktion abhängen.


# Beispiele

```jldoctest
julia> @assert iseven(3) "3 ist eine ungerade Zahl!"
ERROR: AssertionError: 3 ist eine ungerade Zahl!

julia> @assert isodd(3) "Was sind gerade Zahlen?"
```

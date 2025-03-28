```
while
```

`while`-Schleifen bewerten wiederholt einen bedingten Ausdruck und setzen die Bewertung des Körpers der while-Schleife fort, solange der Ausdruck wahr bleibt. Wenn der Bedingungsausdruck falsch ist, wenn die while-Schleife zum ersten Mal erreicht wird, wird der Körper niemals bewertet.

# Beispiele

```jldoctest
julia> i = 1
1

julia> while i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```

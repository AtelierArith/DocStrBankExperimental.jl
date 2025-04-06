```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

Generiere `N` geschachtelte Schleifen, wobei `itersym` als Präfix für die Iterationsvariablen verwendet wird. `rangeexpr` kann ein Ausdruck einer anonymen Funktion oder ein einfaches Symbol `var` sein, in welchem Fall der Bereich `axes(var, d)` für die Dimension `d` ist.

Optional kannst du "pre" und "post" Ausdrücke angeben. Diese werden jeweils zuerst und zuletzt im Körper jeder Schleife ausgeführt. Zum Beispiel:

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

würde generieren:

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

Wenn du nur einen Post-Ausdruck möchtest, gib [`nothing`](@ref) für den Pre-Ausdruck an. Mit Klammern und Semikolons kannst du mehrteilige Ausdrücke angeben.

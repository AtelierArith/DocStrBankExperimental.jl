```
as
```

`as` wird als Schlüsselwort verwendet, um einen Bezeichner, der durch `import` oder `using` in den Geltungsbereich gebracht wird, umzubenennen, um Namenskonflikte zu umgehen und um Namen zu verkürzen. (Außerhalb von `import`- oder `using`-Anweisungen ist `as` kein Schlüsselwort und kann als gewöhnlicher Bezeichner verwendet werden.)

`import LinearAlgebra as LA` bringt die importierte Standardbibliothek `LinearAlgebra` in den Geltungsbereich als `LA`.

`import LinearAlgebra: eigen as eig, cholesky as chol` bringt die Methoden `eigen` und `cholesky` aus `LinearAlgebra` in den Geltungsbereich als `eig` und `chol` respektive.

`as` funktioniert mit `using` nur, wenn einzelne Bezeichner in den Geltungsbereich gebracht werden. Zum Beispiel funktioniert `using LinearAlgebra: eigen as eig` oder `using LinearAlgebra: eigen as eig, cholesky as chol`, aber `using LinearAlgebra as LA` ist ungültige Syntax, da es unsinnig ist, *alle* exportierten Namen von `LinearAlgebra` in `LA` umzubenennen.

```
let
```

`let`-Blöcke erstellen einen neuen harten Geltungsbereich und führen optional neue lokale Bindungen ein.

Genau wie die [anderen Geltungsbereichs-Konstrukte](@ref man-scope-table) definieren `let`-Blöcke den Codeblock, in dem neu eingeführte lokale Variablen zugänglich sind. Darüber hinaus hat die Syntax eine besondere Bedeutung für durch Kommas getrennte Zuweisungen und Variablennamen, die optional in derselben Zeile wie das `let` erscheinen können:

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

Die auf dieser Zeile eingeführten Variablen sind lokal für den `let`-Block und die Zuweisungen werden der Reihe nach ausgewertet, wobei jede rechte Seite im Geltungsbereich ausgewertet wird, ohne den Namen auf der linken Seite zu berücksichtigen. Daher macht es Sinn, etwas wie `let x = x` zu schreiben, da die beiden `x`-Variablen unterschiedlich sind, wobei die linke Seite das `x` aus dem äußeren Geltungsbereich lokal überschattet. Dies kann sogar ein nützliches Idiom sein, da bei jedem Betreten lokaler Geltungsbereiche neue lokale Variablen frisch erstellt werden, aber dies ist nur im Fall von Variablen beobachtbar, die ihren Geltungsbereich durch Closures überdauern. Eine `let`-Variable ohne Zuweisung, wie `var2` im obigen Beispiel, deklariert eine neue lokale Variable, die noch nicht an einen Wert gebunden ist.

Im Gegensatz dazu gruppieren [`begin`](@ref)-Blöcke ebenfalls mehrere Ausdrücke, führen jedoch keinen Geltungsbereich ein und haben nicht die spezielle Zuweisungssyntax.

### Beispiele

In der folgenden Funktion gibt es ein einzelnes `x`, das dreimal iterativ durch die `map` aktualisiert wird. Die zurückgegebenen Closures beziehen sich alle auf dieses eine `x` mit seinem endgültigen Wert:

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generische Funktion mit 1 Methode)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

Wenn wir jedoch einen `let`-Block hinzufügen, der eine *neue* lokale Variable einführt, werden wir am Ende mit drei unterschiedlichen Variablen konfrontiert, die erfasst werden (eine bei jeder Iteration), obwohl wir uns entschieden haben, denselben Namen zu verwenden (zu überschatten).

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generische Funktion mit 1 Methode)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

Alle Geltungsbereichs-Konstrukte, die neue lokale Variablen einführen, verhalten sich auf diese Weise, wenn sie wiederholt ausgeführt werden; das charakteristische Merkmal von `let` ist seine Fähigkeit, prägnant neue `local`s zu deklarieren, die äußere Variablen desselben Namens überschatten können. Zum Beispiel erfasst die direkte Verwendung des Arguments der `do`-Funktion ebenfalls drei unterschiedliche Variablen:

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generische Funktion mit 1 Methode)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```

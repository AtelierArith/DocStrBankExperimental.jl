```
;
```

`;` hat eine ähnliche Rolle in Julia wie in vielen C-ähnlichen Sprachen und wird verwendet, um das Ende der vorherigen Anweisung zu kennzeichnen.

`;` ist am Ende einer Zeile nicht notwendig, kann jedoch verwendet werden, um Anweisungen in einer einzigen Zeile zu trennen oder Anweisungen zu einem einzigen Ausdruck zu verbinden.

Das Hinzufügen von `;` am Ende einer Zeile im REPL unterdrückt die Ausgabe des Ergebnisses dieses Ausdrucks.

In Funktionsdeklarationen und optional in Aufrufen trennt `;` reguläre Argumente von Schlüsselwörtern.

In Array-Literalen werden durch Semikolons getrennte Argumente zusammengefügt. Ein Separator aus einem einzelnen `;` fügt vertikal zusammen (d.h. entlang der ersten Dimension), `;;` fügt horizontal zusammen (zweite Dimension), `;;;` fügt entlang der dritten Dimension zusammen usw. Ein solcher Separator kann auch in letzter Position in den eckigen Klammern verwendet werden, um nachfolgende Dimensionen der Länge 1 hinzuzufügen.

Ein `;` an erster Stelle innerhalb von Klammern kann verwendet werden, um ein benanntes Tupel zu erstellen. Die gleiche `(; ...)`-Syntax auf der linken Seite einer Zuweisung ermöglicht die Destrukturierung von Eigenschaften.

Im standardmäßigen REPL wechselt das Tippen von `;` in einer leeren Zeile in den Shell-Modus.

# Beispiele

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # ohne das ; oder ein nachfolgendes Komma würde dies x zuweisen
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # setze die Variablen b und x mit Hilfe der Destrukturierung von Eigenschaften

julia> b, x
(2, 1)

julia> ; # beim Tippen von ; ändert sich die Eingabeaufforderung (an Ort und Stelle) zu: shell>
shell> echo hello
hello
```

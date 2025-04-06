# [Scope of Variables](@id scope-of-variables)

Der *Geltungsbereich* einer Variablen ist der Codebereich, innerhalb dessen eine Variable zugänglich ist. Die Geltungsbereichsregelung hilft, Namenskonflikte von Variablen zu vermeiden. Das Konzept ist intuitiv: Zwei Funktionen können beide Argumente mit dem Namen `x` haben, ohne dass sich die beiden `x` auf dasselbe beziehen. Ähnlich gibt es viele andere Fälle, in denen verschiedene Codeblöcke denselben Namen verwenden können, ohne sich auf dasselbe zu beziehen. Die Regeln dafür, wann derselbe Variablenname sich auf dasselbe oder nicht bezieht, werden als Geltungsbereichsregeln bezeichnet; dieser Abschnitt erläutert sie im Detail.

Bestimmte Konstrukte in der Sprache führen *Scope-Blöcke* ein, die Codebereiche sind, die für eine bestimmte Menge von Variablen als Gültigkeitsbereich in Frage kommen. Der Gültigkeitsbereich einer Variablen kann kein beliebiger Satz von Quellzeilen sein; stattdessen wird er immer mit einem dieser Blöcke übereinstimmen. Es gibt zwei Haupttypen von Gültigkeitsbereichen in Julia, *globalen Gültigkeitsbereich* und *lokalen Gültigkeitsbereich*. Letzterer kann geschachtelt werden. Es gibt auch eine Unterscheidung in Julia zwischen Konstrukten, die einen "harten Gültigkeitsbereich" einführen, und solchen, die nur einen "weichen Gültigkeitsbereich" einführen, was beeinflusst, ob [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing) eine globale Variable mit demselben Namen erlaubt ist oder nicht.

### [Scope constructs](@id man-scope-table)

Die Konstrukte, die Scope-Blöcke einführen, sind:

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

Bemerkenswert ist, dass in dieser Tabelle [begin blocks](@ref man-compound-expressions) und [if blocks](@ref man-conditional-evaluation) fehlen, die *keine* neuen Bereiche einführen. Die drei Arten von Bereichen folgen etwas unterschiedlichen Regeln, die im Folgenden erläutert werden.

Julia verwendet [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope), was bedeutet, dass der Geltungsbereich einer Funktion nicht vom Geltungsbereich ihres Aufrufers erbt, sondern von dem Geltungsbereich, in dem die Funktion definiert wurde. Zum Beispiel bezieht sich in dem folgenden Code das `x` innerhalb von `foo` auf das `x` im globalen Geltungsbereich seines Moduls `Bar`:

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

und kein `x` im Geltungsbereich, in dem `foo` verwendet wird:

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

Somit bedeutet *lexikalischer Geltungsbereich*, dass man ableiten kann, auf was eine Variable in einem bestimmten Codeabschnitt verweist, nur aus dem Code, in dem sie erscheint, und dass dies nicht davon abhängt, wie das Programm ausgeführt wird. Ein Geltungsbereich, der in einem anderen Geltungsbereich geschachtelt ist, kann Variablen in allen äußeren Geltungsbereichen, in denen er enthalten ist, "sehen". Äußere Geltungsbereiche hingegen können Variablen in inneren Geltungsbereichen nicht sehen.

## Global Scope

Jedes Modul führt einen neuen globalen Geltungsbereich ein, der von dem globalen Geltungsbereich aller anderen Module getrennt ist – es gibt keinen umfassenden globalen Geltungsbereich. Module können Variablen anderer Module in ihren Geltungsbereich einführen durch die [using or import](@ref modules)-Anweisungen oder durch qualifizierten Zugriff mit der Punktnotation, d.h. jedes Modul ist eine sogenannte *Namensraum* sowie eine erstklassige Datenstruktur, die Namen mit Werten verknüpft.

Wenn ein Ausdruck auf oberster Ebene eine Variablendeklaration mit dem Schlüsselwort `local` enthält, ist diese Variable außerhalb dieses Ausdrucks nicht zugänglich. Die Variable innerhalb des Ausdrucks beeinflusst keine globalen Variablen mit demselben Namen. Ein Beispiel ist die Deklaration von `local x` in einem `begin`- oder `if`-Block auf oberster Ebene:

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

Beachten Sie, dass die interaktive Eingabeaufforderung (auch bekannt als REPL) im globalen Geltungsbereich des Moduls `Main` ist.

## [Local Scope](@id local-scope)

Ein neuer lokaler Geltungsbereich wird durch die meisten Codeblöcke eingeführt (siehe oben [table](@ref man-scope-table) für eine vollständige Liste). Wenn ein solcher Block syntaktisch innerhalb eines anderen lokalen Geltungsbereichs geschachtelt ist, ist der Geltungsbereich, den er erstellt, innerhalb aller lokalen Geltungsbereiche geschachtelt, in denen er erscheint, die letztendlich alle innerhalb des globalen Geltungsbereichs des Moduls geschachtelt sind, in dem der Code ausgewertet wird. Variablen in äußeren Geltungsbereichen sind aus jedem Geltungsbereich sichtbar, den sie enthalten – was bedeutet, dass sie in inneren Geltungsbereichen gelesen und geschrieben werden können – es sei denn, es gibt eine lokale Variable mit demselben Namen, die die äußere Variable mit demselben Namen "verdeckt". Dies gilt sogar, wenn der äußere lokale Geltungsbereich nach (im Sinne von textuell darunter) einem inneren Block deklariert wird. Wenn wir sagen, dass eine Variable in einem bestimmten Geltungsbereich "existiert", bedeutet dies, dass eine Variable mit diesem Namen in einem der Geltungsbereiche existiert, in denen der aktuelle Geltungsbereich geschachtelt ist, einschließlich des aktuellen.

Einige Programmiersprachen erfordern die explizite Deklaration neuer Variablen, bevor sie verwendet werden. Die explizite Deklaration funktioniert auch in Julia: In jedem lokalen Geltungsbereich erklärt das Schreiben von `local x` eine neue lokale Variable in diesem Geltungsbereich, unabhängig davon, ob bereits eine Variable mit dem Namen `x` in einem äußeren Geltungsbereich existiert oder nicht. Das Deklarieren jeder neuen Variable auf diese Weise ist jedoch etwas umständlich und mühsam, daher betrachtet Julia, wie viele andere Sprachen, die Zuweisung zu einem Variablennamen, der noch nicht existiert, als implizite Deklaration dieser Variablen. Wenn der aktuelle Geltungsbereich global ist, ist die neue Variable global; wenn der aktuelle Geltungsbereich lokal ist, ist die neue Variable lokal für den innersten lokalen Geltungsbereich und wird innerhalb dieses Geltungsbereichs sichtbar sein, jedoch nicht außerhalb davon. Wenn Sie einer bestehenden lokalen Variable einen Wert zuweisen, wird *immer* diese bestehende lokale Variable aktualisiert: Sie können eine lokale Variable nur durch die explizite Deklaration einer neuen lokalen Variable in einem geschachtelten Geltungsbereich mit dem Schlüsselwort `local` überschreiben. Dies gilt insbesondere für Variablen, die in inneren Funktionen zugewiesen werden, was Benutzer, die aus Python kommen, überraschen kann, da die Zuweisung in einer inneren Funktion eine neue lokale Variable erstellt, es sei denn, die Variable wird ausdrücklich als nicht lokal deklariert.

In der Regel ist dies ziemlich intuitiv, aber wie bei vielen Dingen, die intuitiv erscheinen, sind die Details subtiler, als man naiv annehmen könnte.

Wenn `x = <Wert>` in einem lokalen Geltungsbereich auftritt, wendet Julia die folgenden Regeln an, um zu entscheiden, was der Ausdruck bedeutet, basierend darauf, wo der Zuweisungsausdruck auftritt und worauf `x` an diesem Ort bereits verweist:

1. **Vorhandene lokale:** Wenn `x` *bereits eine lokale Variable* ist, wird die vorhandene lokale `x` zugewiesen;
2. **Harter Bereich:** Wenn `x` *nicht bereits eine lokale Variable* ist und eine Zuweisung innerhalb eines beliebigen harten Bereichs-Konstrukts (d.h. innerhalb eines `let`-Blocks, Funktions- oder Makrokörpers, einer Komprehension oder eines Generators) erfolgt, wird eine neue lokale Variable namens `x` im Gültigkeitsbereich der Zuweisung erstellt;
3. **Weicher Geltungsbereich:** Wenn `x` *nicht bereits eine lokale Variable* ist und alle Geltungsbereichskonstrukte, die die Zuweisung enthalten, weiche Geltungsbereiche sind (Schleifen, `try`/`catch`-Blöcke oder `struct`-Blöcke), hängt das Verhalten davon ab, ob die globale Variable `x` definiert ist:

      * wenn global `x` *undefiniert* ist, wird ein neuer lokaler Name `x` im Geltungsbereich der Zuweisung erstellt;
      * wenn global `x` *definiert* ist, wird die Zuweisung als mehrdeutig betrachtet:

          * in *nicht-interaktiven* Kontexten (Dateien, eval) wird eine Warnung über Mehrdeutigkeit ausgegeben und ein neuer lokaler Bereich wird erstellt;
          * in *interaktiven* Kontexten (REPL, Notebooks) wird die globale Variable `x` zugewiesen.

Sie können feststellen, dass sich in nicht-interaktiven Kontexten das Verhalten von hartem und weichem Geltungsbereich identisch verhält, mit der Ausnahme, dass eine Warnung ausgegeben wird, wenn eine implizit lokale Variable (d.h. nicht mit `local x` deklariert) eine globale Variable überschattet. In interaktiven Kontexten folgen die Regeln einer komplexeren Heuristik aus Gründen der Bequemlichkeit. Dies wird ausführlich in den folgenden Beispielen behandelt.

Jetzt, da Sie die Regeln kennen, lassen Sie uns einige Beispiele ansehen. Jedes Beispiel wird angenommen, dass es in einer neuen REPL-Sitzung bewertet wird, sodass die einzigen globalen Variablen in jedem Snippet die sind, die in diesem Codeblock zugewiesen werden.

Wir beginnen mit einer klaren und eindeutigen Situation – einer Zuweisung innerhalb eines festen Geltungsbereichs, in diesem Fall einem Funktionskörper, wenn keine lokale Variable mit diesem Namen bereits existiert:

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

Innerhalb der `greet`-Funktion bewirkt die Zuweisung `x = "hello"`, dass `x` eine neue lokale Variable im Gültigkeitsbereich der Funktion wird. Es gibt zwei relevante Fakten: Die Zuweisung erfolgt im lokalen Gültigkeitsbereich und es gibt keine vorhandene lokale `x`-Variable. Da `x` lokal ist, spielt es keine Rolle, ob es eine globale Variable namens `x` gibt oder nicht. Hier definieren wir zum Beispiel `x = 123`, bevor wir `greet` definieren und aufrufen:

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

Da das `x` in `greet` lokal ist, wird der Wert (oder das Fehlen davon) des globalen `x` durch den Aufruf von `greet` nicht beeinflusst. Die strikte Geltungsregel interessiert sich nicht dafür, ob ein globales `x` existiert oder nicht: Die Zuweisung zu `x` in einem strengen Geltungsbereich ist lokal (es sei denn, `x` wird als global deklariert).

Die nächste klare Situation, die wir betrachten werden, ist, wenn bereits eine lokale Variable namens `x` existiert, in welchem Fall `x = <value>` immer dieser bestehenden lokalen `x` zuweist. Dies gilt unabhängig davon, ob die Zuweisung im selben lokalen Geltungsbereich, in einem inneren lokalen Geltungsbereich im selben Funktionskörper oder im Körper einer Funktion erfolgt, die in einer anderen Funktion geschachtelt ist, auch bekannt als [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)).

Wir werden die Funktion `sum_to` verwenden, die die Summe der Ganzzahlen von eins bis `n` berechnet, als Beispiel:

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

Wie im vorherigen Beispiel führt die erste Zuweisung an `s` oben in `sum_to` dazu, dass `s` eine neue lokale Variable im Funktionskörper wird. Die `for`-Schleife hat ihren eigenen inneren lokalen Geltungsbereich innerhalb des Funktionsgeltungsbereichs. An dem Punkt, an dem `s = s + i` auftritt, ist `s` bereits eine lokale Variable, sodass die Zuweisung die vorhandene `s` aktualisiert, anstatt eine neue lokale zu erstellen. Wir können dies testen, indem wir `sum_to` im REPL aufrufen:

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

Da `s` lokal für die Funktion `sum_to` ist, hat der Aufruf der Funktion keinen Einfluss auf die globale Variable `s`. Wir können auch sehen, dass die Aktualisierung `s = s + i` in der `for`-Schleife dasselbe `s` aktualisiert haben muss, das durch die Initialisierung `s = 0` erstellt wurde, da wir die korrekte Summe von 55 für die Ganzzahlen von 1 bis 10 erhalten.

Lass uns für einen Moment in die Tatsache eintauchen, dass der Körper der `for`-Schleife seinen eigenen Gültigkeitsbereich hat, indem wir eine etwas ausführlichere Variante schreiben, die wir `sum_to_def` nennen, in der wir die Summe `s + i` in einer Variablen `t` speichern, bevor wir `s` aktualisieren:

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

Diese Version gibt `s` wie zuvor zurück, verwendet jedoch auch das `@isdefined`-Makro, um einen booleschen Wert zurückzugeben, der angibt, ob eine lokale Variable namens `t` im äußersten lokalen Gültigkeitsbereich der Funktion definiert ist. Wie Sie sehen können, ist außerhalb des Körpers der `for`-Schleife kein `t` definiert. Dies liegt erneut an der Regel des harten Gültigkeitsbereichs: Da die Zuweisung an `t` innerhalb einer Funktion erfolgt, die einen harten Gültigkeitsbereich einführt, wird `t` zu einer neuen lokalen Variable im lokalen Gültigkeitsbereich, in dem sie erscheint, d.h. innerhalb des Körpers der Schleife. Selbst wenn es ein globales `t` gäbe, würde das keinen Unterschied machen – die Regel des harten Gültigkeitsbereichs wird durch nichts im globalen Gültigkeitsbereich beeinflusst.

Beachten Sie, dass der lokale Geltungsbereich eines Schleifenrumpfes nicht anders ist als der lokale Geltungsbereich einer inneren Funktion. Das bedeutet, dass wir dieses Beispiel so umschreiben könnten, dass der Schleifenrumpf als Aufruf einer inneren Hilfsfunktion implementiert wird und sich gleich verhält:

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

Dieses Beispiel veranschaulicht einige wichtige Punkte:

1. Innere Funktionsbereiche sind wie jeder andere geschachtelte lokale Bereich. Insbesondere, wenn eine Variable bereits außerhalb einer inneren Funktion lokal ist und Sie ihr innerhalb der inneren Funktion einen Wert zuweisen, wird die äußere lokale Variable aktualisiert.
2. Es spielt keine Rolle, ob die Definition eines äußeren lokalen Bereichs unterhalb der Stelle erfolgt, an der er aktualisiert wird, die Regel bleibt dieselbe. Der gesamte umschließende lokale Geltungsbereich wird analysiert und seine lokalen Variablen bestimmt, bevor die inneren lokalen Bedeutungen aufgelöst werden.

Dieses Design bedeutet, dass Sie im Allgemeinen Code in eine innere Funktion hinein oder heraus verschieben können, ohne seine Bedeutung zu ändern, was eine Reihe von gängigen Idiomen in der Sprache unter Verwendung von Closures erleichtert (siehe [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)).

Lass uns zu einigen mehrdeutigen Fällen über die Regel des weichen Geltungsbereichs übergehen. Wir werden dies tun, indem wir die Körper der Funktionen `greet` und `sum_to_def` in weiche Geltungsbereichskontexte extrahieren. Zuerst setzen wir den Körper von `greet` in eine `for`-Schleife – die weich ist, anstatt hart – und bewerten sie im REPL:

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

Da die globale `x` nicht definiert ist, wenn die `for`-Schleife ausgewertet wird, gilt die erste Klausel der Soft-Scope-Regel und `x` wird als lokal zur `for`-Schleife erstellt, sodass die globale `x` nach der Ausführung der Schleife undefiniert bleibt. Als Nächstes betrachten wir den Körper von `sum_to_def`, der in den globalen Geltungsbereich extrahiert wird, wobei sein Argument auf `n = 10` festgelegt ist.

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

Was macht dieser Code? Hinweis: Es ist eine Fangfrage. Die Antwort lautet "es kommt darauf an." Wenn dieser Code interaktiv eingegeben wird, verhält er sich genauso wie in einem Funktionskörper. Wenn der Code jedoch in einer Datei erscheint, gibt er eine Mehrdeutigkeitswarnung aus und wirft einen Fehler wegen einer undefinierten Variablen. Lassen Sie uns zuerst sehen, wie es im REPL funktioniert:

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

Der REPL ahmt das Verweilen im Körper einer Funktion nach, indem entschieden wird, ob eine Zuweisung innerhalb der Schleife eine globale Variable aktualisiert oder eine neue lokale Variable erstellt, basierend darauf, ob eine globale Variable mit diesem Namen definiert ist oder nicht. Wenn eine globale Variable mit diesem Namen existiert, wird sie durch die Zuweisung aktualisiert. Wenn keine globale Variable existiert, wird eine neue lokale Variable erstellt. In diesem Beispiel sehen wir beide Fälle in Aktion:

  * Es gibt kein globales `t`, daher erstellt `t = s + i` ein neues `t`, das lokal zur `for`-Schleife ist;
  * Es gibt eine globale Variable namens `s`, also weist `s = t` ihr einen Wert zu.

Die zweite Tatsache ist, warum die Ausführung der Schleife den globalen Wert von `s` ändert, und die erste Tatsache ist, warum `t` nach der Ausführung der Schleife immer noch undefiniert ist. Lassen Sie uns nun versuchen, denselben Code zu bewerten, als ob er sich in einer Datei befände:

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

Hier verwenden wir [`include_string`](@ref), um `code` so auszuwerten, als ob es der Inhalt einer Datei wäre. Wir könnten `code` auch in eine Datei speichern und dann `include` auf dieser Datei aufrufen – das Ergebnis wäre dasselbe. Wie Sie sehen können, verhält sich dies ganz anders, als den gleichen Code im REPL auszuwerten. Lassen Sie uns aufschlüsseln, was hier passiert:

  * global `s` ist vor der Auswertung der Schleife mit dem Wert `0` definiert.
  * die Zuweisung `s = t` erfolgt in einem weichen Geltungsbereich—einer `for`-Schleife außerhalb eines Funktionskörpers oder eines anderen harten Geltungsbereichs.
  * daher gilt die zweite Klausel der Soft-Scope-Regel, und die Zuweisung ist mehrdeutig, sodass eine Warnung ausgegeben wird.
  * Die Ausführung wird fortgesetzt, wodurch `s` lokal zum Körper der `for`-Schleife wird.
  * da `s` lokal für die `for`-Schleife ist, ist es undefiniert, wenn `t = s + i` ausgewertet wird, was einen Fehler verursacht.
  * Die Auswertung stoppt dort, aber wenn es zu `s` und `@isdefined(t)` käme, würde es `0` und `false` zurückgeben.

Dies demonstriert einige wichtige Aspekte des Geltungsbereichs: In einem Geltungsbereich kann jede Variable nur eine Bedeutung haben, und diese Bedeutung wird unabhängig von der Reihenfolge der Ausdrücke bestimmt. Die Präsenz des Ausdrucks `s = t` in der Schleife bewirkt, dass `s` lokal zur Schleife ist, was bedeutet, dass es auch lokal ist, wenn es auf der rechten Seite von `t = s + i` erscheint, obwohl dieser Ausdruck zuerst erscheint und zuerst ausgewertet wird. Man könnte sich vorstellen, dass das `s` in der ersten Zeile der Schleife global sein könnte, während das `s` in der zweiten Zeile der Schleife lokal ist, aber das ist nicht möglich, da sich die beiden Zeilen im selben Geltungsbereich befinden und jede Variable in einem bestimmten Geltungsbereich nur eine Bedeutung haben kann.

#### [On Soft Scope](@id on-soft-scope)

Wir haben nun alle Regeln des lokalen Geltungsbereichs behandelt, aber bevor wir diesen Abschnitt abschließen, sollten vielleicht ein paar Worte darüber gesagt werden, warum der mehrdeutige weiche Geltungsbereich in interaktiven und nicht-interaktiven Kontexten unterschiedlich behandelt wird. Es gibt zwei offensichtliche Fragen, die man stellen könnte:

1. Warum funktioniert es nicht einfach überall wie die REPL?
2. Warum funktioniert es nicht einfach wie in Dateien überall? Und vielleicht die Warnung überspringen?

In Julia ≤ 0.6 verhielten sich alle globalen Scopes wie das aktuelle REPL: Wenn `x = <Wert>` in einer Schleife (oder `try`/`catch`, oder `struct`-Körper) aber außerhalb eines Funktionskörpers (oder `let`-Blocks oder einer Komprehension) auftrat, wurde entschieden, ob `x` lokal zur Schleife sein sollte, basierend darauf, ob ein global benannter `x` definiert war oder nicht. Dieses Verhalten hat den Vorteil, intuitiv und praktisch zu sein, da es das Verhalten innerhalb eines Funktionskörpers so genau wie möglich nachahmt. Insbesondere erleichtert es das Hin- und Herbewegen von Code zwischen einem Funktionskörper und dem REPL, wenn man versucht, das Verhalten einer Funktion zu debuggen. Es hat jedoch einige Nachteile. Erstens ist es ein ziemlich komplexes Verhalten: Viele Menschen waren im Laufe der Jahre über dieses Verhalten verwirrt und beschwerten sich, dass es kompliziert und schwer zu erklären und zu verstehen sei. Fairer Punkt. Zweitens, und arguably schlimmer, ist, dass es schlecht für das Programmieren "in großem Maßstab" ist. Wenn man ein kleines Stück Code an einem Ort wie diesem sieht, ist es ziemlich klar, was vor sich geht:

```julia
s = 0
for i = 1:10
    s += i
end
```

Offensichtlich ist die Absicht, die vorhandene globale Variable `s` zu ändern. Was könnte es sonst bedeuten? Allerdings ist nicht jeder reale Code so kurz oder so klar. Wir haben festgestellt, dass Code wie der folgende oft in der Wildnis vorkommt:

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

Es ist viel weniger klar, was hier passieren sollte. Da `x + "hello"` einen Methodenfehler verursacht, scheint es wahrscheinlich, dass die Absicht darin besteht, dass `x` lokal zur `for`-Schleife ist. Aber Laufzeitwerte und welche Methoden existieren, können nicht verwendet werden, um die Gültigkeitsbereiche von Variablen zu bestimmen. Mit dem Verhalten von Julia ≤ 0.6 ist es besonders besorgniserregend, dass jemand die `for`-Schleife zuerst geschrieben hat, sie einwandfrei funktionierte, aber später, als jemand anders eine neue globale Variable weit entfernt hinzufügt – möglicherweise in einer anderen Datei – sich der Code plötzlich anders verhält und entweder lautstark fehlschlägt oder, noch schlimmer, stillschweigend das Falsche tut. Diese Art von ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming)) ist etwas, das gute Programmiersprachen-Designs verhindern sollten.

So in Julia 1.0 haben wir die Regeln für den Geltungsbereich vereinfacht: In jedem lokalen Geltungsbereich erzeugte die Zuweisung an einen Namen, der noch keine lokale Variable war, eine neue lokale Variable. Dies beseitigte das Konzept des weichen Geltungsbereichs vollständig und entfernte das Potenzial für spooky action. Wir entdeckten und beheben eine erhebliche Anzahl von Fehlern aufgrund der Beseitigung des weichen Geltungsbereichs, was die Entscheidung, ihn loszuwerden, bestätigte. Und es gab viel Freude! Nun, nicht wirklich. Denn einige Leute waren verärgert, dass sie jetzt schreiben mussten:

```julia
s = 0
for i = 1:10
    global s += i
end
```

Siehst du die `global`-Annotation dort? Hässlich. Offensichtlich konnte diese Situation nicht toleriert werden. Aber im Ernst, es gibt zwei Hauptprobleme mit der Anforderung von `global` für diese Art von Code auf oberster Ebene:

1. Es ist nicht mehr praktisch, den Code aus dem Funktionskörper in die REPL zu kopieren und einzufügen, um ihn zu debuggen – man muss `global`-Annotationen hinzufügen und sie dann wieder entfernen, um zurückzukehren;
2. Anfänger werden diesen Code ohne das `global` schreiben und haben keine Ahnung, warum ihr Code nicht funktioniert – der Fehler, den sie erhalten, ist, dass `s` undefiniert ist, was niemanden erleuchtet, der diesen Fehler macht.

Ab Julia 1.5 funktioniert dieser Code ohne die `global`-Annotation in interaktiven Kontexten wie dem REPL oder Jupyter-Notebooks (genauso wie Julia 0.6) und in Dateien sowie anderen nicht-interaktiven Kontexten wird diese sehr direkte Warnung ausgegeben:

> Die Zuweisung an `s` im weichen Geltungsbereich ist mehrdeutig, da eine globale Variable mit demselben Namen existiert: `s` wird als neue lokale Variable behandelt. Klären Sie dies, indem Sie `local s` verwenden, um diese Warnung zu unterdrücken, oder `global s`, um der bestehenden globalen Variable zuzuweisen.


Dies adressiert beide Probleme und bewahrt gleichzeitig die Vorteile des "Programmieren in großem Maßstab" des Verhaltens von 1.0: Globale Variablen haben keinen unheimlichen Einfluss auf die Bedeutung von Code, der weit entfernt sein kann; im REPL funktioniert das Kopieren und Einfügen beim Debuggen und Anfänger haben keine Probleme; jedes Mal, wenn jemand entweder eine `global`-Annotation vergisst oder versehentlich eine vorhandene globale Variable mit einer lokalen in einem weichen Geltungsbereich überschattet, was ohnehin verwirrend wäre, erhält er eine klare Warnung.

Eine wichtige Eigenschaft dieses Designs ist, dass jeder Code, der in einer Datei ohne Warnung ausgeführt wird, sich in einem frischen REPL gleich verhält. Und umgekehrt, wenn Sie eine REPL-Sitzung nehmen und sie in eine Datei speichern, und sie sich anders verhält als im REPL, dann erhalten Sie eine Warnung.

### Let Blocks

`let`-Anweisungen erstellen einen neuen *harten Geltungsbereich* (siehe oben) und führen jedes Mal, wenn sie ausgeführt werden, neue Variablenbindungen ein. Die Variable muss nicht sofort zugewiesen werden:

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

Während Zuweisungen einen neuen Wert an einem bestehenden Wertstandort zuweisen können, erstellt `let` immer einen neuen Standort. Dieser Unterschied ist normalerweise nicht wichtig und ist nur im Fall von Variablen erkennbar, die ihren Geltungsbereich durch Closures überdauern. Die `let`-Syntax akzeptiert eine durch Kommas getrennte Reihe von Zuweisungen und Variablennamen:

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

Die Zuweisungen werden der Reihe nach ausgewertet, wobei jede rechte Seite im Geltungsbereich ausgewertet wird, bevor die neue Variable auf der linken Seite eingeführt wird. Daher ist es sinnvoll, etwas wie `let x = x` zu schreiben, da die beiden `x`-Variablen unterschiedlich sind und separaten Speicher haben. Hier ist ein Beispiel, in dem das Verhalten von `let` benötigt wird:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

Hier erstellen und speichern wir zwei Closures, die die Variable `i` zurückgeben. Es ist jedoch immer dieselbe Variable `i`, sodass sich die beiden Closures identisch verhalten. Wir können `let` verwenden, um eine neue Bindung für `i` zu erstellen:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Da der `begin`-Konstruktion keinen neuen Gültigkeitsbereich einführt, kann es nützlich sein, ein null-Argument `let` zu verwenden, um einfach einen neuen Gültigkeitsbereichsblock einzuführen, ohne sofort neue Bindungen zu erstellen:

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

Da `let` einen neuen Block-Scope einführt, ist die innere lokale `x` eine andere Variable als die äußere lokale `x`. Dieses spezielle Beispiel ist äquivalent zu:

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Eine `for`-Schleife oder eine Komprehensions-Iterationsvariable ist immer eine neue Variable:

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

Es ist jedoch gelegentlich nützlich, eine vorhandene lokale Variable als Iterationsvariable wiederzuverwenden. Dies kann bequem durch Hinzufügen des Schlüsselworts `outer` erfolgen:

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

Ein gängiger Gebrauch von Variablen besteht darin, bestimmten, unveränderlichen Werten Namen zu geben. Solche Variablen werden nur einmal zugewiesen. Diese Absicht kann dem Compiler mit dem [`const`](@ref) Schlüsselwort vermittelt werden:

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

Mehrere Variablen können in einer einzelnen `const`-Anweisung deklariert werden:

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

Die `const`-Deklaration sollte nur im globalen Geltungsbereich für globale Variablen verwendet werden. Es ist für den Compiler schwierig, Code zu optimieren, der globale Variablen beinhaltet, da sich deren Werte (oder sogar deren Typen) fast jederzeit ändern können. Wenn eine globale Variable sich nicht ändern wird, löst das Hinzufügen einer `const`-Deklaration dieses Leistungsproblem.

Lokale Konstanten sind ganz anders. Der Compiler kann automatisch bestimmen, wann eine lokale Variable konstant ist, sodass lokale Konstantendeklarationen nicht erforderlich sind und derzeit tatsächlich nicht unterstützt werden.

Spezielle Top-Level-Zuweisungen, wie sie durch die Schlüsselwörter `function` und `struct` durchgeführt werden, sind standardmäßig konstant.

Beachten Sie, dass `const` nur die Bindung der Variablen betrifft; die Variable kann an ein veränderliches Objekt (wie ein Array) gebunden sein, und dieses Objekt kann weiterhin geändert werden. Darüber hinaus sind die folgenden Szenarien möglich, wenn man versucht, einen Wert einer konstant deklarierten Variablen zuzuweisen:

  * wenn ein neuer Wert einen anderen Typ hat als der Typ der Konstante, wird ein Fehler ausgelöst:

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * wenn ein neuer Wert denselben Typ wie die Konstante hat, wird eine Warnung ausgegeben:

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * Wenn eine Zuweisung nicht zu einer Änderung des Variablenwerts führt, wird keine Nachricht ausgegeben:

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

Die letzte Regel gilt für unveränderliche Objekte, selbst wenn die Variablenbindung sich ändern würde, z.B.:

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

Allerdings wird für veränderliche Objekte die Warnung wie erwartet ausgegeben:

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

Beachten Sie, dass es zwar manchmal möglich ist, der Wert einer `const`-Variablen zu ändern, dies jedoch stark abgeraten wird und nur zur Bequemlichkeit während der interaktiven Nutzung gedacht ist. Das Ändern von Konstanten kann verschiedene Probleme oder unerwartete Verhaltensweisen verursachen. Wenn beispielsweise eine Methode auf eine Konstante verweist und bereits kompiliert wurde, bevor die Konstante geändert wurde, könnte sie weiterhin den alten Wert verwenden:

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    Die Unterstützung für typisierte globale Variablen wurde in Julia 1.8 hinzugefügt.


Ähnlich wie bei der Deklaration von Konstanten können auch globale Bindungen als immer vom konstanten Typ deklariert werden. Dies kann entweder ohne Zuweisung eines tatsächlichen Wertes mit der Syntax `global x::T` oder bei der Zuweisung als `x::T = 123` erfolgen.

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

Für jede Zuweisung an eine globale Variable wird Julia zunächst versuchen, sie in den entsprechenden Typ zu konvertieren, indem sie [`convert`](@ref) verwendet:

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

Der Typ muss nicht konkret sein, aber Anmerkungen mit abstrakten Typen haben typischerweise wenig Leistungsgewinn.

Sobald ein globaler Wert entweder zugewiesen oder sein Typ festgelegt wurde, ist eine Änderung des Bindungstyps nicht erlaubt:

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```

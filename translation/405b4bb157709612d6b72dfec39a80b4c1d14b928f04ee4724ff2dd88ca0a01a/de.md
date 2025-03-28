# Julia ASTs

Julia hat zwei Darstellungen von Code. Zuerst gibt es eine Oberflächensyntax-AST, die vom Parser zurückgegeben wird (z. B. die [`Meta.parse`](@ref)-Funktion) und von Makros manipuliert wird. Es ist eine strukturierte Darstellung von Code, wie er geschrieben ist, die von `julia-parser.scm` aus einem Zeichenstrom konstruiert wird. Als Nächstes gibt es eine abgesenkte Form oder IR (intermediate representation), die von der Typinferenz und der Codegenerierung verwendet wird. In der abgesenkten Form gibt es weniger Arten von Knoten, alle Makros sind erweitert, und alle Kontrollflüsse werden in explizite Verzweigungen und Sequenzen von Anweisungen umgewandelt. Die abgesenkte Form wird von `julia-syntax.scm` konstruiert.

Zuerst werden wir uns auf den AST konzentrieren, da er benötigt wird, um Makros zu schreiben.

## Surface syntax AST

Frontend-ASTs bestehen fast ausschließlich aus [`Expr`](@ref)s und Atomen (z. B. Symbole, Zahlen). Es gibt im Allgemeinen einen anderen Ausdrucks-Kopf für jede visuell unterscheidbare syntaktische Form. Beispiele werden in s-Ausdruck-Syntax gegeben. Jede in Klammern gesetzte Liste entspricht einem Expr, wobei das erste Element der Kopf ist. Zum Beispiel entspricht `(call f x)` `Expr(:call, :f, :x)` in Julia.

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` Syntax:

```julia
f(x) do a,b
    body
end
```

parst als `(do (call f x) (-> (tuple a b) (block body)))`.

### Operators

Die meisten Verwendungen von Operatoren sind einfach Funktionsaufrufe, daher werden sie mit dem Kopf `call` geparst. Einige Operatoren sind jedoch spezielle Formen (nicht unbedingt Funktionsaufrufe), und in diesen Fällen ist der Operator selbst der Ausdruckskopf. In julia-parser.scm werden diese als "syntaktische Operatoren" bezeichnet. Einige Operatoren (`+` und `*`) verwenden N-ary Parsing; verkettete Aufrufe werden als ein einziger N-Argument-Aufruf geparst. Schließlich haben Ketten von Vergleichen ihre eigene spezielle Ausdrucksstruktur.

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

Docstring-Syntax:

```julia
"some docs"
f(x) = x
```

parst als `(macrocall (|.| Core '@doc) (line) "einige Dokumente" (= (call f x) (block x)))`.

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using` hat die gleiche Darstellung wie `import`, jedoch mit dem Ausdrucksanfang `:using` anstelle von `:import`.

### Numbers

Julia unterstützt mehr Zahlentypen als viele Scheme-Implementierungen, sodass nicht alle Zahlen direkt als Scheme-Zahlen im AST dargestellt werden.

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

Ein Block von Anweisungen wird als `(block stmt1 stmt2 ...)` geparst.

Wenn-Anweisung:

```julia
if a
    b
elseif c
    d
else
    e
end
```

parst als:

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

Eine `while`-Schleife wird als `(while Bedingung Körper)` interpretiert.

Eine `for`-Schleife wird als `(for (= var iter) body)` geparst. Wenn es mehr als eine Iterationsspezifikation gibt, werden sie als Block geparst: `(for (block (= v1 iter1) (= v2 iter2)) body)`.

`break` und `continue` werden als 0-Argument-Ausdrücke `(break)` und `(continue)` interpretiert.

`let` wird als `(let (= var val) body)` oder `(let (block (= var1 val1) (= var2 val2) ...) body)` geparst, ähnlich wie `for`-Schleifen.

Eine grundlegende Funktionsdefinition wird als `(function (call f x) body)` analysiert. Ein komplexeres Beispiel:

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

parst als:

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

Typdefinition:

```julia
mutable struct Foo{T<:S}
    x::T
end
```

parst als:

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

Das erste Argument ist ein Boolean, der angibt, ob der Typ veränderlich ist.

`try`-Blöcke werden als `(try try_block var catch_block finally_block)` geparst. Wenn nach `catch` keine Variable vorhanden ist, ist `var` `#f`. Wenn keine `finally`-Klausel vorhanden ist, fehlt das letzte Argument.

### Quote expressions

Julia-Quellsyntaxformen für Code-Zitierungen (`quote` und `:( )`) unterstützen die Interpolation mit `$`. In der Lisp-Terminologie bedeutet dies, dass sie tatsächlich "Backquote" oder "Quasiquote"-Formen sind. Intern gibt es auch die Notwendigkeit für Code-Zitierungen ohne Interpolation. In Julias Schemakode wird die nicht-interpolierende Zitierung mit dem Ausdrucks-Kopf `inert` dargestellt.

`inert` Ausdrücke werden in Julia `QuoteNode` Objekte umgewandelt. Diese Objekte umschließen einen einzelnen Wert beliebigen Typs und geben bei der Auswertung einfach diesen Wert zurück.

Ein `quote`-Ausdruck, dessen Argument ein Atom ist, wird ebenfalls in einen `QuoteNode` umgewandelt.

### Line numbers

Quellortinformationen werden als `(Zeile zeilen_num dateiname)` dargestellt, wobei die dritte Komponente optional ist (und weggelassen wird, wenn sich die aktuelle Zeilennummer, aber nicht der Dateiname, ändert).

Diese Ausdrücke werden in Julia als `LineNumberNode`s dargestellt.

### Macros

Makro-Hygiene wird durch den Ausdruck Kopf-Paar `escape` und `hygienic-scope` dargestellt. Das Ergebnis einer Makroerweiterung wird automatisch in `(hygienic-scope block module)` eingewickelt, um das Ergebnis des neuen Geltungsbereichs darzustellen. Der Benutzer kann `(escape block)` einfügen, um Code vom Aufrufer zu interpolieren.

## Lowered form

Die abgesenkte Form (IR) ist für den Compiler wichtiger, da sie für Typinferenz, Optimierungen wie Inlining und Codegenerierung verwendet wird. Sie ist auch weniger offensichtlich für den Menschen, da sie aus einer erheblichen Umstrukturierung der Eingabesyntax resultiert.

Zusätzlich zu `Symbol`s und einigen Zahlentypen existieren die folgenden Datentypen in gesenkter Form:

  * `Expr`

    Hat einen Knotentyp, der durch das `head`-Feld angezeigt wird, und ein `args`-Feld, das ein `Vector{Any}` von Unterausdrücken ist. Während fast jeder Teil eines Oberflächen-AST durch ein `Expr` dargestellt wird, verwendet das IR nur eine begrenzte Anzahl von `Expr`s, hauptsächlich für Aufrufe und einige nur auf oberster Ebene vorhandene Formen.
  * `SlotNummer`

    Identifiziert Argumente und lokale Variablen durch aufeinanderfolgende Nummerierung. Es hat ein ganzzahliges `id`-Feld, das den Slot-Index angibt. Die Typen dieser Slots können im `slottypes`-Feld ihres `CodeInfo`-Objekts gefunden werden.
  * `Argument`

    Das gleiche wie `SlotNumber`, erscheint jedoch nur nach der Optimierung. Zeigt an, dass der referenzierte Slot ein Argument der umschließenden Funktion ist.
  * `CodeInfo`

    Umhüllt die IR einer Gruppe von Anweisungen. Das `code`-Feld ist ein Array von Ausdrücken, die ausgeführt werden sollen.
  * `GotoNode`

    Unbedingter Sprung. Das Argument ist das Sprungziel, dargestellt als ein Index im Code-Array, zu dem gesprungen werden soll.
  * `GotoIfNot`

    Bedingte Verzweigung. Wenn das Feld `cond` auf falsch ausgewertet wird, geht es zu dem durch das Feld `dest` identifizierten Index.
  * `ReturnNode`

    Gibt sein Argument (das `val`-Feld) als den Wert der umschließenden Funktion zurück. Wenn das `val`-Feld undefiniert ist, stellt dies eine unerreichbare Anweisung dar.
  * `ZitatKnoten`

    Wickelt einen beliebigen Wert, um ihn als Daten zu referenzieren. Zum Beispiel enthält die Funktion `f() = :a` einen `QuoteNode`, dessen `value`-Feld das Symbol `a` ist, um das Symbol selbst zurückzugeben, anstatt es auszuwerten.
  * `GlobalRef`

    Bezieht sich auf die globale Variable `name` im Modul `mod`.
  * `SSAValue`

    Bezieht sich auf eine fortlaufend nummerierte (beginnend bei 1) statische Ein-Zuweisung (SSA) Variable, die vom Compiler eingefügt wurde. Die Nummer (`id`) eines `SSAValue` ist der Code-Array-Index des Ausdrucks, dessen Wert sie darstellt.
  * `NewvarNode`

    Markiert einen Punkt, an dem eine Variable (Slot) erstellt wird. Dies hat zur Folge, dass eine Variable auf undefiniert zurückgesetzt wird.

### `Expr` types

Diese Symbole erscheinen im `head`-Feld von [`Expr`](@ref) in kleingeschriebener Form.

  * `anrufen`

    Funktionsaufruf (dynamische Dispatch). `args[1]` ist die aufzurufende Funktion, `args[2:end]` sind die Argumente.
  * `aufrufen`

    Funktionsaufruf (statische Dispatch). `args[1]` ist die MethodInstance, die aufgerufen werden soll, `args[2:end]` sind die Argumente (einschließlich der Funktion, die aufgerufen wird, bei `args[2]`).
  * `statischer_parameter`

    Verweisen Sie auf einen statischen Parameter nach Index.
  * `=`

    Aufgabe. Im IR ist das erste Argument immer eine `SlotNumber` oder ein `GlobalRef`.
  * `Methode`

    Fügt einer generischen Funktion eine Methode hinzu und weist das Ergebnis bei Bedarf zu.

    Hat eine 1-Argument-Form und eine 3-Argument-Form. Die 1-Argument-Form ergibt sich aus der Syntax `function foo end`. In der 1-Argument-Form ist das Argument ein Symbol. Wenn dieses Symbol bereits eine Funktion im aktuellen Gültigkeitsbereich benennt, passiert nichts. Wenn das Symbol undefiniert ist, wird eine neue Funktion erstellt und dem durch das Symbol angegebenen Bezeichner zugewiesen. Wenn das Symbol definiert ist, aber eine Nicht-Funktion benennt, wird ein Fehler ausgelöst. Die Definition von "benennt eine Funktion" ist, dass die Bindung konstant ist und auf ein Objekt vom Singleton-Typ verweist. Der Grund dafür ist, dass eine Instanz eines Singleton-Typs den Typ eindeutig identifiziert, um die Methode hinzuzufügen. Wenn der Typ Felder hat, wäre es unklar, ob die Methode der Instanz oder ihrem Typ hinzugefügt wird.

    Die 3-Argument-Form hat die folgenden Argumente:

      * `args[1]`

        Ein Funktionsname oder `nichts`, wenn unbekannt oder nicht benötigt. Wenn ein Symbol, verhält sich der Ausdruck zuerst wie die oben genannte 1-Argument-Form. Dieses Argument wird von da an ignoriert. Es kann `nichts` sein, wenn Methoden strikt nach Typ hinzugefügt werden, `(::T)(x) = x`, oder wenn eine Methode zu einer bestehenden Funktion hinzugefügt wird, `MyModule.f(x) = x`.
      * `args[2]`

        Ein `SimpleVector` des Argumenttyps Daten. `args[2][1]` ist ein `SimpleVector` der Argumenttypen, und `args[2][2]` ist ein `SimpleVector` der Typvariablen, die den statischen Parametern der Methode entsprechen.
      * `args[3]`

        Ein `CodeInfo` der Methode selbst. Für "außerhalb des Geltungsbereichs" liegende Methodendefinitionen (Hinzufügen einer Methode zu einer Funktion, die auch Methoden in verschiedenen Geltungsbereichen definiert hat) handelt es sich um einen Ausdruck, der zu einem `:lambda`-Ausdruck ausgewertet wird.
  * `struct_type`

    Ein 7-Argument-Ausdruck, der eine neue `struct` definiert:

      * `args[1]`

        Der Name der `struct`
      * `args[2]`

        Ein `call`-Ausdruck, der einen `SimpleVector` erstellt und seine Parameter angibt.
      * `args[3]`

        Ein `call`-Ausdruck, der einen `SimpleVector` erstellt und seine Feldnamen angibt.
      * `args[4]`

        Ein `Symbol`, `GlobalRef` oder `Expr`, der den Supertyp angibt (z. B. `:Integer`, `GlobalRef(Core, :Any)` oder `:(Core.apply_type(AbstractArray, T, N))`)
      * `args[5]`

        Ein `call`-Ausdruck, der einen `SimpleVector` erstellt und seine Feldtypen angibt.
      * `args[6]`

        Ein Bool, wahr wenn `mutable`
      * `args[7]`

        Die Anzahl der Argumente zur Initialisierung. Dies wird die Anzahl der Felder sein oder die minimale Anzahl der Felder, die durch die `new`-Anweisung eines inneren Konstruktors aufgerufen werden.
  * `abstract_type`

    Ein 3-Argument-Ausdruck, der einen neuen abstrakten Typ definiert. Die Argumente sind dieselben wie die Argumente 1, 2 und 4 von `struct_type`-Ausdrücken.
  * `primitive_type`

    Ein 4-Argumente-Ausdruck, der einen neuen primitiven Typ definiert. Die Argumente 1, 2 und 4 sind dieselben wie `struct_type`. Argument 3 ist die Anzahl der Bits.

    !!! compat "Julia 1.5"
        `struct_type`, `abstract_type` und `primitive_type` wurden in Julia 1.5 entfernt und durch Aufrufe neuer Built-ins ersetzt.
  * `global`

    Deklariert eine globale Bindung.
  * `const`

    Deklariert eine (globale) Variable als konstant.
  * `neu`

    Allokiert ein neues struct-ähnliches Objekt. Das erste Argument ist der Typ. Die [`new`](@ref) Pseudo-Funktion wird darauf reduziert, und der Typ wird immer vom Compiler eingefügt. Dies ist eine sehr interne Funktion und führt keine Überprüfungen durch. Die Auswertung beliebiger `new`-Ausdrücke kann leicht zu einem Segfault führen.
  * `splatnew`

    Ähnlich wie `new`, außer dass die Feldwerte als ein einzelnes Tupel übergeben werden. Funktioniert ähnlich wie `splat(new)`, wenn `new` eine erstklassige Funktion wäre, daher der Name.
  * `isdefined`

    `Expr(:isdefined, :x)` gibt einen Bool zurück, der angibt, ob `x` im aktuellen Gültigkeitsbereich bereits definiert wurde.
  * `die_ausnahme`

    Gibt die gefangene Ausnahme innerhalb eines `catch`-Blocks zurück, wie von `jl_current_exception(ct)` zurückgegeben.
  * `enter`

    Tritt in einen Ausnahmebehandler (`setjmp`) ein. `args[1]` ist das Label des Catch-Blocks, zu dem bei einem Fehler gesprungen werden soll. Gibt ein Token zurück, das von `pop_exception` verbraucht wird.
  * `Urlaub`

    Pop-Ausnahmebehandler. `args[1]` ist die Anzahl der zu entfernenden Behandler.
  * `pop_exception`

    Poppen Sie den Stapel der aktuellen Ausnahmen zurück in den Zustand beim zugehörigen `enter`, wenn Sie einen Catch-Block verlassen. `args[1]` enthält das Token vom zugehörigen `enter`.

    !!! compat "Julia 1.1"
        `pop_exception` ist neu in Julia 1.1.
  * `inbounds`

    Steuert das Aktivieren oder Deaktivieren von Grenzprüfungen. Ein Stack wird verwaltet; wenn das erste Argument dieses Ausdrucks wahr oder falsch ist (`true` bedeutet, dass die Grenzprüfungen deaktiviert sind), wird es auf den Stack gelegt. Wenn das erste Argument `:pop` ist, wird der Stack geleert.
  * `boundscheck`

    Hat den Wert `false`, wenn es in einen Codeabschnitt eingefügt wird, der mit `@inbounds` gekennzeichnet ist, andernfalls hat es den Wert `true`.
  * `loopinfo`

    Markiert das Ende einer Schleife. Enthält Metadaten, die an `LowerSimdLoop` übergeben werden, um entweder die innere Schleife eines `@simd`-Ausdrucks zu kennzeichnen oder Informationen an LLVM-Schleifenpässe weiterzugeben.
  * `copyast`

    Teil der Implementierung von Quasi-Zitaten. Das Argument ist ein Oberflächensyntax-AST, der einfach rekursiv kopiert und zur Laufzeit zurückgegeben wird.
  * `meta`

    Metadaten. `args[1]` ist typischerweise ein Symbol, das die Art der Metadaten angibt, und die restlichen Argumente sind frei formatiert. Die folgenden Arten von Metadaten werden häufig verwendet:

      * `:inline` und `:noinline`: Inlining-Hinweise.
  * `foreigncall`

    Statisch berechneter Container für `ccall`-Informationen. Die Felder sind:

      * `args[1]` : Name

        Der Ausdruck, der für die Fremdfunktion geparst wird.
      * `args[2]::Type` : RT

        Der (wörtliche) Rückgabetyp, der statisch berechnet wird, wenn die umgebende Methode definiert wurde.
      * `args[3]::SimpleVector` (von Typen) : AT

        Der (wörtliche) Vektor der Argumenttypen, der statisch berechnet wird, wenn die enthaltene Methode definiert wurde.
      * `args[4]::Int` : nreq

        Die Anzahl der erforderlichen Argumente für eine Varargs-Funktionsdefinition.
      * `args[5]::QuoteNode{Symbol}` : Aufrufkonvention

        Die Aufrufkonvention für den Aufruf.
      * `args[6:5+length(args[3])]` : Argumente

        Die Werte für alle Argumente (mit den Typen von jedem in args[3] angegeben).
      * `args[6+length(args[3])+1:end]` : gc-wurzeln

        Die zusätzlichen Objekte, die während des Aufrufs gc-rooted werden müssen. Siehe [Working with LLVM](@ref Working-with-LLVM) für die Herkunft und wie sie behandelt werden.
  * `new_opaque_closure`

    Konstruiert einen neuen undurchsichtigen Closure. Die Felder sind:

      * `args[1]` : Signatur

        Die Funktionssignatur des opaken Closures. Opake Closures nehmen nicht am Dispatch teil, aber die Eingabetypen können eingeschränkt werden.
      * `args[2]` : isva

        Gibt an, ob der Closure varargs akzeptiert.
      * `args[3]` : lb

        Untergrenze für den Ausgabetyp. (Standardmäßig `Union{}`)
      * `args[4]` : ub

        Obergrenze für den Ausgabetyp. (Standardmäßig `Any`)
      * `args[5]` : Methode

        Die tatsächliche Methode als `opaque_closure_method` Ausdruck.
      * `args[6:end]` : erfasst

        Die Werte, die durch den undurchsichtigen Abschluss erfasst werden.

    !!! compat "Julia 1.7"
        Intransparente Closures wurden in Julia 1.7 hinzugefügt.

### [Method](@id ast-lowered-method)

Ein einzigartiger Container, der die gemeinsamen Metadaten für eine einzelne Methode beschreibt.

  * `name`, `modul`, `datei`, `zeile`, `sig`

    Metadaten zur eindeutigen Identifizierung der Methode für den Computer und den Menschen.
  * `ambig`

    Cache anderer Methoden, die mit dieser hier möglicherweise mehrdeutig sind.
  * `spezialisierungen`

    Cache aller jemals für diese Methode erstellten MethodInstance, die zur Gewährleistung der Einzigartigkeit verwendet wird. Einzigartigkeit ist für die Effizienz erforderlich, insbesondere für die inkrementelle Vorabkompilierung und die Verfolgung der Ungültigkeit von Methoden.
  * `Quelle`

    Der ursprüngliche Quellcode (sofern verfügbar, normalerweise komprimiert).
  * `Generator`

    Ein aufrufbares Objekt, das ausgeführt werden kann, um spezialisierten Quellcode für eine bestimmte Methodensignatur zu erhalten.
  * `Wurzeln`

    Zeiger auf Nicht-AST-Dinge, die in den AST interpoliert wurden, erforderlich durch die Kompression des AST, Typinferenz oder die Generierung von nativen Code.
  * `nargs`, `isva`, `called`, `is_for_opaque_closure`,

    Beschreibende Bitfelder für den Quellcode dieser Methode.
  * `primäre_welt`

    Das Weltzeitalter, das diese Methode "besitzt".

### MethodInstance

Ein einzigartiger Container, der eine einzelne aufrufbare Signatur für eine Methode beschreibt. Siehe insbesondere [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks) für wichtige Details, wie man diese Felder sicher ändern kann.

  * `specTypes`

    Der Primärschlüssel für diese MethodInstance. Die Eindeutigkeit wird durch eine `def.specializations`-Suche garantiert.
  * `def`

    Die `Methode`, die diese Funktion beschreibt, ist eine Spezialisierung. Oder ein `Modul`, wenn dies ein top-level Lambda ist, das im Modul erweitert wurde und nicht Teil einer Methode ist.
  * `sparam_vals`

    Die Werte der statischen Parameter in `specTypes`. Für die `MethodInstance` bei `Method.unspecialized` ist dies der leere `SimpleVector`. Aber für eine Laufzeit-`MethodInstance` aus dem `MethodTable`-Cache wird dies immer definiert und indexierbar sein.
  * `uninferred`

    Der unkomprimierte Quellcode für einen Top-Level-Thunk. Darüber hinaus ist dies für eine generierte Funktion einer von vielen Orten, an denen der Quellcode gefunden werden kann.
  * `Rückkanten`

    Wir speichern die Rückwärtsliste der Cache-Abhängigkeiten für eine effiziente Verfolgung der inkrementellen Neuanalyse/-kompilierungsarbeiten, die nach neuen Methodendefinitionen erforderlich sein können. Dies funktioniert, indem eine Liste der anderen `MethodInstance` geführt wird, die abgeleitet oder optimiert wurden, um einen möglichen Aufruf zu dieser `MethodInstance` zu enthalten. Diese Optimierungsergebnisse könnten irgendwo im `cache` gespeichert sein, oder es könnte das Ergebnis von etwas gewesen sein, das wir nicht cachen wollten, wie z. B. Konstantenpropagation. Daher fügen wir all diese Rückkanten zu verschiedenen Cache-Einträgen hier zusammen (es gibt fast immer nur den einen anwendbaren Cache-Eintrag mit einem Sentinelwert für max_world).
  * `Cache`

    Cache von `CodeInstance`-Objekten, die diese Template-Instanziierung teilen.

### CodeInstance

  * `def`

    Der `MethodInstance`, von dem dieser Cache-Eintrag abgeleitet ist.
  * `Besitzer`

    Ein Token, das den Besitzer dieser `CodeInstance` repräsentiert. Wird `jl_egal` verwenden, um Übereinstimmungen zu finden.

  * `rettype`/`rettype_const`

    Der abgeleitete Rückgabetyp für das Feld `specFunctionObject`, das (in den meisten Fällen) auch der berechnete Rückgabetyp für die Funktion im Allgemeinen ist.
  * `abgeleitet`

    Kann einen Cache der abgeleiteten Quelle für diese Funktion enthalten, oder es könnte auf `nichts` gesetzt werden, um einfach anzuzeigen, dass `rettype` abgeleitet ist.
  * `ftpr`

    Der generische jlcall-Einstiegspunkt.
  * `jlcall_api`

    Die ABI, die beim Aufrufen von `fptr` verwendet werden soll. Einige bedeutende sind:

      * 0 - Noch nicht kompiliert
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - Konstante (Wert, der in `rettype_const` gespeichert ist)
      * 3 - Mit statischen Parametern weitergeleitet `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - Führen Sie im Interpreter aus `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_world` / `max_world`

    Der Bereich der Weltalter, für den diese Methodeninstanz gültig ist, um aufgerufen zu werden. Wenn max_world der spezielle Tokenwert `-1` ist, ist der Wert noch nicht bekannt. Er kann weiterhin verwendet werden, bis wir auf eine Rückkante stoßen, die uns zwingt, dies zu überdenken.

### CodeInfo

Ein (normalerweise temporärer) Behälter zum Halten von gesenktem Quellcode.

  * `code`

    Ein `Any`-Array von Aussagen
  * `slotnamen`

    Ein Array von Symbolen, die Namen für jeden Slot (Argument oder lokale Variable) geben.
  * `slotflags`

    Ein `UInt8`-Array von Slot-Eigenschaften, dargestellt als Bit-Flags:

      * 0x02 - zugewiesen (nur falsch, wenn es *keine* Zuweisungsanweisungen mit dieser Variablen auf der linken Seite gibt)
      * 0x08 - verwendet (wenn es eine Lese- oder Schreiboperation des Slots gibt)
      * 0x10 - statisch einmal zugewiesen
      * 0x20 - könnte vor der Zuweisung verwendet werden. Dieses Flag ist nur nach der Typinferenz gültig.
  * `ssavaluetypes`

    Entweder ein Array oder ein `Int`.

    Wenn es sich um ein `Int` handelt, gibt es die Anzahl der vom Compiler eingefügten temporären Speicherorte in der Funktion an (die Länge des `code`-Arrays). Wenn es sich um ein Array handelt, wird ein Typ für jeden Speicherort angegeben.
  * `ssaflags`

    Aussageebene 32-Bit-Flags für jeden Ausdruck in der Funktion. Siehe die Definition von `jl_code_info_t` in julia.h für weitere Details.
  * `linetable`

    Ein Array von Quellstandortobjekten
  * `codelocs`

    Ein Array von ganzzahligen Indizes in die `linetable`, das den Standort angibt, der mit jeder Anweisung verbunden ist.

Optionale Felder:

  * `slottypes`

    Ein Array von Typen für die Slots.
  * `rettype`

    Der abgeleitete Rückgabetyp der gesenkten Form (IR). Der Standardwert ist `Any`.
  * `method_for_inference_limit_heuristics`

    Die `method_for_inference_heuristics` wird den Generator der gegebenen Methode bei Bedarf während der Inferenz erweitern.
  * `Eltern`

    Das `MethodInstance`, das dieses Objekt "besitzt" (falls zutreffend).
  * `Kanten`

    Leiten Sie Kanten zu Methodeninstanzen weiter, die ungültig gemacht werden müssen.
  * `min_world`/`max_world`

    Der Bereich der Weltalter, für den dieser Code zum Zeitpunkt seiner Ableitung gültig war.

Boolesche Eigenschaften:

  * `abgeleitet`

    Ob es durch Typinferenz erzeugt wurde.
  * `inlineable`

    Ob es für das Inlining in Frage kommen sollte.
  * `propagate_inbounds`

    Ob es `@inbounds` propagieren sollte, wenn es zum Zweck des Auslassens von `@boundscheck`-Blöcken inlinet wird.

`UInt8` Einstellungen:

  * `constprop`

      * 0 = Heuristik verwenden
      * 1 = aggressiv
      * 2 = keine
  * `purity` Konstruiert aus 5 Bit-Flags:

      * 0x01 << 0 = Diese Methode garantiert, dass sie konsistent zurückgibt oder terminiert (`:consistent`)
      * 0x01 << 1 = Diese Methode ist frei von extern sichtbaren semantischen Nebenwirkungen (`:effect_free`)
      * 0x01 << 2 = Diese Methode garantiert, dass keine Ausnahme ausgelöst wird (`:nothrow`)
      * 0x01 << 3 = Diese Methode garantiert, dass sie terminiert (`:terminates_globally`)
      * 0x01 << 4 = Der syntaktische Kontrollfluss innerhalb dieser Methode ist garantiert, dass er terminiert (`:terminates_locally`)

    Siehe die Dokumentation von `Base.@assume_effects` für weitere Details.

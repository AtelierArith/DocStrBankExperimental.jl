# [Variables](@id man-variables)

Eine Variable in Julia ist ein Name, der mit einem Wert verknüpft (oder gebunden) ist. Sie ist nützlich, wenn Sie einen Wert speichern möchten (den Sie beispielsweise nach einigen Berechnungen erhalten haben) für eine spätere Verwendung. Zum Beispiel:

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

Julia bietet ein äußerst flexibles System zur Benennung von Variablen. Variablennamen sind groß- und kleinschreibungssensitiv und haben keine semantische Bedeutung (das heißt, die Sprache behandelt Variablen nicht unterschiedlich basierend auf ihren Namen).

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

Unicode-Namen (in UTF-8-Codierung) sind erlaubt:

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

Im Julia REPL und in mehreren anderen Julia-Bearbeitungsumgebungen können Sie viele Unicode-Mathematiksymbole eingeben, indem Sie den umgekehrten Schrägstrich gefolgt vom LaTeX-Symbolnamen und dann die Tabulatortaste eingeben. Zum Beispiel kann der Variablenname `δ` eingegeben werden, indem Sie `\delta`-*tab* eingeben, oder sogar `α̂⁽²⁾` durch `\alpha`-*tab*-`\hat`-*tab*-`\^(2)`-*tab*. (Wenn Sie ein Symbol irgendwo finden, z. B. im Code eines anderen, das Sie nicht wissen, wie man es eingibt, wird Ihnen die REPL-Hilfe sagen: Geben Sie einfach `?` ein und fügen Sie dann das Symbol ein.)

Julia erlaubt es Ihnen sogar, vorhandene exportierte Konstanten und Funktionen mit lokalen zu überschreiben (obwohl dies nicht empfohlen wird, um potenzielle Verwirrungen zu vermeiden):

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

Wenn Sie jedoch versuchen, eine eingebaute Konstante oder Funktion, die bereits verwendet wird, neu zu definieren, gibt Ihnen Julia einen Fehler aus:

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

Variablenamen müssen mit einem Buchstaben (A-Z oder a-z), einem Unterstrich oder einer Teilmenge von Unicode-Codepunkten, die größer als 00A0 sind, beginnen; insbesondere [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl (Buchstaben), Sc/So (Währungs- und andere Symbole) und einige andere buchstabenähnliche Zeichen (z. B. eine Teilmenge der Sm-Mathematiksymbole) sind erlaubt. Nachfolgende Zeichen können auch ! und Ziffern (0-9 und andere Zeichen in den Kategorien Nd/No) sowie andere Unicode-Codepunkte enthalten: diakritische Zeichen und andere modifizierende Zeichen (Kategorien Mn/Mc/Me/Sk), einige Interpunktionsverbindungen (Kategorie Pc), Primzahlen und einige andere Zeichen.

Operatoren wie `+` sind ebenfalls gültige Bezeichner, werden jedoch speziell geparst. In einigen Kontexten können Operatoren wie Variablen verwendet werden; zum Beispiel bezieht sich `(+)` auf die Additionsfunktion, und `(+) = f` wird sie neu zuweisen. Die meisten Unicode-Infix-Operatoren (in der Kategorie Sm), wie `⊕`, werden als Infix-Operatoren geparst und stehen für benutzerdefinierte Methoden zur Verfügung (z. B. können Sie `const ⊗ = kron` verwenden, um `⊗` als Infix-Kronecker-Produkt zu definieren). Operatoren können auch mit modifizierenden Zeichen, Primzahlen und Sub-/Superskripten versehen werden, z. B. wird `+̂ₐ″` als Infix-Operator mit der gleichen Priorität wie `+` geparst. Ein Leerzeichen ist erforderlich zwischen einem Operator, der mit einem Subskript-/Superskriptbuchstaben endet, und einem nachfolgenden Variablennamen. Wenn `+ᵃ` ein Operator ist, muss `+ᵃx` als `+ᵃ x` geschrieben werden, um es von `+ ᵃx` zu unterscheiden, wobei `ᵃx` der Variablenname ist.

Eine bestimmte Klasse von Variablennamen ist eine, die nur Unterstriche enthält. Diese Bezeichner sind schreibgeschützt. Das heißt, sie können nur Werte zugewiesen bekommen, die sofort verworfen werden, und ihre Werte können auf keine Weise verwendet werden.

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

Einige Unicode-Zeichen werden in Bezeichnern als äquivalent betrachtet. Verschiedene Möglichkeiten zur Eingabe von Unicode-Kombinationszeichen (z. B. Akzenten) werden als äquivalent behandelt (insbesondere sind Julia-Bezeichner [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence). Julia umfasst auch einige nicht-standardmäßige Äquivalenzen für Zeichen, die visuell ähnlich sind und von einigen Eingabemethoden leicht eingegeben werden können. Die Unicode-Zeichen `ɛ` (U+025B: Lateinischer Kleinbuchstabe offenes e) und `µ` (U+00B5: Mikrosymbol) werden als äquivalent zu den entsprechenden griechischen Buchstaben betrachtet. Der Mittelpunkt `·` (U+00B7) und das griechische [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) werden beide als der mathematische Punktoperator `⋅` (U+22C5) behandelt. Das Minuszeichen `−` (U+2212) wird als äquivalent zum Bindestrich-Minuszeichen `-` (U+002D) betrachtet.

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

Eine Zuweisung `variable = value` "bindet" den Namen `variable` an den `value`, der auf der rechten Seite berechnet wird, und die gesamte Zuweisung wird von Julia als Ausdruck behandelt, der dem `value` auf der rechten Seite entspricht. Das bedeutet, dass Zuweisungen *verkettet* werden können (der gleiche `value` wird mehreren Variablen zugewiesen mit `variable1 = variable2 = value`) oder in anderen Ausdrücken verwendet werden können, und das ist auch der Grund, warum ihr Ergebnis im REPL als der Wert der rechten Seite angezeigt wird. (Im Allgemeinen zeigt der REPL den Wert des Ausdrucks an, den Sie auswerten.) Zum Beispiel wird hier der Wert `4` von `b = 2+2` in einer anderen arithmetischen Operation und Zuweisung verwendet:

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

Eine häufige Verwirrung ist der Unterschied zwischen *Zuweisung* (einen neuen "Namen" einem Wert zu geben) und *Mutation* (einen Wert zu ändern). Wenn Sie `a = 2` gefolgt von `a = 3` ausführen, haben Sie den "Namen" `a` geändert, um auf einen neuen Wert `3` zu verweisen … Sie haben die Zahl `2` nicht geändert, sodass `2+2` immer noch `4` und nicht `6` ergibt! Diese Unterscheidung wird klarer, wenn man mit *veränderbaren* Typen wie [arrays](@ref lib-arrays) umgeht, deren Inhalte *geändert* werden können:

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

Hier macht die Zeile `b = a` *keine* Kopie des Arrays `a`, sie bindet einfach den Namen `b` an dasselbe Array `a`: sowohl `b` als auch `a` "zeigen" auf dasselbe Array `[1,2,3]` im Speicher. Im Gegensatz dazu *ändert* eine Zuweisung `a[i] = value` die *Inhalte* des Arrays, und das modifizierte Array wird durch beide Namen `a` und `b` sichtbar sein:

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

Das heißt, `a[i] = value` (ein Alias für [`setindex!`](@ref)) *verändert* ein bestehendes Array-Objekt im Speicher, das entweder über `a` oder `b` zugänglich ist. Das anschließende Setzen von `a = 3.14159` ändert dieses Array nicht, es bindet einfach `a` an ein anderes Objekt; das Array ist weiterhin über `b` zugänglich. Eine weitere gängige Syntax zur Veränderung eines bestehenden Objekts ist `a.field = value` (ein Alias für [`setproperty!`](@ref)), die verwendet werden kann, um ein [`mutable struct`](@ref) zu ändern. Es gibt auch Mutationen über Punktzuweisungen, zum Beispiel `b .= 5:7` (was unser Array `b` vor Ort verändert, um `[5,6,7]` zu enthalten), als Teil von Julias [vectorized "dot" syntax](@ref man-dot-operators).

Wenn Sie eine [function](@ref man-functions) in Julia aufrufen, verhält sie sich so, als ob Sie die Argumentwerte neuen Variablennamen zugewiesen hätten, die den Funktionsargumenten entsprechen, wie in [Argument-Passing Behavior](@ref man-argument-passing) besprochen. (Durch [convention](@ref man-punctuation) haben Funktionen, die eines oder mehrere ihrer Argumente ändern, Namen, die mit `!` enden.)

## Stylistic Conventions

Während Julia nur wenige Einschränkungen für gültige Namen auferlegt, hat es sich als nützlich erwiesen, die folgenden Konventionen zu übernehmen:

  * Die Namen der Variablen sind in Kleinbuchstaben.
  * Die Trennung von Wörtern kann durch Unterstriche (`'_'`) angezeigt werden, aber die Verwendung von Unterstrichen wird nicht empfohlen, es sei denn, der Name wäre sonst schwer zu lesen.
  * Die Namen von `Type`s und `Module`s beginnen mit einem Großbuchstaben, und die Worttrennung wird durch Upper Camel Case anstelle von Unterstrichen angezeigt.
  * Die Namen von `function`s und `macro`s sind in Kleinbuchstaben, ohne Unterstriche.
  * Funktionen, die ihre Argumente verändern, haben Namen, die mit `!` enden. Diese werden manchmal als "mutierende" oder "in-place" Funktionen bezeichnet, da sie darauf abzielen, Änderungen an ihren Argumenten vorzunehmen, nachdem die Funktion aufgerufen wurde, und nicht nur einen Wert zurückzugeben.

Für weitere Informationen zu stilistischen Konventionen siehe die [Style Guide](@ref).

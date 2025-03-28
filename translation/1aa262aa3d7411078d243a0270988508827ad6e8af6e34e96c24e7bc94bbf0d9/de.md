# [Strings](@id man-strings)

Strings sind endliche Sequenzen von Zeichen. Natürlich kommt das eigentliche Problem, wenn man fragt, was ein Zeichen ist. Die Zeichen, mit denen englischsprachige Personen vertraut sind, sind die Buchstaben `A`, `B`, `C` usw., zusammen mit Ziffern und gängigen Satzzeichen. Diese Zeichen sind zusammen mit einer Zuordnung zu ganzzahligen Werten zwischen 0 und 127 durch den [ASCII](https://en.wikipedia.org/wiki/ASCII) Standard standardisiert. Es gibt natürlich viele andere Zeichen, die in nicht-englischen Sprachen verwendet werden, einschließlich Varianten der ASCII-Zeichen mit Akzenten und anderen Modifikationen, verwandten Schriften wie Kyrillisch und Griechisch sowie Schriften, die völlig unabhängig von ASCII und Englisch sind, einschließlich Arabisch, Chinesisch, Hebräisch, Hindi, Japanisch und Koreanisch. Der [Unicode](https://en.wikipedia.org/wiki/Unicode) Standard befasst sich mit den Komplexitäten dessen, was genau ein Zeichen ist, und wird allgemein als der definitive Standard angesehen, der dieses Problem anspricht. Je nach Ihren Bedürfnissen können Sie entweder diese Komplexitäten vollständig ignorieren und einfach so tun, als ob nur ASCII-Zeichen existieren, oder Sie können Code schreiben, der mit beliebigen Zeichen oder Kodierungen umgehen kann, die man beim Umgang mit nicht-ASCII-Text antreffen kann. Julia macht den Umgang mit einfachem ASCII-Text einfach und effizient, und der Umgang mit Unicode ist so einfach und effizient wie möglich. Insbesondere können Sie C-ähnlichen String-Code schreiben, um ASCII-Strings zu verarbeiten, und sie werden wie erwartet funktionieren, sowohl in Bezug auf Leistung als auch Semantik. Wenn solcher Code auf nicht-ASCII-Text stößt, wird er elegant mit einer klaren Fehlermeldung fehlschlagen, anstatt stillschweigend fehlerhafte Ergebnisse einzuführen. Wenn dies geschieht, ist es unkompliziert, den Code zu ändern, um nicht-ASCII-Daten zu verarbeiten.

Es gibt einige bemerkenswerte hochrangige Merkmale von Julias Strings:

  * Der integrierte Beton-Typ, der für Strings (und String-Literale) in Julia verwendet wird, ist [`String`](@ref). Dies unterstützt die gesamte Palette von [Unicode](https://en.wikipedia.org/wiki/Unicode) Zeichen über die [UTF-8](https://en.wikipedia.org/wiki/UTF-8) Kodierung. (Eine [`transcode`](@ref) Funktion wird bereitgestellt, um zwischen anderen Unicode-Kodierungen zu konvertieren.)
  * Alle Stringtypen sind Untertypen des abstrakten Typs `AbstractString`, und externe Pakete definieren zusätzliche `AbstractString`-Untertypen (z. B. für andere Kodierungen). Wenn Sie eine Funktion definieren, die ein String-Argument erwartet, sollten Sie den Typ als `AbstractString` deklarieren, um jeden Stringtyp zu akzeptieren.
  * Wie C und Java, aber im Gegensatz zu den meisten dynamischen Sprachen hat Julia einen erstklassigen Typ zur Darstellung eines einzelnen Zeichens, genannt [`AbstractChar`](@ref). Der eingebaute [`Char`](@ref) Untertyp von `AbstractChar` ist ein 32-Bit-Primitivtyp, der jedes Unicode-Zeichen darstellen kann (und der auf der UTF-8-Codierung basiert).
  * Wie in Java sind Strings unveränderlich: Der Wert eines `AbstractString`-Objekts kann nicht geändert werden. Um einen anderen String-Wert zu erstellen, konstruieren Sie einen neuen String aus Teilen anderer Strings.
  * Konzeptionell ist ein String eine *partielle Funktion* von Indizes zu Zeichen: Für einige Indexwerte wird kein Zeichenwert zurückgegeben, und stattdessen wird eine Ausnahme ausgelöst. Dies ermöglicht eine effiziente Indizierung von Strings durch den Byte-Index einer kodierten Darstellung anstelle eines Zeichenindex, der für variable Breitenkodierungen von Unicode-Strings nicht sowohl effizient als auch einfach implementiert werden kann.

## [Characters](@id man-characters)

Ein `Char`-Wert repräsentiert ein einzelnes Zeichen: Es ist einfach ein 32-Bit-Primitive-Typ mit einer speziellen literalen Darstellung und entsprechenden arithmetischen Verhaltensweisen, und der in einen numerischen Wert umgewandelt werden kann, der [Unicode code point](https://en.wikipedia.org/wiki/Code_point) darstellt. (Julia-Pakete können andere Untertypen von `AbstractChar` definieren, z. B. um Operationen für andere [text encodings](https://en.wikipedia.org/wiki/Character_encoding) zu optimieren.) Hier ist, wie `Char`-Werte eingegeben und angezeigt werden (beachten Sie, dass Zeichenliterale mit einfachen Anführungszeichen und nicht mit doppelten Anführungszeichen begrenzt sind):

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

Sie können ein `Char` ganz einfach in seinen ganzzahligen Wert, d.h. den Codepunkt, umwandeln:

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

Auf 32-Bit-Architekturen wird [`typeof(c)`](@ref) zu [`Int32`](@ref). Sie können einen ganzzahligen Wert ebenso einfach wieder in ein `Char` umwandeln:

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

Nicht alle Ganzzahlen sind gültige Unicode-Codepunkte, aber aus Leistungsgründen überprüft die `Char`-Konvertierung nicht, ob jeder Zeichenwert gültig ist. Wenn Sie überprüfen möchten, ob jeder konvertierte Wert ein gültiger Codepunkt ist, verwenden Sie die [`isvalid`](@ref)-Funktion:

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

Zum Zeitpunkt dieses Schreibens sind die gültigen Unicode-Codepunkte `U+0000` bis `U+D7FF` und `U+E000` bis `U+10FFFF`. Diese wurden noch nicht alle mit verständlichen Bedeutungen versehen, noch sind sie notwendigerweise von Anwendungen interpretierbar, aber all diese Werte gelten als gültige Unicode-Zeichen.

Sie können jedes Unicode-Zeichen in einfachen Anführungszeichen mit `\u`, gefolgt von bis zu vier hexadezimalen Ziffern, oder `\U`, gefolgt von bis zu acht hexadezimalen Ziffern (der längste gültige Wert erfordert nur sechs), eingeben:

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

Julia verwendet die Locale- und Spracheinstellungen Ihres Systems, um zu bestimmen, welche Zeichen unverändert ausgegeben werden können und welche in den generischen, escaped `\u` oder `\U` Eingabeformen ausgegeben werden müssen. Neben diesen Unicode-Escape-Formen können auch alle von [C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes) verwendet werden:

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

Sie können Vergleiche und eine begrenzte Menge an Arithmetik mit `Char`-Werten durchführen:

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

Stringliterale sind durch doppelte Anführungszeichen oder dreifache doppelte Anführungszeichen (nicht durch einfache Anführungszeichen) begrenzt:

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

Lange Zeilen in Strings können durch ein vorangestelltes Zeilenumbruchzeichen mit einem Backslash (`\`) unterbrochen werden:

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

Wenn Sie ein Zeichen aus einer Zeichenkette extrahieren möchten, indexieren Sie darin:

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

Viele Julia-Objekte, einschließlich Strings, können mit Ganzzahlen indiziert werden. Der Index des ersten Elements (des ersten Zeichens eines Strings) wird durch [`firstindex(str)`](@ref) zurückgegeben, und der Index des letzten Elements (Zeichens) mit [`lastindex(str)`](@ref). Die Schlüsselwörter `begin` und `end` können innerhalb einer Indizierungsoperation als Kurzform für die ersten und letzten Indizes entlang der gegebenen Dimension verwendet werden. Die String-Indizierung, wie die meisten Indizierungen in Julia, ist 1-basiert: `firstindex` gibt immer `1` für jede `AbstractString` zurück. Wie wir unten sehen werden, ist jedoch `lastindex(str)` *nicht* im Allgemeinen dasselbe wie `length(str)` für einen String, da einige Unicode-Zeichen mehrere "Code-Einheiten" belegen können.

Sie können arithmetische und andere Operationen mit [`end`](@ref) durchführen, genau wie mit einem normalen Wert:

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

Die Verwendung eines Index, der kleiner als `begin` (`1`) oder größer als `end` ist, führt zu einem Fehler:

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

Sie können auch einen Teilstring mit Bereichsindizierung extrahieren:

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

Beachten Sie, dass die Ausdrücke `str[k]` und `str[k:k]` nicht das gleiche Ergebnis liefern:

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

Das erste ist ein einzelnes Zeichen vom Typ `Char`, während das letztere ein String-Wert ist, der zufällig nur ein einzelnes Zeichen enthält. In Julia sind dies sehr unterschiedliche Dinge.

Bereichsindizierung erstellt eine Kopie des ausgewählten Teils des ursprünglichen Strings. Alternativ ist es möglich, eine Ansicht in einen String zu erstellen, indem man den Typ [`SubString`](@ref) verwendet. Einfacher gesagt, konvertiert die Verwendung des [`@views`](@ref) Makros auf einem Codeblock alle String-Slices in Substrings. Zum Beispiel:

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

Mehrere Standardfunktionen wie [`chop`](@ref), [`chomp`](@ref) oder [`strip`](@ref) geben ein [`SubString`](@ref) zurück.

## Unicode and UTF-8

Julia unterstützt vollständig Unicode-Zeichen und -Strings. Als [discussed above](@ref man-characters) können Unicode-Codepunkte in Zeichenliteralen mit den Unicode-`\u`- und `\U`-Escape-Sequenzen sowie allen standardmäßigen C-Escape-Sequenzen dargestellt werden. Diese können ebenfalls verwendet werden, um Stringliterale zu schreiben:

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

Obwohl diese Unicode-Zeichen als Escape-Sequenzen oder als Sonderzeichen angezeigt werden, hängt dies von den Locale-Einstellungen Ihres Terminals und dessen Unterstützung für Unicode ab. Zeichenfolgenliterale werden mit der UTF-8-Codierung kodiert. UTF-8 ist eine variable Breite Codierung, was bedeutet, dass nicht alle Zeichen in der gleichen Anzahl von Bytes ("Codeeinheiten") kodiert sind. In UTF-8 werden ASCII-Zeichen – d.h. solche mit Codepunkten kleiner als 0x80 (128) – so kodiert, wie sie in ASCII sind, unter Verwendung eines einzelnen Bytes, während Codepunkte 0x80 und höher mit mehreren Bytes kodiert werden – bis zu vier pro Zeichen.

String-Indizes in Julia beziehen sich auf Codeeinheiten (= Bytes für UTF-8), die festen Bausteine, die verwendet werden, um beliebige Zeichen (Codepunkte) zu kodieren. Das bedeutet, dass nicht jeder Index in einem `String` notwendigerweise ein gültiger Index für ein Zeichen ist. Wenn Sie an einem solchen ungültigen Byte-Index in einen String indizieren, wird ein Fehler ausgelöst:

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

In diesem Fall ist das Zeichen `∀` ein Drei-Byte-Zeichen, sodass die Indizes 2 und 3 ungültig sind und der Index des nächsten Zeichens 4 ist; dieser nächste gültige Index kann durch [`nextind(s,1)`](@ref) berechnet werden, und der nächste Index danach durch `nextind(s,4)` und so weiter.

Da `end` immer der letzte gültige Index in einer Sammlung ist, verweist `end-1` auf einen ungültigen Byte-Index, wenn das vorletzte Zeichen mehrbyte ist.

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

Der erste Fall funktioniert, weil das letzte Zeichen `y` und das Leerzeichen einbyte-Zeichen sind, während `end-2` in die Mitte der multibyte Darstellung von `∃` indiziert. Der richtige Weg für diesen Fall ist die Verwendung von `prevind(s, lastindex(s), 2)` oder, wenn Sie diesen Wert verwenden, um in `s` zu indizieren, können Sie `s[prevind(s, end, 2)]` schreiben und `end` erweitert sich zu `lastindex(s)`.

Die Extraktion eines Teilstrings mit Bereichsindizes erwartet ebenfalls gültige Byte-Indizes, andernfalls wird ein Fehler ausgelöst:

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

Aufgrund von variablen Längen-Codierungen ist die Anzahl der Zeichen in einer Zeichenkette (angegeben durch [`length(s)`](@ref)) nicht immer gleich dem letzten Index. Wenn Sie durch die Indizes 1 bis [`lastindex(s)`](@ref) iterieren und in `s` indizieren, ist die Sequenz der zurückgegebenen Zeichen, wenn keine Fehler auftreten, die Sequenz der Zeichen, die die Zeichenkette `s` bilden. Daher gilt `length(s) <= lastindex(s)`, da jedes Zeichen in einer Zeichenkette seinen eigenen Index haben muss. Folgendes ist eine ineffiziente und ausführliche Möglichkeit, durch die Zeichen von `s` zu iterieren:

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

Die leeren Zeilen haben tatsächlich Leerzeichen. Glücklicherweise ist das oben genannte unbeholfene Idiom für das Durchlaufen der Zeichen in einem String nicht notwendig, da Sie einfach den String als iterierbares Objekt verwenden können, ohne dass eine Ausnahmebehandlung erforderlich ist:

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

Wenn Sie gültige Indizes für eine Zeichenkette erhalten müssen, können Sie die Funktionen [`nextind`](@ref) und [`prevind`](@ref) verwenden, um zum nächsten/vorherigen gültigen Index zu inkrementieren/dekrementieren, wie oben erwähnt. Sie können auch die Funktion [`eachindex`](@ref) verwenden, um über die gültigen Zeichenindizes zu iterieren:

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

Um auf die rohen Codeeinheiten (Bytes für UTF-8) der Kodierung zuzugreifen, können Sie die [`codeunit(s,i)`](@ref)-Funktion verwenden, wobei der Index `i` fortlaufend von `1` bis [`ncodeunits(s)`](@ref) läuft. Die [`codeunits(s)`](@ref)-Funktion gibt einen `AbstractVector{UInt8}`-Wrapper zurück, der es Ihnen ermöglicht, auf diese rohen Codeeinheiten (Bytes) als Array zuzugreifen.

Strings in Julia können ungültige UTF-8-Codeeinheitenfolgen enthalten. Diese Konvention ermöglicht es, jede Bytefolge als `String` zu behandeln. In solchen Situationen gilt die Regel, dass beim Parsen einer Folge von Codeeinheiten von links nach rechts Zeichen durch die längste Folge von 8-Bit-Codeeinheiten gebildet werden, die mit dem Anfang eines der folgenden Bitmuster übereinstimmt (jedes `x` kann `0` oder `1` sein):

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

Insbesondere bedeutet dies, dass zu lange und zu hohe Codeeinheitenfolgen und deren Präfixe als ein einzelnes ungültiges Zeichen und nicht als mehrere ungültige Zeichen behandelt werden. Diese Regel lässt sich am besten mit einem Beispiel erklären:

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

Wir können sehen, dass die ersten beiden Codeeinheiten im String `s` eine überlange Kodierung des Leerzeichens bilden. Sie ist ungültig, wird jedoch in einem String als ein einzelnes Zeichen akzeptiert. Die nächsten beiden Codeeinheiten bilden einen gültigen Anfang einer drei-Byte UTF-8-Sequenz. Allerdings ist die fünfte Codeeinheit `\xe2` keine gültige Fortsetzung. Daher werden die Codeeinheiten 3 und 4 ebenfalls als fehlerhafte Zeichen in diesem String interpretiert. Ebenso bildet die Codeeinheit 5 ein fehlerhaftes Zeichen, da `|` keine gültige Fortsetzung dafür ist. Schließlich enthält der String `s2` einen zu hohen Codepunkt.

Julia verwendet standardmäßig die UTF-8-Codierung, und die Unterstützung für neue Codierungen kann durch Pakete hinzugefügt werden. Zum Beispiel implementiert das [LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl)-Paket die Typen `UTF16String` und `UTF32String`. Eine zusätzliche Diskussion über andere Codierungen und wie man Unterstützung für sie implementiert, liegt derzeit nicht im Rahmen dieses Dokuments. Für weitere Diskussionen über Probleme mit der UTF-8-Codierung siehe den Abschnitt unten zu [byte array literals](@ref man-byte-array-literals). Die [`transcode`](@ref)-Funktion wird bereitgestellt, um Daten zwischen den verschiedenen UTF-xx-Codierungen zu konvertieren, hauptsächlich um mit externen Daten und Bibliotheken zu arbeiten.

## [Concatenation](@id man-concatenation)

Eine der häufigsten und nützlichsten Zeichenfolgenoperationen ist die Verkettung:

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

Es ist wichtig, sich potenziell gefährlicher Situationen bewusst zu sein, wie z. B. der Verkettung ungültiger UTF-8-Zeichenfolgen. Die resultierende Zeichenfolge kann andere Zeichen enthalten als die Eingabezeichenfolgen, und ihre Anzahl an Zeichen kann geringer sein als die Summe der Anzahl der Zeichen der verketteten Zeichenfolgen, z. B.:

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

Diese Situation kann nur bei ungültigen UTF-8-Zeichenfolgen auftreten. Bei gültigen UTF-8-Zeichenfolgen bewahrt die Verkettung alle Zeichen in den Zeichenfolgen und die Additivität der Zeichenfolgenlängen.

Julia bietet auch [`*`](@ref) für die Zeichenfolgenverkettung an:

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

Während `*` für Benutzer von Sprachen, die `+` für die Zeichenfolgenverkettung bereitstellen, überraschend erscheinen mag, hat diese Verwendung von `*` in der Mathematik, insbesondere in der abstrakten Algebra, eine Vorgeschichte.

In der Mathematik bezeichnet `+` normalerweise eine *kommutative* Operation, bei der die Reihenfolge der Operanden keine Rolle spielt. Ein Beispiel dafür ist die Matrizenaddition, bei der `A + B == B + A` für beliebige Matrizen `A` und `B` gilt, die die gleiche Form haben. Im Gegensatz dazu bezeichnet `*` typischerweise eine *nichtkommutative* Operation, bei der die Reihenfolge der Operanden *eine Rolle spielt*. Ein Beispiel dafür ist die Matrizenmultiplikation, bei der im Allgemeinen `A * B != B * A` gilt. Wie bei der Matrizenmultiplikation ist auch die Zeichenkettenverkettung nichtkommutativ: `greet * whom != whom * greet`. Daher ist `*` eine natürlichere Wahl für einen infix Zeichenkettenverkettungsoperator, die mit der gängigen mathematischen Verwendung übereinstimmt.

Genauer gesagt bildet die Menge aller endlichen Zeichenfolgen *S* zusammen mit dem Zeichenkettenverkettungsoperator `*` ein [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`). Das Identitätselement dieser Menge ist die leere Zeichenfolge, `""`. Wann immer ein freier Monoid nicht kommutativ ist, wird die Operation typischerweise als `\cdot`, `*` oder ein ähnliches Symbol dargestellt, anstatt `+`, was, wie gesagt, normalerweise Kommutativität impliziert.

## [Interpolation](@id string-interpolation)

Constructing strings using concatenation can become a bit cumbersome, however. To reduce the need for these verbose calls to [`string`](@ref) or repeated multiplications, Julia allows interpolation into string literals using `$`, as in Perl:

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

Dies ist leserlicher und bequemer und entspricht der obigen Zeichenfolgenverkettung – das System wandelt diesen scheinbar einzelnen Zeichenfolgenliteral in den Aufruf `string(greet, ", ", whom, ".\n")` um.

Der kürzeste vollständige Ausdruck nach dem `$` wird als der Ausdruck betrachtet, dessen Wert in den String interpoliert werden soll. So können Sie jeden Ausdruck in einen String interpolieren, indem Sie Klammern verwenden:

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

Sowohl die Verkettung als auch die Zeichenfolgeninterpolation rufen [`string`](@ref) auf, um Objekte in eine Zeichenfolgenform zu konvertieren. Allerdings gibt `string` tatsächlich nur die Ausgabe von [`print`](@ref) zurück, sodass neue Typen Methoden zu `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` oder [`show`](@ref) hinzufügen sollten, anstatt zu `string`.

Die meisten Nicht-`AbstractString`-Objekte werden in Strings umgewandelt, die eng dem entsprechen, wie sie als literale Ausdrücke eingegeben werden:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref) ist die Identität für `AbstractString` und `AbstractChar` Werte, sodass diese als sie selbst, unquoted und unescaped, in Strings interpoliert werden:

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

Um ein literales `$` in einem Zeichenfolgenliteral einzuschließen, entkommen Sie ihm mit einem Backslash:

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

Wenn Zeichenfolgen mit dreifachen Anführungszeichen (`"""..."""`) erstellt werden, haben sie ein spezielles Verhalten, das nützlich sein kann, um längere Textblöcke zu erstellen.

Zuerst werden auch dreifach zitierte Strings auf das Niveau der am wenigsten eingerückten Zeile zurückgeführt. Dies ist nützlich, um Strings innerhalb von eingerücktem Code zu definieren. Zum Beispiel:

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

In diesem Fall legt die letzte (leere) Zeile vor dem schließenden `"""` die Einrückungsebene fest.

Die Einrückungsebene wird als die längste gemeinsame Anfangssequenz von Leerzeichen oder Tabs in allen Zeilen bestimmt, wobei die Zeile, die auf das öffnende `"""` folgt, sowie Zeilen, die nur Leerzeichen oder Tabs enthalten, ausgeschlossen werden (die Zeile mit dem schließenden `"""` ist immer enthalten). Dann wird für alle Zeilen, mit Ausnahme des Textes, der auf das öffnende `"""` folgt, die gemeinsame Anfangssequenz entfernt (einschließlich Zeilen, die nur Leerzeichen und Tabs enthalten, wenn sie mit dieser Sequenz beginnen), z. B.:

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

Als Nächstes, wenn das öffnende `"""` von einer neuen Zeile gefolgt wird, wird die neue Zeile aus dem resultierenden String entfernt.

```julia
"""hello"""
```

entspricht

```julia
"""
hello"""
```

aber

```julia
"""

hello"""
```

wird einen wörtlichen Zeilenumbruch am Anfang enthalten.

Das Entfernen der Zeilenumbrüche erfolgt nach der Einrückungsreduzierung. Zum Beispiel:

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

Wenn die Zeilenumbruch mit einem Backslash entfernt wird, wird die Einrückung ebenfalls respektiert:

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

Trailing whitespace bleibt unverändert.

Dreifach-quoted String-Literale können `"`-Zeichen ohne Escape enthalten.

Beachten Sie, dass Zeilenumbrüche in literalen Zeichenfolgen, ob einfach oder dreifach zitiert, zu einem Zeilenumbruch (LF)-Zeichen `\n` in der Zeichenfolge führen, selbst wenn Ihr Editor ein Wagenrücklauf `\r` (CR) oder eine CRLF-Kombination zum Beenden von Zeilen verwendet. Um ein CR in einer Zeichenfolge einzuschließen, verwenden Sie eine explizite Escape-Sequenz `\r`; zum Beispiel können Sie die literale Zeichenfolge `"a CRLF line ending\r\n"` eingeben.

## Common Operations

Sie können Zeichenfolgen lexikografisch mit den Standardvergleichsoperatoren vergleichen:

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

Sie können den Index eines bestimmten Zeichens mit den Funktionen [`findfirst`](@ref) und [`findlast`](@ref) suchen:

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

Sie können die Suche nach einem Zeichen an einem bestimmten Offset starten, indem Sie die Funktionen [`findnext`](@ref) und [`findprev`](@ref) verwenden:

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

Sie können die [`occursin`](@ref)-Funktion verwenden, um zu überprüfen, ob ein Teilstring in einem String gefunden wird:

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

Das letzte Beispiel zeigt, dass [`occursin`](@ref) auch nach einem Zeichenliteral suchen kann.

Zwei weitere nützliche String-Funktionen sind [`repeat`](@ref) und [`join`](@ref):

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

Einige andere nützliche Funktionen sind:

  * [`firstindex(str)`](@ref) gibt den minimalen (Byte-)Index an, der verwendet werden kann, um in `str` zu indizieren (immer 1 für Strings, nicht unbedingt wahr für andere Container).
  * [`lastindex(str)`](@ref) gibt den maximalen (Byte-)Index an, der verwendet werden kann, um in `str` zu indizieren.
  * [`length(str)`](@ref) the number of characters in `str`.
  * [`length(str, i, j)`](@ref) die Anzahl der gültigen Zeichenindizes in `str` von `i` bis `j`.
  * [`ncodeunits(str)`](@ref) Anzahl von [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) in einem String.
  * [`codeunit(str, i)`](@ref) gibt den Codeeinheitswert im String `str` an der Stelle `i` zurück.
  * [`thisind(str, i)`](@ref) gegeben einen beliebigen Index in einen String, finde den ersten Index des Zeichens, auf das der Index zeigt.
  * [`nextind(str, i, n=1)`](@ref) finde den Start des `n`-ten Zeichens, das nach dem Index `i` beginnt.
  * [`prevind(str, i, n=1)`](@ref) finde den Start des `n`-ten Zeichens, das vor dem Index `i` beginnt.

## [Non-Standard String Literals](@id non-standard-string-literals)

Es gibt Situationen, in denen Sie einen String konstruieren oder String-Semantiken verwenden möchten, aber das Verhalten des Standard-String-Konstrukts nicht ganz dem entspricht, was benötigt wird. Für diese Arten von Situationen bietet Julia nicht-standardmäßige String-Literale an. Ein nicht-standardmäßiges String-Literal sieht aus wie ein reguläres, doppelt zitiertes String-Literal, wird jedoch sofort von einem Bezeichner vorangestellt und kann sich anders verhalten als ein normales String-Literal.

[Regular expressions](@ref man-regex-literals), [byte array literals](@ref man-byte-array-literals), und [version number literals](@ref man-version-number-literals), wie unten beschrieben, sind einige Beispiele für nicht-standardisierte String-Literale. Benutzer und Pakete können auch neue nicht-standardisierte String-Literale definieren. Weitere Dokumentation ist im Abschnitt [Metaprogramming](@ref meta-non-standard-string-literals) zu finden.

## [Regular Expressions](@id man-regex-literals)

Manchmal suchen Sie nicht nach einer genauen Zeichenfolge, sondern nach einem bestimmten *Muster*. Zum Beispiel, nehmen wir an, Sie versuchen, ein einzelnes Datum aus einer großen Textdatei zu extrahieren. Sie wissen nicht, welches Datum das ist (deshalb suchen Sie danach), aber Sie wissen, dass es ungefähr so aussehen wird: `YYYY-MM-DD`. Reguläre Ausdrücke ermöglichen es Ihnen, diese Muster anzugeben und danach zu suchen.

Julia verwendet Version 2 von Perl-kompatiblen regulären Ausdrücken (Regex), wie sie von der [PCRE](https://www.pcre.org/)-Bibliothek bereitgestellt werden (siehe die [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html) für weitere Details). Reguläre Ausdrücke stehen in zwei Weisen im Zusammenhang mit Zeichenfolgen: Die offensichtliche Verbindung besteht darin, dass reguläre Ausdrücke verwendet werden, um reguläre Muster in Zeichenfolgen zu finden; die andere Verbindung besteht darin, dass reguläre Ausdrücke selbst als Zeichenfolgen eingegeben werden, die in eine Zustandsmaschine geparst werden, die verwendet werden kann, um effizient nach Mustern in Zeichenfolgen zu suchen. In Julia werden reguläre Ausdrücke mit nicht standardmäßigen Zeichenfolgenliteralen eingegeben, die mit verschiedenen Bezeichnern beginnen, die mit `r` beginnen. Das grundlegendste reguläre Ausdrucksliteral ohne aktivierte Optionen verwendet einfach `r"..."`:

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

Um zu überprüfen, ob ein Regex mit einem String übereinstimmt, verwenden Sie [`occursin`](@ref):

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

Wie man hier sehen kann, [`occursin`](@ref) gibt einfach true oder false zurück, was angibt, ob ein Treffer für den gegebenen Regex im String auftritt. Häufig möchte man jedoch nicht nur wissen, ob ein String übereinstimmt, sondern auch *wie* er übereinstimmt. Um diese Informationen über einen Treffer zu erfassen, verwenden Sie stattdessen die [`match`](@ref) Funktion:

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

Wenn der reguläre Ausdruck mit dem gegebenen String nicht übereinstimmt, gibt [`match`](@ref) den Wert [`nothing`](@ref) zurück – ein spezieller Wert, der im interaktiven Prompt nichts ausgibt. Abgesehen davon, dass er nichts ausgibt, ist es ein völlig normaler Wert, und Sie können programmgesteuert darauf testen:

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

Wenn ein regulärer Ausdruck übereinstimmt, ist der zurückgegebene Wert von [`match`](@ref) ein [`RegexMatch`](@ref) Objekt. Diese Objekte zeichnen auf, wie der Ausdruck übereinstimmt, einschließlich des Teilstrings, der mit dem Muster übereinstimmt, und aller erfassten Teilstrings, falls vorhanden. Dieses Beispiel erfasst nur den Teil des Teilstrings, der übereinstimmt, aber vielleicht möchten wir jeden nicht-leeren Text nach dem Kommentarzeichen erfassen. Wir könnten Folgendes tun:

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

Beim Aufruf von [`match`](@ref) haben Sie die Möglichkeit, einen Index anzugeben, an dem die Suche beginnen soll. Zum Beispiel:

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

Sie können die folgenden Informationen aus einem `RegexMatch`-Objekt extrahieren:

  * der gesamte übereinstimmende Teilstring: `m.match`
  * die erfassten Teilstrings als ein Array von Strings: `m.captures`
  * der Offset, an dem das gesamte Match beginnt: `m.offset`
  * die Offsets der erfassten Teilstrings als Vektor: `m.offsets`

Für den Fall, dass eine Erfassung nicht übereinstimmt, enthält `m.captures` an dieser Stelle `nothing` und `m.offsets` hat einen Offset von null (denken Sie daran, dass Indizes in Julia 1-basiert sind, sodass ein Offset von null in einen String ungültig ist). Hier ist ein Paar von etwas konstruierten Beispielen:

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

Es ist praktisch, die Erfassungen als Array zurückzugeben, damit man die Destrukturierungssyntax verwenden kann, um sie an lokale Variablen zu binden. Zur Vereinfachung implementiert das `RegexMatch`-Objekt Iterator-Methoden, die an das `captures`-Feld weitergeleitet werden, sodass man das Match-Objekt direkt destrukturieren kann:

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

Erfassungen können auch durch Indizierung des `RegexMatch`-Objekts mit der Nummer oder dem Namen der Erfassungsgruppe zugegriffen werden:

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

Erfassungen können in einem Ersetzungsstring referenziert werden, wenn [`replace`](@ref) verwendet wird, indem `\n` verwendet wird, um auf die n-te Erfassungsgruppe zu verweisen, und der Ersetzungsstring mit `s` vorangestellt wird. Die Erfassungsgruppe 0 bezieht sich auf das gesamte Übereinstimmungsobjekt. Benannte Erfassungsgruppen können in der Ersetzung mit `\g<gruppenname>` referenziert werden. Zum Beispiel:

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

Nummerierte Erfassungsgruppen können auch als `\g<n>` zur Entambiguierung referenziert werden, wie in:

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

Sie können das Verhalten von regulären Ausdrücken durch eine Kombination der Flags `i`, `m`, `s` und `x` nach dem schließenden Anführungszeichen ändern. Diese Flags haben die gleiche Bedeutung wie in Perl, wie in diesem Auszug aus der [perlre manpage](https://perldoc.perl.org/perlre#Modifiers) erklärt.

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

Zum Beispiel hat der folgende Regex alle drei Flags aktiviert:

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Der `r"..."` Literal wird ohne Interpolation und Unescaping (außer für das Anführungszeichen `"` , das weiterhin escaped werden muss) erstellt. Hier ist ein Beispiel, das den Unterschied zu standardmäßigen String-Literalen zeigt:

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

Dreifach-quoted Regex-Strings der Form `r"""..."""` werden ebenfalls unterstützt (und können praktisch sein für reguläre Ausdrücke, die Anführungszeichen oder Zeilenumbrüche enthalten).

Der `Regex()`-Konstruktor kann verwendet werden, um programmgesteuert einen gültigen Regex-String zu erstellen. Dies ermöglicht die Verwendung des Inhalts von String-Variablen und anderen String-Operationen beim Erstellen des Regex-Strings. Jeder der oben genannten Regex-Codes kann innerhalb des einzelnen String-Arguments von `Regex()` verwendet werden. Hier sind einige Beispiele:

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

Beachten Sie die Verwendung der Escape-Sequenz `\Q...\E`. Alle Zeichen zwischen `\Q` und `\E` werden als Literalzeichen interpretiert. Dies ist praktisch, um Zeichen zu matchen, die andernfalls Regex-Metazeichen wären. Vorsicht ist jedoch geboten, wenn Sie diese Funktion zusammen mit der String-Interpolation verwenden, da der interpolierte String möglicherweise selbst die Sequenz `\E` enthält, was das literale Matching unerwartet beendet. Benutzereingaben müssen vor der Einbeziehung in ein Regex bereinigt werden.

## [Byte Array Literals](@id man-byte-array-literals)

Ein weiterer nützlicher nicht-standardmäßiger String-Literal ist der Byte-Array-String-Literal: `b"..."`. Diese Form ermöglicht es Ihnen, die String-Notation zu verwenden, um schreibgeschützte literale Byte-Arrays auszudrücken – d.h. Arrays von [`UInt8`](@ref) Werten. Der Typ dieser Objekte ist `CodeUnits{UInt8, String}`. Die Regeln für Byte-Array-Literale sind die folgenden:

  * ASCII-Zeichen und ASCII-Escape-Sequenzen erzeugen ein einzelnes Byte.
  * `\x` und oktale Escape-Sequenzen erzeugen das *Byte*, das dem Escape-Wert entspricht.
  * Unicode-Escape-Sequenzen erzeugen eine Bytefolge, die diesen Codepunkt in UTF-8 kodiert.

Es gibt einige Überschneidungen zwischen diesen Regeln, da das Verhalten von `\x` und oktalen Escape-Sequenzen unter 0x80 (128) von beiden der ersten beiden Regeln abgedeckt wird, aber hier stimmen diese Regeln überein. Zusammen ermöglichen diese Regeln, dass man leicht ASCII-Zeichen, beliebige Byte-Werte und UTF-8-Sequenzen verwenden kann, um Byte-Arrays zu erzeugen. Hier ist ein Beispiel, das alle drei verwendet:

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

Der ASCII-String "DATA" entspricht den Bytes 68, 65, 84, 65. `\xff` erzeugt das einzelne Byte 255. Der Unicode-Escape `\u2200` wird in UTF-8 als die drei Bytes 226, 136, 128 kodiert. Beachten Sie, dass das resultierende Byte-Array nicht mit einem gültigen UTF-8-String übereinstimmt:

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

Wie bereits erwähnt, verhält sich der Typ `CodeUnits{UInt8, String}` wie ein schreibgeschütztes Array von `UInt8`, und wenn Sie einen Standardvektor benötigen, können Sie ihn mit `Vector{UInt8}` konvertieren:

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

Beachten Sie auch den wesentlichen Unterschied zwischen `\xff` und `\uff`: Die erste Escape-Sequenz kodiert das *Byte 255*, während die letzte Escape-Sequenz den *Codepunkt 255* darstellt, der in UTF-8 als zwei Bytes kodiert ist:

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

Zeichenliterale verwenden dasselbe Verhalten.

Für Codepunkte kleiner als `\u80` ist es so, dass die UTF-8-Codierung jedes Codepunkts einfach das einzelne Byte ist, das durch den entsprechenden `\x`-Escape erzeugt wird, sodass die Unterscheidung sicher ignoriert werden kann. Bei den Escapes `\x80` bis `\xff` im Vergleich zu `\u80` bis `\uff` gibt es jedoch einen wesentlichen Unterschied: Die ersteren Escapes codieren alle einzelne Bytes, die – es sei denn, sie werden von sehr spezifischen Fortsetzungsbytes gefolgt – keine gültigen UTF-8-Daten bilden, während die letzteren Escapes alle Unicode-Codepunkte mit zweibyte-Codierungen darstellen.

Wenn dies alles extrem verwirrend ist, versuchen Sie, ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/) zu lesen. Es ist eine hervorragende Einführung in Unicode und UTF-8 und kann helfen, einige Verwirrungen in Bezug auf das Thema zu beseitigen.

## [Version Number Literals](@id man-version-number-literals)

Versionsnummern können leicht mit nicht standardmäßigen String-Literalen der Form [`v"..."`](@ref @v_str) ausgedrückt werden. Versionsnummern-Literale erstellen [`VersionNumber`](@ref) Objekte, die den Spezifikationen von [semantic versioning](https://semver.org/) folgen und daher aus Haupt-, Neben- und Patch-Zahlenwerten bestehen, gefolgt von Vorab- und Build-alphanumerischen Anmerkungen. Zum Beispiel wird `v"0.2.1-rc1+win64"` in die Hauptversion `0`, die Nebenversion `2`, die Patchversion `1`, die Vorabversion `rc1` und den Build `win64` unterteilt. Bei der Eingabe eines Versionsliterals ist alles außer der Hauptversionsnummer optional, daher ist z.B. `v"0.2"` gleichwertig mit `v"0.2.0"` (mit leeren Vorab-/Build-Anmerkungen), `v"2"` ist gleichwertig mit `v"2.0.0"` und so weiter.

`VersionNumber`-Objekte sind hauptsächlich nützlich, um zwei (oder mehr) Versionen einfach und korrekt zu vergleichen. Zum Beispiel hält die Konstante [`VERSION`](@ref) die Julia-Version als ein `VersionNumber`-Objekt, und daher kann man einige versionsspezifische Verhaltensweisen mit einfachen Anweisungen definieren, wie:

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

Beachten Sie, dass im obigen Beispiel die nicht standardmäßige Versionsnummer `v"0.3-"` verwendet wird, mit einem nachgestellten `-`: Diese Notation ist eine Erweiterung von Julia des Standards und wird verwendet, um eine Version anzuzeigen, die niedriger ist als jede `0.3`-Version, einschließlich aller ihrer Vorabversionen. Im obigen Beispiel würde der Code also nur mit stabilen `0.2`-Versionen ausgeführt werden und solche Versionen wie `v"0.3.0-rc1"` ausschließen. Um auch instabile (d.h. Vorabversionen) `0.2`-Versionen zuzulassen, sollte die untere Grenzkontrolle wie folgt geändert werden: `v"0.2-" <= VERSION`.

Eine weitere nicht standardisierte Versionsspezifikationserweiterung ermöglicht es, ein abschließendes `+` zu verwenden, um eine obere Grenze für Build-Versionen auszudrücken, z. B. kann `VERSION > v"0.2-rc1+"` verwendet werden, um jede Version über `0.2-rc1` und jede ihrer Builds zu bedeuten: Es wird `false` für die Version `v"0.2-rc1+win64"` und `true` für `v"0.2-rc2"` zurückgeben.

Es ist gute Praxis, solche speziellen Versionen in Vergleichen zu verwenden (insbesondere sollte der abschließende `-` immer bei oberen Grenzen verwendet werden, es sei denn, es gibt einen guten Grund, dies nicht zu tun), aber sie dürfen nicht als die tatsächliche Versionsnummer von irgendetwas verwendet werden, da sie im semantischen Versionsschema ungültig sind.

Neben der Verwendung für die [`VERSION`](@ref) Konstante werden `VersionNumber`-Objekte im `Pkg`-Modul häufig verwendet, um die Versionen von Paketen und deren Abhängigkeiten anzugeben.

## [Raw String Literals](@id man-raw-string-literals)

Rohzeichenfolgen ohne Interpolation oder Unescaping können mit nicht standardmäßigen Zeichenfolgenliteralen der Form `raw"..."` ausgedrückt werden. Rohzeichenfolgenliterale erstellen gewöhnliche `String`-Objekte, die den enthaltenen Inhalt genau so enthalten, wie er eingegeben wurde, ohne Interpolation oder Unescaping. Dies ist nützlich für Zeichenfolgen, die Code oder Markup in anderen Sprachen enthalten, die `$` oder `\` als Sonderzeichen verwenden.

Die Ausnahme ist, dass Anführungszeichen weiterhin escaped werden müssen, z.B. `raw"\""` ist gleichbedeutend mit `"\""`. Um es möglich zu machen, alle Zeichenfolgen auszudrücken, müssen auch Rückwärtsschläge escaped werden, aber nur wenn sie direkt vor einem Anführungszeichen erscheinen:

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

Beachten Sie, dass die ersten beiden Backslashes unverändert im Output erscheinen, da sie nicht vor einem Anführungszeichen stehen. Der nächste Backslash hingegen entwertet den folgenden Backslash, und der letzte Backslash entwertet ein Anführungszeichen, da diese Backslashes vor einem Anführungszeichen stehen.

## [Annotated Strings](@id man-annotated-strings)

!!! note
    Die API für AnnotatedStrings wird als experimentell betrachtet und kann sich zwischen den Julia-Versionen ändern.


Es ist manchmal nützlich, Metadaten zu Regionen eines Strings zu halten. Ein [`AnnotatedString`](@ref Base.AnnotatedString) umschließt einen anderen String und ermöglicht es, Regionen davon mit beschrifteten Werten (`:label => value`) zu annotieren. Alle generischen String-Operationen werden auf den zugrunde liegenden String angewendet. Wenn möglich, werden jedoch Styling-Informationen beibehalten. Das bedeutet, dass Sie einen `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` manipulieren können — indem Sie Teilstrings entnehmen, sie auffüllen, sie mit anderen Strings verketten — und die Metadatenannotationen werden "mitkommen".

Dieser Stringtyp ist grundlegend für die [StyledStrings stdlib](@ref stdlib-styledstrings), die `:face`-beschriftete Annotationen verwendet, um Stilinformationen zu halten.

When concatenating a [`AnnotatedString`](@ref Base.AnnotatedString), take care to use [`annotatedstring`](@ref Base.annotatedstring) instead of [`string`](@ref) if you want to keep the string annotations.

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

Die Anmerkungen eines [`AnnotatedString`](@ref Base.AnnotatedString) können über die [`annotations`](@ref Base.annotations) und [`annotate!`](@ref Base.annotate!) Funktionen zugegriffen und geändert werden.

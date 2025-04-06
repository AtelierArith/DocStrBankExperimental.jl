# [Conversion and Promotion](@id conversion-and-promotion)

Julia hat ein System zur Förderung von Argumenten mathematischer Operatoren auf einen gemeinsamen Typ, das in verschiedenen anderen Abschnitten erwähnt wurde, einschließlich [Integers and Floating-Point Numbers](@ref), [Mathematical Operations and Elementary Functions](@ref), [Types](@ref man-types) und [Methods](@ref). In diesem Abschnitt erklären wir, wie dieses Fördersystem funktioniert, sowie wie man es auf neue Typen erweitern und auf Funktionen anwenden kann, die über eingebaute mathematische Operatoren hinausgehen. Traditionell fallen Programmiersprachen in zwei Lager in Bezug auf die Förderung arithmetischer Argumente:

  * **Automatische Promotion für integrierte arithmetische Typen und Operatoren.** In den meisten Sprachen werden integrierte numerische Typen, wenn sie als Operanden für arithmetische Operatoren mit Infix-Syntax wie `+`, `-`, `*` und `/` verwendet werden, automatisch auf einen gemeinsamen Typ befördert, um die erwarteten Ergebnisse zu erzielen. C, Java, Perl und Python, um nur einige zu nennen, berechnen korrekt die Summe `1 + 1.5` als den Gleitkommawert `2.5`, obwohl einer der Operanden von `+` eine Ganzzahl ist. Diese Systeme sind praktisch und so sorgfältig gestaltet, dass sie für den Programmierer im Allgemeinen nahezu unsichtbar sind: Kaum jemand denkt bewusst an diese Promotion, wenn er einen solchen Ausdruck schreibt, aber Compiler und Interpreter müssen eine Umwandlung vor der Addition durchführen, da Ganzzahlen und Gleitkommawerte nicht so addiert werden können. Komplexe Regeln für solche automatischen Umwandlungen sind daher unvermeidlich Teil der Spezifikationen und Implementierungen für solche Sprachen.
  * **Keine automatische Promotion.** Dieses Camp umfasst Ada und ML – sehr "strenge" statisch typisierte Sprachen. In diesen Sprachen muss jede Umwandlung vom Programmierer ausdrücklich angegeben werden. Daher würde der Beispielausdruck `1 + 1.5` in sowohl Ada als auch ML einen Kompilierungsfehler verursachen. Stattdessen muss man `real(1) + 1.5` schreiben, um die Ganzzahl `1` ausdrücklich in einen Gleitkommawert umzuwandeln, bevor die Addition durchgeführt wird. Die explizite Umwandlung überall ist jedoch so unpraktisch, dass selbst Ada einen gewissen Grad an automatischer Umwandlung hat: Ganzzahl-Literale werden automatisch in den erwarteten Ganzzahltyp befördert, und Gleitkomma-Literale werden ähnlich in die entsprechenden Gleitkomma-Typen befördert.

In gewissem Sinne fällt Julia in die Kategorie "keine automatische Promotion": Mathematische Operatoren sind einfach Funktionen mit spezieller Syntax, und die Argumente von Funktionen werden niemals automatisch konvertiert. Man kann jedoch beobachten, dass die Anwendung mathematischer Operationen auf eine Vielzahl gemischter Argumenttypen nur einen extremen Fall von polymorphem Mehrfach-Dispatch darstellt – etwas, wofür Julias Dispatch- und Typsysteme besonders gut geeignet sind. Die "automatische" Promotion mathematischer Operanden ergibt sich einfach als eine spezielle Anwendung: Julia kommt mit vordefinierten Auffang-Dispatch-Regeln für mathematische Operatoren, die aufgerufen werden, wenn keine spezifische Implementierung für eine bestimmte Kombination von Operanden-Typen existiert. Diese Auffangregeln befördern zunächst alle Operanden zu einem gemeinsamen Typ unter Verwendung benutzerdefinierbarer Promotionsregeln und rufen dann eine spezialisierte Implementierung des betreffenden Operators für die resultierenden Werte auf, die nun vom gleichen Typ sind. Benutzerdefinierte Typen können leicht an diesem Promotionssystem teilnehmen, indem sie Methoden zur Konvertierung zu und von anderen Typen definieren und eine Handvoll Promotionsregeln bereitstellen, die definieren, zu welchen Typen sie befördert werden sollen, wenn sie mit anderen Typen gemischt werden.

## Conversion

Der Standardweg, um einen Wert eines bestimmten Typs `T` zu erhalten, besteht darin, den Konstruktor des Typs aufzurufen, `T(x)`. Es gibt jedoch Fälle, in denen es praktisch ist, einen Wert von einem Typ in einen anderen zu konvertieren, ohne dass der Programmierer dies ausdrücklich anfordert. Ein Beispiel ist die Zuweisung eines Wertes in ein Array: Wenn `A` ein `Vector{Float64}` ist, sollte der Ausdruck `A[1] = 2` funktionieren, indem er automatisch die `2` von `Int` in `Float64` konvertiert und das Ergebnis im Array speichert. Dies geschieht über die [`convert`](@ref)-Funktion.

Die `convert`-Funktion nimmt im Allgemeinen zwei Argumente: Das erste ist ein Typobjekt und das zweite ist ein Wert, der in diesen Typ konvertiert werden soll. Der zurückgegebene Wert ist der in eine Instanz des angegebenen Typs konvertierte Wert. Der einfachste Weg, diese Funktion zu verstehen, besteht darin, sie in Aktion zu sehen:

```jldoctest
julia> x = 12
12

julia> typeof(x)
Int64

julia> xu = convert(UInt8, x)
0x0c

julia> typeof(xu)
UInt8

julia> xf = convert(AbstractFloat, x)
12.0

julia> typeof(xf)
Float64

julia> a = Any[1 2 3; 4 5 6]
2×3 Matrix{Any}:
 1  2  3
 4  5  6

julia> convert(Array{Float64}, a)
2×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
```

Die Konvertierung ist nicht immer möglich, in diesem Fall wird ein [`MethodError`](@ref) ausgegeben, das anzeigt, dass `convert` nicht weiß, wie die angeforderte Konvertierung durchgeführt werden kann:

```jldoctest
julia> convert(AbstractFloat, "foo")
ERROR: MethodError: Cannot `convert` an object of type String to an object of type AbstractFloat
[...]
```

Einige Sprachen betrachten das Parsen von Zeichenfolgen als Zahlen oder das Formatieren von Zahlen als Zeichenfolgen als Konvertierungen (viele dynamische Sprachen führen die Konvertierung sogar automatisch für Sie durch). Dies ist in Julia nicht der Fall. Obwohl einige Zeichenfolgen als Zahlen geparst werden können, sind die meisten Zeichenfolgen keine gültigen Darstellungen von Zahlen, und nur eine sehr begrenzte Teilmenge von ihnen ist es. Daher muss in Julia die spezielle [`parse`](@ref) Funktion verwendet werden, um diese Operation durchzuführen, was sie expliziter macht.

### When is `convert` called?

Die folgenden Sprachkonstrukte rufen `convert` auf:

  * Die Zuweisung an ein Array konvertiert in den Elementtyp des Arrays.
  * Die Zuweisung zu einem Feld eines Objekts wird in den deklarierten Typ des Feldes umgewandelt.
  * Das Erstellen eines Objekts mit [`new`](@ref) konvertiert in die deklarierten Feldtypen des Objekts.
  * Die Zuweisung an eine Variable mit einem deklarierten Typ (z. B. `local x::T`) konvertiert in diesen Typ.
  * Eine Funktion mit einem deklarierten Rückgabewerttyp konvertiert ihren Rückgabewert in diesen Typ.
  * Das Übergeben eines Wertes an [`ccall`](@ref) konvertiert ihn in den entsprechenden Argumenttyp.

### Conversion vs. Construction

Beachten Sie, dass das Verhalten von `convert(T, x)` nahezu identisch mit `T(x)` zu sein scheint. Tatsächlich ist es das normalerweise auch. Es gibt jedoch einen entscheidenden semantischen Unterschied: Da `convert` implizit aufgerufen werden kann, sind seine Methoden auf Fälle beschränkt, die als "sicher" oder "nicht überraschend" gelten. `convert` wird nur zwischen Typen konvertieren, die dasselbe grundlegende Konzept darstellen (z. B. unterschiedliche Darstellungen von Zahlen oder unterschiedliche Zeichenkodierungen). Es ist auch normalerweise verlustfrei; das Konvertieren eines Wertes in einen anderen Typ und zurück sollte den exakt gleichen Wert ergeben.

Es gibt vier allgemeine Arten von Fällen, in denen sich Konstruktoren von `convert` unterscheiden:

#### Constructors for types unrelated to their arguments

Einige Konstruktoren implementieren nicht das Konzept der "Konversion". Zum Beispiel erstellt `Timer(2)` einen 2-Sekunden-Timer, was nicht wirklich eine "Konversion" von einer Ganzzahl zu einem Timer ist.

#### Mutable collections

`convert(T, x)` wird erwartet, dass es das ursprüngliche `x` zurückgibt, wenn `x` bereits vom Typ `T` ist. Im Gegensatz dazu sollte `T(x)` immer eine neue Sammlung erstellen (Elemente von `x` kopieren), wenn `T` ein veränderbarer Sammlungstyp ist.

#### Wrapper types

Für einige Typen, die andere Werte "einwickeln", kann der Konstruktor sein Argument in ein neues Objekt einwickeln, selbst wenn es bereits vom angeforderten Typ ist. Zum Beispiel wickelt `Some(x)` `x` ein, um anzuzeigen, dass ein Wert vorhanden ist (in einem Kontext, in dem das Ergebnis entweder `Some` oder `nothing` sein könnte). `x` selbst könnte jedoch das Objekt `Some(y)` sein, in diesem Fall ist das Ergebnis `Some(Some(y))`, mit zwei Ebenen der Einwicklung. `convert(Some, x)` würde hingegen einfach `x` zurückgeben, da es bereits ein `Some` ist.

#### Constructors that don't return instances of their own type

In *sehr seltenen* Fällen kann es sinnvoll sein, dass der Konstruktor `T(x)` ein Objekt zurückgibt, das nicht vom Typ `T` ist. Dies könnte passieren, wenn ein Wrapper-Typ sein eigener Inverser ist (z. B. `Flip(Flip(x)) === x`), oder um eine alte Aufrufsyntax für die Rückwärtskompatibilität zu unterstützen, wenn eine Bibliothek umstrukturiert wird. Aber `convert(T, x)` sollte immer einen Wert vom Typ `T` zurückgeben.

### Defining New Conversions

Beim Definieren eines neuen Typs sollten zunächst alle Möglichkeiten zu seiner Erstellung als Konstruktoren definiert werden. Wenn sich herausstellt, dass eine implizite Konvertierung nützlich wäre und einige Konstruktoren die oben genannten "Sicherheits"-Kriterien erfüllen, können `convert`-Methoden hinzugefügt werden. Diese Methoden sind typischerweise recht einfach, da sie nur den entsprechenden Konstruktor aufrufen müssen. Eine solche Definition könnte folgendermaßen aussehen:

```julia
import Base: convert
convert(::Type{MyType}, x) = MyType(x)
```

Der Typ des ersten Arguments dieser Methode ist [`Type{MyType}`](@ref man-typet-type), dessen einzige Instanz `MyType` ist. Daher wird diese Methode nur aufgerufen, wenn das erste Argument der Typwert `MyType` ist. Beachten Sie die Syntax, die für das erste Argument verwendet wird: der Argumentname wird vor dem `::`-Symbol weggelassen, und nur der Typ wird angegeben. Dies ist die Syntax in Julia für ein Funktionsargument, dessen Typ angegeben ist, dessen Wert jedoch nicht namentlich referenziert werden muss.

Alle Instanzen einiger abstrakter Typen werden standardmäßig als "ausreichend ähnlich" betrachtet, sodass eine universelle `convert`-Definition in Julia Base bereitgestellt wird. Zum Beispiel besagt diese Definition, dass es gültig ist, jeden `Number`-Typ in einen anderen zu `convert`, indem ein Konstruktor mit einem Argument aufgerufen wird:

```julia
convert(::Type{T}, x::Number) where {T<:Number} = T(x)::T
```

Das bedeutet, dass neue `Number`-Typen nur Konstruktoren definieren müssen, da diese Definition `convert` für sie übernimmt. Eine Identitätskonvertierung wird ebenfalls bereitgestellt, um den Fall zu behandeln, in dem das Argument bereits vom angeforderten Typ ist:

```julia
convert(::Type{T}, x::T) where {T<:Number} = x
```

Ähnliche Definitionen existieren für `AbstractString`, [`AbstractArray`](@ref) und [`AbstractDict`](@ref).

## Promotion

Promotion bezieht sich auf die Umwandlung von Werten gemischter Typen in einen einzigen gemeinsamen Typ. Obwohl es nicht unbedingt notwendig ist, wird allgemein impliziert, dass der gemeinsame Typ, in den die Werte umgewandelt werden, alle ursprünglichen Werte treu darstellen kann. In diesem Sinne ist der Begriff "Promotion" angemessen, da die Werte in einen "größeren" Typ umgewandelt werden – d.h. einen, der alle Eingabewerte in einem einzigen gemeinsamen Typ darstellen kann. Es ist jedoch wichtig, dies nicht mit der objektorientierten (strukturellen) Super-Typisierung oder Julias Vorstellung von abstrakten Super-Typen zu verwechseln: Promotion hat nichts mit der Typ-Hierarchie zu tun und alles mit der Umwandlung zwischen alternativen Darstellungen. Zum Beispiel kann jeder [`Int32`](@ref) Wert auch als [`Float64`](@ref) Wert dargestellt werden, aber `Int32` ist kein Subtyp von `Float64`.

Die Promotion zu einem gemeinsamen "größeren" Typ wird in Julia durch die [`promote`](@ref)-Funktion durchgeführt, die eine beliebige Anzahl von Argumenten annimmt und ein Tupel der gleichen Anzahl von Werten zurückgibt, die in einen gemeinsamen Typ konvertiert wurden, oder eine Ausnahme auslöst, wenn die Promotion nicht möglich ist. Der häufigste Anwendungsfall für die Promotion besteht darin, numerische Argumente in einen gemeinsamen Typ zu konvertieren:

```jldoctest
julia> promote(1, 2.5)
(1.0, 2.5)

julia> promote(1, 2.5, 3)
(1.0, 2.5, 3.0)

julia> promote(2, 3//4)
(2//1, 3//4)

julia> promote(1, 2.5, 3, 3//4)
(1.0, 2.5, 3.0, 0.75)

julia> promote(1.5, im)
(1.5 + 0.0im, 0.0 + 1.0im)

julia> promote(1 + 2im, 3//4)
(1//1 + 2//1*im, 3//4 + 0//1*im)
```

Gleitkommawerte werden auf den größten der Gleitkomma-Argumenttypen befördert. Ganzzahlwerte werden auf den größten der Ganzzahl-Argumenttypen befördert. Wenn die Typen die gleiche Größe haben, sich aber in der Vorzeichenbehandlung unterscheiden, wird der unsigned Typ gewählt. Mischungen aus Ganzzahlen und Gleitkommawerten werden auf einen Gleitkommatyp befördert, der groß genug ist, um alle Werte zu halten. Ganzzahlen, die mit rationalen Zahlen gemischt werden, werden auf rationale Zahlen befördert. Rationale Zahlen, die mit Gleitkommawerten gemischt werden, werden auf Gleitkommawerte befördert. Komplexe Werte, die mit reellen Werten gemischt werden, werden auf die entsprechende Art von komplexen Werten befördert.

Das ist wirklich alles, was es über die Verwendung von Promotionen zu sagen gibt. Der Rest ist nur eine Frage der cleveren Anwendung, wobei die typischste "clevere" Anwendung die Definition von universellen Methoden für numerische Operationen wie die arithmetischen Operatoren `+`, `-`, `*` und `/` ist. Hier sind einige der universellen Methodendefinitionen, die in [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) gegeben sind:

```julia
+(x::Number, y::Number) = +(promote(x,y)...)
-(x::Number, y::Number) = -(promote(x,y)...)
*(x::Number, y::Number) = *(promote(x,y)...)
/(x::Number, y::Number) = /(promote(x,y)...)
```

Diese Methodendefinitionen besagen, dass in Abwesenheit spezifischerer Regeln für das Hinzufügen, Subtrahieren, Multiplizieren und Dividieren von Paaren numerischer Werte die Werte auf einen gemeinsamen Typ befördert werden und dann erneut versucht wird. Das ist alles: nirgendwo sonst muss man sich um die Beförderung zu einem gemeinsamen numerischen Typ für arithmetische Operationen kümmern – es geschieht einfach automatisch. Es gibt Definitionen von allgemeinen Beförderungsmethoden für eine Reihe anderer arithmetischer und mathematischer Funktionen in [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), aber darüber hinaus gibt es kaum Aufrufe von `promote`, die in Julia Base erforderlich sind. Die häufigsten Verwendungen von `promote` treten in äußeren Konstruktor-Methoden auf, die zur Bequemlichkeit bereitgestellt werden, um Konstruktoraufrufe mit gemischten Typen zu ermöglichen, die an einen inneren Typ delegieren, dessen Felder auf einen geeigneten gemeinsamen Typ befördert werden. Zum Beispiel erinnert man sich, dass [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) die folgende äußere Konstruktor-Methode bereitstellt:

```julia
Rational(n::Integer, d::Integer) = Rational(promote(n,d)...)
```

Dies ermöglicht, dass Aufrufe wie die folgenden funktionieren:

```jldoctest
julia> x = Rational(Int8(15),Int32(-5))
-3//1

julia> typeof(x)
Rational{Int32}
```

Für die meisten benutzerdefinierten Typen ist es besser, Programmierer dazu zu bringen, die erwarteten Typen für Konstruktorfunktionen ausdrücklich anzugeben. Manchmal kann es jedoch, insbesondere bei numerischen Problemen, praktisch sein, die Typen automatisch zu befördern.

### Defining Promotion Rules

Obwohl man prinzipiell Methoden für die Funktion `promote` direkt definieren könnte, würde dies viele redundante Definitionen für alle möglichen Permutationen von Argumenttypen erfordern. Stattdessen wird das Verhalten von `promote` in Bezug auf eine Hilfsfunktion namens [`promote_rule`](@ref) definiert, für die man Methoden bereitstellen kann. Die Funktion `promote_rule` nimmt ein Paar von Typobjekten und gibt ein anderes Typobjekt zurück, sodass Instanzen der Argumenttypen auf den zurückgegebenen Typ befördert werden. Somit wird durch die Definition der Regel:

```julia
import Base: promote_rule
promote_rule(::Type{Float64}, ::Type{Float32}) = Float64
```

man erklärt, dass wenn 64-Bit- und 32-Bit-Gleitkommawerte zusammen befördert werden, sie zu 64-Bit-Gleitkomma befördert werden sollten. Der Beförderungstyp muss nicht einer der Argumenttypen sein. Zum Beispiel treten die folgenden Beförderungsregeln sowohl in Julia Base auf:

```julia
promote_rule(::Type{BigInt}, ::Type{Float64}) = BigFloat
promote_rule(::Type{BigInt}, ::Type{Int8}) = BigInt
```

Im letzteren Fall ist der Ergebnistyp [`BigInt`](@ref), da `BigInt` der einzige Typ ist, der groß genug ist, um Ganzzahlen für die Ganzzahl-Arithmetik mit beliebiger Präzision zu halten. Beachten Sie auch, dass man nicht sowohl `promote_rule(::Type{A}, ::Type{B})` als auch `promote_rule(::Type{B}, ::Type{A})` definieren muss – die Symmetrie ist durch die Art und Weise, wie `promote_rule` im Promotionsprozess verwendet wird, impliziert.

Die `promote_rule`-Funktion wird als Baustein verwendet, um eine zweite Funktion namens [`promote_type`](@ref) zu definieren, die, gegeben beliebige Anzahl von Typobjekten, den gemeinsamen Typ zurückgibt, zu dem diese Werte, als Argumente an `promote`, befördert werden sollten. Wenn man also wissen möchte, was für ein Typ eine Sammlung von Werten bestimmter Typen in Abwesenheit tatsächlicher Werte befördern würde, kann man `promote_type` verwenden:

```jldoctest
julia> promote_type(Int8, Int64)
Int64
```

Beachten Sie, dass wir `promote_type` **nicht** direkt überladen: Wir überladen stattdessen `promote_rule`. `promote_type` verwendet `promote_rule` und fügt die Symmetrie hinzu. Ein direktes Überladen kann zu Mehrdeutigkeitsfehlern führen. Wir überladen `promote_rule`, um zu definieren, wie Dinge befördert werden sollen, und verwenden `promote_type`, um dies abzufragen.

Internally wird `promote_type` innerhalb von `promote` verwendet, um zu bestimmen, in welchen Typ Argumentwerte für die Promotion konvertiert werden sollen. Der neugierige Leser kann den Code in [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) lesen, der den vollständigen Promotionsmechanismus in etwa 35 Zeilen definiert.

### Case Study: Rational Promotions

Schließlich beenden wir unsere laufende Fallstudie über Julias rationalen Zahlentyp, der relativ anspruchsvoll den Promotionsmechanismus mit den folgenden Promotionsregeln nutzt:

```julia
import Base: promote_rule
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{Rational{S}}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:AbstractFloat} = promote_type(T,S)
```

Die erste Regel besagt, dass die Förderung einer rationalen Zahl mit einem anderen ganzzahligen Typ zu einem rationalen Typ führt, dessen Zähler-/Nenner-Typ das Ergebnis der Förderung seines Zähler-/Nenner-Typs mit dem anderen ganzzahligen Typ ist. Die zweite Regel wendet dieselbe Logik auf zwei verschiedene Typen rationaler Zahlen an, was zu einem rationalen Typ der Förderung ihrer jeweiligen Zähler-/Nenner-Typen führt. Die dritte und letzte Regel besagt, dass die Förderung einer rationalen Zahl mit einer Fließkommazahl zu demselben Typ führt wie die Förderung des Zähler-/Nenner-Typs mit der Fließkommazahl.

Diese kleine Handvoll von Promotionsregeln, zusammen mit den Konstruktoren des Typs und der standardmäßigen `convert`-Methode für Zahlen, sind ausreichend, um rationale Zahlen vollständig natürlich mit allen anderen numerischen Typen von Julia – Ganzzahlen, Fließkommazahlen und komplexen Zahlen – interoperabel zu machen. Durch die Bereitstellung geeigneter Umwandlungsmethoden und Promotionsregeln auf die gleiche Weise kann jeder benutzerdefinierte numerische Typ ebenso natürlich mit Julias vordefinierten numerischen Typen interagieren.

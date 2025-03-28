# [Types](@id man-types)

Typ-Systeme sind traditionell in zwei ganz unterschiedliche Lager gefallen: statische Typ-Systeme, bei denen jeder Programme Ausdruck einen Typ haben muss, der vor der Ausführung des Programms berechnet werden kann, und dynamische Typ-Systeme, bei denen bis zur Laufzeit nichts über Typen bekannt ist, wenn die tatsächlichen Werte, die vom Programm verarbeitet werden, verfügbar sind. Objektorientierung ermöglicht eine gewisse Flexibilität in statisch typisierten Sprachen, indem sie es erlaubt, Code zu schreiben, ohne dass die genauen Typen der Werte zur Compile-Zeit bekannt sind. Die Fähigkeit, Code zu schreiben, der mit verschiedenen Typen arbeiten kann, wird als Polymorphismus bezeichnet. Alle Codes in klassischen dynamisch typisierten Sprachen sind polymorph: Nur durch explizites Überprüfen von Typen oder wenn Objekte zur Laufzeit keine Operationen unterstützen, werden die Typen von Werten jemals eingeschränkt.

Julias Typsystem ist dynamisch, gewinnt jedoch einige der Vorteile statischer Typsysteme, indem es möglich ist, anzugeben, dass bestimmte Werte spezifische Typen haben. Dies kann bei der Generierung effizienter Codes von großem Nutzen sein, aber noch bedeutender ist, dass es die Methodenaufrufe auf die Typen der Funktionsargumente tief in die Sprache integriert. Der Methodenaufruf wird ausführlich in [Methods](@ref) behandelt, ist jedoch im Typsystem verankert, das hier vorgestellt wird.

Das Standardverhalten in Julia, wenn Typen weggelassen werden, erlaubt es, dass Werte jeden Typ haben können. Daher kann man viele nützliche Julia-Funktionen schreiben, ohne jemals explizit Typen zu verwenden. Wenn jedoch zusätzliche Ausdruckskraft benötigt wird, ist es einfach, schrittweise explizite Typannotationen in zuvor "untypisierten" Code einzuführen. Das Hinzufügen von Annotationen dient drei Hauptzwecken: um die leistungsstarke Mehrfachdispatch-Mechanik von Julia zu nutzen, um die Lesbarkeit für Menschen zu verbessern und um Programmierfehler zu erkennen.

Julia in der Sprache von [type systems](https://en.wikipedia.org/wiki/Type_system) ist: dynamisch, nominativ und parametrisch. Generische Typen können parametrisiert werden, und die hierarchischen Beziehungen zwischen Typen sind [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system), anstatt [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system). Ein besonders markantes Merkmal von Julias Typsystem ist, dass konkrete Typen sich nicht gegenseitig untertypen können: Alle konkreten Typen sind final und dürfen nur abstrakte Typen als ihre Supertypen haben. Auch wenn dies zunächst als unangemessen restriktiv erscheinen mag, hat es viele vorteilhafte Konsequenzen mit überraschend wenigen Nachteilen. Es stellt sich heraus, dass die Fähigkeit, Verhalten zu erben, viel wichtiger ist als die Fähigkeit, Struktur zu erben, und das Erben beider verursacht erhebliche Schwierigkeiten in traditionellen objektorientierten Sprachen. Weitere hochrangige Aspekte von Julias Typsystem, die zu Beginn erwähnt werden sollten, sind:

  * Es gibt keine Trennung zwischen Objekt- und Nicht-Objektwerten: Alle Werte in Julia sind wahre Objekte, die einen Typ haben, der zu einem einzigen, vollständig verbundenen Typgraphen gehört, dessen alle Knoten gleichermaßen erstklassig als Typen sind.
  * Es gibt kein sinnvolles Konzept eines "Kompilierungszeit-Typs": Der einzige Typ, den ein Wert hat, ist sein tatsächlicher Typ, wenn das Programm läuft. Dies wird in objektorientierten Sprachen als "Laufzeit-Typ" bezeichnet, wo die Kombination aus statischer Kompilierung und Polymorphismus diese Unterscheidung bedeutend macht.
  * Nur Werte, nicht Variablen, haben Typen – Variablen sind einfach Namen, die an Werte gebunden sind, obwohl wir der Einfachheit halber sagen können "Typ einer Variablen" als Kurzform für "Typ des Wertes, auf den sich eine Variable bezieht".
  * Sowohl abstrakte als auch konkrete Typen können durch andere Typen parametrisiert werden. Sie können auch durch Symbole, durch Werte eines beliebigen Typs, für den [`isbits`](@ref) wahr zurückgibt (im Wesentlichen Dinge wie Zahlen und Booles, die wie C-Typen oder `struct`s ohne Zeiger auf andere Objekte gespeichert sind), und auch durch Tupel davon. Typparameter können weggelassen werden, wenn sie nicht referenziert oder eingeschränkt werden müssen.

Julias Typsystem ist so gestaltet, dass es leistungsfähig und ausdrucksstark, gleichzeitig jedoch klar, intuitiv und unauffällig ist. Viele Julia-Programmierer werden möglicherweise nie das Bedürfnis verspüren, Code zu schreiben, der explizit Typen verwendet. Einige Arten der Programmierung hingegen werden mit deklarierten Typen klarer, einfacher, schneller und robuster.

## Type Declarations

Der `::` Operator kann verwendet werden, um Typannotationen an Ausdrücke und Variablen in Programmen anzuhängen. Es gibt zwei Hauptgründe, dies zu tun:

1. Als eine Behauptung, um zu helfen zu bestätigen, dass Ihr Programm so funktioniert, wie Sie es erwarten, und
2. Um dem Compiler zusätzliche Typinformationen bereitzustellen, die in einigen Fällen die Leistung verbessern können.

Wenn an einen Ausdruck, der einen Wert berechnet, angehängt, wird der `::`-Operator als "ist eine Instanz von" gelesen. Er kann überall verwendet werden, um zu bestätigen, dass der Wert des Ausdrucks auf der linken Seite eine Instanz des Typs auf der rechten Seite ist. Wenn der Typ auf der rechten Seite konkret ist, muss der Wert auf der linken Seite diesen Typ als seine Implementierung haben – denken Sie daran, dass alle konkreten Typen final sind, sodass keine Implementierung ein Subtyp eines anderen ist. Wenn der Typ abstrakt ist, reicht es aus, dass der Wert von einem konkreten Typ implementiert wird, der ein Subtyp des abstrakten Typs ist. Wenn die Typassertion nicht wahr ist, wird eine Ausnahme ausgelöst, andernfalls wird der Wert auf der linken Seite zurückgegeben:

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

Dies ermöglicht es, eine Typanpassung direkt an jeden Ausdruck anzuhängen.

Wenn es an eine Variable auf der linken Seite einer Zuweisung angehängt wird oder Teil einer `local`-Deklaration ist, bedeutet der `::`-Operator etwas anderes: Er erklärt, dass die Variable immer den angegebenen Typ haben soll, ähnlich einer Typdeklaration in einer statisch typisierten Sprache wie C. Jeder Wert, der der Variable zugewiesen wird, wird in den deklarierten Typ umgewandelt, indem [`convert`](@ref) verwendet wird:

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

Dieses Feature ist nützlich, um Leistungs-"Fallen" zu vermeiden, die auftreten könnten, wenn eine der Zuweisungen an eine Variable ihren Typ unerwartet ändert.

Dieses "Deklarations"-Verhalten tritt nur in bestimmten Kontexten auf:

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

und gilt für den gesamten aktuellen Geltungsbereich, sogar vor der Deklaration.

Seit Julia 1.8 können Typdeklarationen jetzt im globalen Geltungsbereich verwendet werden, d.h. Typannotationen können zu globalen Variablen hinzugefügt werden, um den Zugriff auf sie typstabil zu machen.

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

Deklarationen können auch an Funktionsdefinitionen angehängt werden:

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

Die Rückgabe aus dieser Funktion verhält sich genau wie eine Zuweisung an eine Variable mit einem deklarierten Typ: Der Wert wird immer in `Float64` umgewandelt.

## [Abstract Types](@id man-abstract-types)

Abstrakte Typen können nicht instanziiert werden und dienen nur als Knoten im Typgraphen, wodurch sie Mengen verwandter konkreter Typen beschreiben: jene konkreten Typen, die ihre Nachkommen sind. Wir beginnen mit abstrakten Typen, obwohl sie keine Instanziierung haben, da sie das Rückgrat des Typsystems bilden: Sie bilden die konzeptionelle Hierarchie, die Julias Typsystem mehr als nur eine Sammlung von Objektimplementierungen macht.

Erinnere dich daran, dass wir in [Integers and Floating-Point Numbers](@ref) eine Vielzahl konkreter Typen von numerischen Werten eingeführt haben: [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`Float16`](@ref), [`Float32`](@ref), und [`Float64`](@ref). Obwohl sie unterschiedliche Darstellungsgrößen haben, haben `Int8`, `Int16`, `Int32`, `Int64` und `Int128` gemeinsam, dass sie vorzeichenbehaftete Ganzzahltypen sind. Ebenso sind `UInt8`, `UInt16`, `UInt32`, `UInt64` und `UInt128` alle vorzeichenlosen Ganzzahltypen, während `Float16`, `Float32` und `Float64 sich dadurch unterscheiden, dass sie Fließkommatypen und keine Ganzzahlen sind. Es ist üblich, dass ein Stück Code nur dann sinnvoll ist, wenn seine Argumente eine Art von Ganzzahl sind, aber nicht wirklich davon abhängt, welche *Art* von Ganzzahl. Zum Beispiel funktioniert der Algorithmus für den größten gemeinsamen Teiler für alle Arten von Ganzzahlen, funktioniert jedoch nicht für Fließkommazahlen. Abstrakte Typen ermöglichen den Aufbau einer Hierarchie von Typen, die einen Kontext bieten, in den konkrete Typen passen können. Dies ermöglicht es Ihnen beispielsweise, einfach für jeden Typ zu programmieren, der eine Ganzzahl ist, ohne einen Algorithmus auf einen bestimmten Typ von Ganzzahl zu beschränken.

Abstrakte Typen werden mit dem [`abstract type`](@ref) Schlüsselwort deklariert. Die allgemeinen Syntaxen zur Deklaration eines abstrakten Typs sind:

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

Das Schlüsselwort `abstract type` führt einen neuen abstrakten Typ ein, dessen Name durch `«name»` angegeben wird. Dieser Name kann optional gefolgt werden von [`<:`](@ref) und einem bereits bestehenden Typ, was anzeigt, dass der neu deklarierte abstrakte Typ ein Untertyp dieses "Eltern"-Typs ist.

Wenn kein Supertyp angegeben ist, ist der Standard-Supertyp `Any` – ein vordefinierter abstrakter Typ, von dem alle Objekte Instanzen sind und alle Typen Subtypen sind. In der Typentheorie wird `Any` häufig als "top" bezeichnet, da es sich an der Spitze des Typgraphen befindet. Julia hat auch einen vordefinierten abstrakten "bottom" Typ, der sich am Tiefpunkt des Typgraphen befindet und als `Union{}` geschrieben wird. Er ist das genaue Gegenteil von `Any`: Kein Objekt ist eine Instanz von `Union{}` und alle Typen sind Supertypen von `Union{}`.

Lassen Sie uns einige der abstrakten Typen betrachten, die die numerische Hierarchie von Julia ausmachen:

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

Der [`Number`](@ref) Typ ist ein direkter Kindtyp von `Any`, und [`Real`](@ref) ist sein Kind. Im Gegenzug hat `Real` zwei Kinder (es hat mehr, aber hier werden nur zwei gezeigt; wir werden später auf die anderen eingehen): [`Integer`](@ref) und [`AbstractFloat`](@ref), die die Welt in Darstellungen von Ganzzahlen und Darstellungen von reellen Zahlen unterteilen. Darstellungen von reellen Zahlen umfassen Fließkommatypen, beinhalten aber auch andere Typen, wie z.B. rationale Zahlen. `AbstractFloat` umfasst nur Fließkommadarstellungen von reellen Zahlen. Ganzzahlen werden weiter unterteilt in [`Signed`](@ref) und [`Unsigned`](@ref) Varianten.

Der `<:` Operator bedeutet allgemein "ist ein Subtyp von" und erklärt, verwendet in Deklarationen wie den oben genannten, den rechten Typ als unmittelbaren Supertyp des neu deklarierten Typs. Er kann auch in Ausdrücken als Subtyp-Operator verwendet werden, der `true` zurückgibt, wenn sein linker Operand ein Subtyp seines rechten Operanden ist:

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

Ein wichtiger Einsatz von abstrakten Typen besteht darin, Standardimplementierungen für konkrete Typen bereitzustellen. Um ein einfaches Beispiel zu geben, betrachten Sie:

```julia
function myplus(x,y)
    x+y
end
```

Das erste, was zu beachten ist, ist, dass die obigen Argumentdeklarationen äquivalent zu `x::Any` und `y::Any` sind. Wenn diese Funktion aufgerufen wird, sagen wir als `myplus(2,5)`, wählt der Dispatcher die spezifischste Methode mit dem Namen `myplus`, die zu den gegebenen Argumenten passt. (Siehe [Methods](@ref) für weitere Informationen zu Multiple Dispatch.)

Angenommen, es wird keine spezifischere Methode als die oben genannte gefunden, definiert und kompiliert Julia intern eine Methode namens `myplus`, die speziell für zwei `Int`-Argumente basierend auf der oben genannten generischen Funktion ist, d.h. sie definiert und kompiliert implizit:

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

und schließlich ruft es diese spezifische Methode auf.

So ermöglichen abstrakte Typen Programmierern, generische Funktionen zu schreiben, die später als Standardmethode von vielen Kombinationen konkreter Typen verwendet werden können. Dank des mehrfachen Dispatch hat der Programmierer die volle Kontrolle darüber, ob die Standard- oder die spezifischere Methode verwendet wird.

Ein wichtiger Punkt ist, dass es keinen Leistungsverlust gibt, wenn der Programmierer sich auf eine Funktion verlässt, deren Argumente abstrakte Typen sind, da sie für jedes Tupel konkreter Argumenttypen, mit denen sie aufgerufen wird, neu kompiliert wird. (Es kann jedoch ein Leistungsproblem auftreten, wenn es sich um Funktionsargumente handelt, die Container abstrakter Typen sind; siehe [Performance Tips](@ref man-performance-abstract-container).)

## Primitive Types

!!! warning
    Es ist fast immer vorzuziehen, einen bestehenden primitiven Typ in einen neuen zusammengesetzten Typ zu wickeln, als einen eigenen primitiven Typ zu definieren.

    Diese Funktionalität existiert, um Julia zu ermöglichen, die standardmäßigen primitiven Typen, die LLVM unterstützt, zu bootstrappen. Sobald sie definiert sind, gibt es nur sehr wenig Grund, weitere zu definieren.


Ein primitiver Typ ist ein konkreter Typ, dessen Daten aus einfachen alten Bits bestehen. Klassische Beispiele für primitive Typen sind Ganzzahlen und Gleitkommawerte. Im Gegensatz zu den meisten Sprachen erlaubt es Julia, eigene primitive Typen zu deklarieren, anstatt nur eine feste Menge an eingebauten Typen bereitzustellen. Tatsächlich sind die standardmäßigen primitiven Typen alle in der Sprache selbst definiert:

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

Die allgemeinen Syntaxen zur Deklaration eines primitiven Typs sind:

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

Die Anzahl der Bits gibt an, wie viel Speicher der Typ benötigt, und der Name verleiht dem neuen Typ einen Namen. Ein primitiver Typ kann optional als Untertyp eines bestimmten Supertyps deklariert werden. Wenn ein Supertyp weggelassen wird, hat der Typ standardmäßig `Any` als seinen unmittelbaren Supertyp. Die Deklaration von [`Bool`](@ref) oben bedeutet daher, dass ein boolescher Wert acht Bits zum Speichern benötigt und [`Integer`](@ref) als seinen unmittelbaren Supertyp hat. Derzeit werden nur Größen unterstützt, die Vielfache von 8 Bits sind, und Sie werden wahrscheinlich auf LLVM-Fehler mit Größen stoßen, die von den oben verwendeten abweichen. Daher können boolesche Werte, obwohl sie tatsächlich nur ein einzelnes Bit benötigen, nicht kleiner als acht Bits deklariert werden.

Die Typen [`Bool`](@ref), [`Int8`](@ref) und [`UInt8`](@ref) haben alle identische Darstellungen: Sie sind acht-Bit-Chunks des Speichers. Da Julias Typsystem jedoch nominativ ist, sind sie trotz identischer Struktur nicht austauschbar. Ein grundlegender Unterschied zwischen ihnen ist, dass sie unterschiedliche Supertypen haben: Der direkte Supertyp von `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` ist [`Integer`](@ref), der von `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` ist [`Signed`](@ref), und der von `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` ist [`Unsigned`](@ref). Alle anderen Unterschiede zwischen `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`, `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` und `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` sind Verhaltensfragen – die Art und Weise, wie Funktionen definiert sind, um zu handeln, wenn ihnen Objekte dieser Typen als Argumente übergeben werden. Deshalb ist ein nominatives Typsystem notwendig: Wenn die Struktur den Typ bestimmen würde, der wiederum das Verhalten diktiert, wäre es unmöglich, `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` anders zu verhalten als `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` oder `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`.

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type) werden in verschiedenen Sprachen als Datensätze, Strukturen oder Objekte bezeichnet. Ein zusammengesetzter Typ ist eine Sammlung von benannten Feldern, deren Instanz als ein einzelner Wert behandelt werden kann. In vielen Sprachen sind zusammengesetzte Typen die einzige Art von benutzerdefiniertem Typ, und sie sind bei weitem der am häufigsten verwendete benutzerdefinierte Typ in Julia.

In mainstream objektorientierten Sprachen wie C++, Java, Python und Ruby haben zusammengesetzte Typen auch benannte Funktionen, die mit ihnen verbunden sind, und die Kombination wird als "Objekt" bezeichnet. In reineren objektorientierten Sprachen wie Ruby oder Smalltalk sind alle Werte Objekte, unabhängig davon, ob sie zusammengesetzt sind oder nicht. In weniger reinen objektorientierten Sprachen, einschließlich C++ und Java, sind einige Werte, wie Ganzzahlen und Gleitkommawerte, keine Objekte, während Instanzen benutzerdefinierter zusammengesetzter Typen wahre Objekte mit zugehörigen Methoden sind. In Julia sind alle Werte Objekte, aber Funktionen sind nicht mit den Objekten gebündelt, auf denen sie operieren. Dies ist notwendig, da Julia auswählt, welche Methode einer Funktion verwendet werden soll, durch Mehrfachdispatch, was bedeutet, dass die Typen *aller* Argumente einer Funktion berücksichtigt werden, wenn eine Methode ausgewählt wird, und nicht nur das erste (siehe [Methods](@ref) für weitere Informationen zu Methoden und Dispatch). Daher wäre es unangemessen, dass Funktionen nur ihrem ersten Argument "gehören". Die Organisation von Methoden in Funktionsobjekten, anstatt benannte Sammlungen von Methoden "innerhalb" jedes Objekts zu haben, erweist sich als ein äußerst vorteilhafter Aspekt des Sprachdesigns.

Zusammengesetzte Typen werden mit dem [`struct`](@ref) Schlüsselwort eingeführt, gefolgt von einem Block von Feldnamen, die optional mit Typen unter Verwendung des `::` Operators annotiert sind:

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

Felder ohne Typannotation haben standardmäßig den Typ `Any` und können entsprechend jeden Wert halten.

Neue Objekte vom Typ `Foo` werden erstellt, indem das `Foo`-Typobjekt wie eine Funktion auf Werte für seine Felder angewendet wird:

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

Wenn ein Typ wie eine Funktion angewendet wird, wird dies als *Konstruktor* bezeichnet. Zwei Konstruktoren werden automatisch generiert (diese werden als *Standardkonstruktoren* bezeichnet). Der eine akzeptiert beliebige Argumente und ruft [`convert`](@ref) auf, um sie in die Typen der Felder zu konvertieren, und der andere akzeptiert Argumente, die genau mit den Feldtypen übereinstimmen. Der Grund, warum beide generiert werden, ist, dass dies das Hinzufügen neuer Definitionen erleichtert, ohne versehentlich einen Standardkonstruktor zu ersetzen.

Da das Feld `bar` in seinem Typ nicht eingeschränkt ist, ist jeder Wert zulässig. Der Wert für `baz` muss jedoch in `Int` umwandelbar sein:

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

Sie können eine Liste von Feldnamen mit der Funktion [`fieldnames`](@ref) finden.

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

Sie können auf die Feldwerte eines zusammengesetzten Objekts mit der traditionellen `foo.bar`-Notation zugreifen:

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

Zusammengesetzte Objekte, die mit `struct` deklariert werden, sind *unveränderlich*; sie können nach der Konstruktion nicht mehr geändert werden. Das mag zunächst seltsam erscheinen, hat jedoch mehrere Vorteile:

  * Es kann effizienter sein. Einige Strukturen können effizient in Arrays gepackt werden, und in einigen Fällen ist der Compiler in der Lage, die Zuweisung unveränderlicher Objekte vollständig zu vermeiden.
  * Es ist nicht möglich, die Invarianten, die von den Konstruktoren des Typs bereitgestellt werden, zu verletzen.
  * Code mit unveränderlichen Objekten kann einfacher zu verstehen sein.

Ein unveränderliches Objekt kann veränderliche Objekte, wie Arrays, als Felder enthalten. Diese enthaltenen Objekte bleiben veränderlich; nur die Felder des unveränderlichen Objekts selbst können nicht geändert werden, um auf andere Objekte zu verweisen.

Wo erforderlich können veränderbare zusammengesetzte Objekte mit dem Schlüsselwort [`mutable struct`](@ref) deklariert werden, das im nächsten Abschnitt besprochen wird.

Wenn alle Felder einer unveränderlichen Struktur ununterscheidbar sind (`===`), dann sind auch zwei unveränderliche Werte, die diese Felder enthalten, ununterscheidbar:

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

Es gibt viel mehr zu sagen darüber, wie Instanzen von zusammengesetzten Typen erstellt werden, aber diese Diskussion hängt sowohl von [Parametric Types](@ref) als auch von [Methods](@ref) ab und ist ausreichend wichtig, um in einem eigenen Abschnitt behandelt zu werden: [Constructors](@ref man-constructors).

Für viele benutzerdefinierte Typen `X` möchten Sie möglicherweise eine Methode [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting) definieren, damit Instanzen dieses Typs als 0-dimensionale "Skalare" für [broadcasting](@ref Broadcasting) fungieren.

## Mutable Composite Types

Wenn ein zusammengesetzter Typ mit `mutable struct` anstelle von `struct` deklariert wird, können Instanzen davon geändert werden:

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

Eine zusätzliche Schnittstelle zwischen den Feldern und dem Benutzer kann durch [Instance Properties](@ref man-instance-properties) bereitgestellt werden. Dies gewährt mehr Kontrolle darüber, was mit der `bar.baz`-Notation zugegriffen und geändert werden kann.

Um Mutation zu unterstützen, werden solche Objekte in der Regel im Heap zugewiesen und haben stabile Speicheradressen. Ein veränderliches Objekt ist wie ein kleiner Behälter, der im Laufe der Zeit unterschiedliche Werte halten kann, und kann daher nur zuverlässig mit seiner Adresse identifiziert werden. Im Gegensatz dazu ist eine Instanz eines unveränderlichen Typs mit bestimmten Feldwerten verbunden – die Feldwerte allein sagen Ihnen alles über das Objekt. Bei der Entscheidung, ob ein Typ veränderlich sein soll, fragen Sie sich, ob zwei Instanzen mit denselben Feldwerten als identisch betrachtet werden würden oder ob sie im Laufe der Zeit unabhängig voneinander geändert werden müssten. Wenn sie als identisch betrachtet würden, sollte der Typ wahrscheinlich unveränderlich sein.

Um zusammenzufassen, zwei wesentliche Eigenschaften definieren Unveränderlichkeit in Julia:

  * Es ist nicht erlaubt, den Wert eines unveränderlichen Typs zu ändern.

      * Für Bittypen bedeutet dies, dass das Bitmuster eines Wertes, sobald es festgelegt ist, sich niemals ändert und dieser Wert die Identität eines Bittyps ist.
      * Für zusammengesetzte Typen bedeutet dies, dass die Identität der Werte ihrer Felder sich niemals ändern wird. Wenn die Felder Bit-Typen sind, bedeutet das, dass sich ihre Bits niemals ändern werden. Für Felder, deren Werte veränderliche Typen wie Arrays sind, bedeutet das, dass die Felder immer auf denselben veränderlichen Wert verweisen, auch wenn der Inhalt dieses veränderlichen Wertes selbst geändert werden kann.
  * Ein Objekt mit einem unveränderlichen Typ kann vom Compiler frei kopiert werden, da seine Unveränderlichkeit es unmöglich macht, programmgesteuert zwischen dem ursprünglichen Objekt und einer Kopie zu unterscheiden.

      * Insbesondere bedeutet dies, dass kleine, unveränderliche Werte wie Ganzzahlen und Fließkommazahlen typischerweise in Registern (oder im Stack) an Funktionen übergeben werden.
      * Veränderliche Werte hingegen werden im Heap zugewiesen und als Zeiger auf im Heap zugewiesene Werte an Funktionen übergeben, es sei denn, der Compiler ist sich sicher, dass es keine Möglichkeit gibt, zu erkennen, dass dies nicht der Fall ist.

In Fällen, in denen ein oder mehrere Felder einer ansonsten veränderbaren Struktur als unveränderlich bekannt sind, kann man diese Felder mit `const` wie unten gezeigt deklarieren. Dies ermöglicht einige, aber nicht alle Optimierungen von unveränderlichen Strukturen und kann verwendet werden, um Invarianten für die bestimmten als `const` markierten Felder durchzusetzen.

!!! compat "Julia 1.8"
    `const` annotierende Felder von veränderlichen Strukturen erfordert mindestens Julia 1.8.


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

Die drei Arten von Typen (abstrakt, primitiv, zusammengesetzt), die in den vorherigen Abschnitten besprochen wurden, sind tatsächlich alle eng miteinander verwandt. Sie teilen sich die gleichen Schlüsselmerkmale:

  * Sie sind ausdrücklich erklärt.
  * Sie haben Namen.
  * Sie haben explizit Supertypen deklariert.
  * Sie können Parameter haben.

Aufgrund dieser gemeinsamen Eigenschaften werden diese Typen intern als Instanzen desselben Konzepts, `DataType`, dargestellt, das der Typ eines dieser Typen ist:

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

Ein `DataType` kann abstrakt oder konkret sein. Wenn er konkret ist, hat er eine festgelegte Größe, ein Speicherlayout und (optional) Feldnamen. Somit ist ein primitiver Typ ein `DataType` mit einer Größe ungleich null, aber ohne Feldnamen. Ein zusammengesetzter Typ ist ein `DataType`, der Feldnamen hat oder leer ist (Größe null).

Jeder konkrete Wert im System ist eine Instanz eines bestimmten `DataType`.

## Type Unions

Ein Typenverein ist ein spezieller abstrakter Typ, der als Objekte alle Instanzen seiner Argumenttypen umfasst, die mit dem speziellen [`Union`](@ref) Schlüsselwort konstruiert werden:

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

Die Compiler für viele Sprachen haben eine interne Union-Konstruktion zur Typenbeurteilung; Julia stellt sie einfach dem Programmierer zur Verfügung. Der Julia-Compiler ist in der Lage, effizienten Code im Beisein von `Union`-Typen mit einer kleinen Anzahl von Typen [^1] zu generieren, indem er spezialisierten Code in separaten Zweigen für jeden möglichen Typ erzeugt.

Ein besonders nützlicher Fall eines `Union`-Typs ist `Union{T, Nothing}`, wobei `T` jeder Typ sein kann und [`Nothing`](@ref) der Singleton-Typ ist, dessen einzige Instanz das Objekt [`nothing`](@ref) ist. Dieses Muster ist das Äquivalent von [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type)-Typen in anderen Sprachen. Das Deklarieren eines Funktionsarguments oder eines Feldes als `Union{T, Nothing}` ermöglicht es, es entweder auf einen Wert des Typs `T` oder auf `nothing` zu setzen, um anzuzeigen, dass kein Wert vorhanden ist. Siehe [this FAQ entry](@ref faq-nothing) für weitere Informationen.

## Parametric Types

Ein wichtiges und leistungsstarkes Merkmal von Julias Typsystem ist, dass es parametrisch ist: Typen können Parameter annehmen, sodass Typdeklarationen tatsächlich eine ganze Familie neuer Typen einführen – einen für jede mögliche Kombination von Parameterwerten. Es gibt viele Sprachen, die eine Version von [generic programming](https://en.wikipedia.org/wiki/Generic_programming) unterstützen, in denen Datenstrukturen und Algorithmen zu deren Manipulation spezifiziert werden können, ohne die genauen beteiligten Typen anzugeben. Zum Beispiel existiert eine Form der generischen Programmierung in ML, Haskell, Ada, Eiffel, C++, Java, C#, F# und Scala, um nur einige zu nennen. Einige dieser Sprachen unterstützen echten parametrischen Polymorphismus (z. B. ML, Haskell, Scala), während andere ad-hoc, template-basierte Stile der generischen Programmierung unterstützen (z. B. C++, Java). Angesichts der vielen verschiedenen Varianten der generischen Programmierung und parametrischen Typen in verschiedenen Sprachen werden wir nicht einmal versuchen, Julias parametrische Typen mit anderen Sprachen zu vergleichen, sondern uns stattdessen darauf konzentrieren, Julias System für sich selbst zu erklären. Wir werden jedoch anmerken, dass, da Julia eine dynamisch typisierte Sprache ist und nicht alle Typentscheidungen zur Compile-Zeit treffen muss, viele traditionelle Schwierigkeiten, die in statischen parametrischen Typsystemen auftreten, relativ einfach gehandhabt werden können.

Alle deklarierten Typen (der `DataType`-Variante) können parametrisiert werden, und zwar mit derselben Syntax in jedem Fall. Wir werden sie in folgender Reihenfolge besprechen: zuerst parametrische zusammengesetzte Typen, dann parametrische abstrakte Typen und schließlich parametrische primitive Typen.

### [Parametric Composite Types](@id man-parametric-composite-types)

Typ-Parameter werden unmittelbar nach dem Typnamen eingeführt, umgeben von geschweiften Klammern:

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

Diese Deklaration definiert einen neuen parametrischen Typ, `Point{T}`, der zwei "Koordinaten" vom Typ `T` hält. Was, so könnte man fragen, ist `T`? Nun, das ist genau der Punkt parametrischer Typen: Es kann jeder Typ sein (oder ein Wert eines beliebigen Bittyps, tatsächlich, obwohl er hier eindeutig als Typ verwendet wird). `Point{Float64}` ist ein konkreter Typ, der dem Typ entspricht, der durch das Ersetzen von `T` in der Definition von `Point` mit [`Float64`](@ref) definiert wird. Somit erklärt diese einzelne Deklaration tatsächlich eine unbegrenzte Anzahl von Typen: `Point{Float64}`, `Point{AbstractString}`, `Point{Int64}`, usw. Jeder dieser Typen ist jetzt ein verwendbarer konkreter Typ:

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

Der Typ `Point{Float64}` ist ein Punkt, dessen Koordinaten 64-Bit-Gleitkommawerte sind, während der Typ `Point{AbstractString}` ein "Punkt" ist, dessen "Koordinaten" String-Objekte sind (siehe [Strings](@ref)).

`Point` selbst ist auch ein gültiger Typobjekt, das alle Instanzen `Point{Float64}`, `Point{AbstractString}`, usw. als Subtypen enthält:

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

Andere Typen sind natürlich keine Untertypen davon:

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

Konkrete `Point`-Typen mit unterschiedlichen Werten von `T` sind niemals Subtypen voneinander:

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    Dieser letzte Punkt ist *sehr* wichtig: auch wenn `Float64 <: Real` haben wir **NICHT** `Point{Float64} <: Point{Real}`.


Mit anderen Worten, in der Sprache der Typentheorie sind Julias Typparameter *invariant*, anstatt [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29) zu sein. Dies hat praktische Gründe: Während jede Instanz von `Point{Float64}` konzeptionell wie eine Instanz von `Point{Real}` sein kann, haben die beiden Typen unterschiedliche Darstellungen im Speicher:

  * Eine Instanz von `Point{Float64}` kann kompakt und effizient als ein unmittelbares Paar von 64-Bit-Werten dargestellt werden;
  * Eine Instanz von `Point{Real}` muss in der Lage sein, jedes Paar von Instanzen von [`Real`](@ref) zu halten. Da Objekte, die Instanzen von `Real` sind, beliebige Größen und Strukturen haben können, muss eine Instanz von `Point{Real}` in der Praxis als ein Paar von Zeigern auf individuell zugewiesene `Real`-Objekte dargestellt werden.

Die Effizienz, die durch die Möglichkeit gewonnen wird, `Point{Float64}`-Objekte mit unmittelbaren Werten zu speichern, wird im Fall von Arrays enorm verstärkt: Ein `Array{Float64}` kann als zusammenhängender Speicherblock von 64-Bit-Gleitkommawerten gespeichert werden, während ein `Array{Real}` ein Array von Zeigern auf individuell zugewiesene [`Real`](@ref)-Objekte sein muss – die möglicherweise [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing) 64-Bit-Gleitkommawerte sind, aber auch beliebig große, komplexe Objekte sein könnten, die als Implementierungen des abstrakten Typs `Real` deklariert sind.

Da `Point{Float64}` kein Subtyp von `Point{Real}` ist, kann die folgende Methode nicht auf Argumente vom Typ `Point{Float64}` angewendet werden:

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

Eine korrekte Möglichkeit, eine Methode zu definieren, die alle Argumente vom Typ `Point{T}` akzeptiert, wobei `T` ein Untertyp von [`Real`](@ref) ist, lautet:

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

(Äquivalent könnte man `function norm(p::Point{T} where T<:Real)` oder `function norm(p::Point{T}) where T<:Real` definieren; siehe [UnionAll Types](@ref).)

Weitere Beispiele werden später in [Methods](@ref) besprochen.

Wie konstruiert man ein `Point`-Objekt? Es ist möglich, benutzerdefinierte Konstruktoren für zusammengesetzte Typen zu definieren, die ausführlich in [Constructors](@ref man-constructors) behandelt werden, aber in Abwesenheit von speziellen Konstruktorerklärungen gibt es zwei Standardmethoden zur Erstellung neuer zusammengesetzter Objekte: eine, bei der die Typparameter explizit angegeben werden, und die andere, bei der sie durch die Argumente des Objektkonstruktors impliziert werden.

Da der Typ `Point{Float64}` ein konkreter Typ ist, der äquivalent zu `Point` ist, der mit [`Float64`](@ref) anstelle von `T` deklariert wurde, kann er entsprechend als Konstruktor angewendet werden:

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

Für den Standardkonstruktor muss genau ein Argument für jedes Feld bereitgestellt werden:

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

Nur ein Standardkonstruktor wird für parametrische Typen generiert, da es nicht möglich ist, ihn zu überschreiben. Dieser Konstruktor akzeptiert beliebige Argumente und konvertiert sie in die Feldtypen.

In vielen Fällen ist es redundant, den Typ des `Point`-Objekts anzugeben, das man konstruieren möchte, da die Typen der Argumente des Konstruktors bereits implizit Typinformationen bereitstellen. Aus diesem Grund kann man auch `Point` selbst als Konstruktor verwenden, vorausgesetzt, der implizierte Wert des Parameter-Typs `T` ist eindeutig:

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

Im Falle von `Point` ist der Typ von `T` eindeutig impliziert, wenn und nur wenn die beiden Argumente von `Point` denselben Typ haben. Wenn dies nicht der Fall ist, schlägt der Konstruktor mit einem [`MethodError`](@ref) fehl:

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

Konstruktor-Methoden, um solche Mischfälle angemessen zu behandeln, können definiert werden, aber das wird erst später in [Constructors](@ref man-constructors) besprochen.

### Parametric Abstract Types

Parametrische abstrakte Typdeklarationen erklären eine Sammlung von abstrakten Typen, ähnlich wie:

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

Mit dieser Deklaration ist `Pointy{T}` ein distinct abstrakter Typ für jeden Typ oder ganzzahligen Wert von `T`. Wie bei parametrischen zusammengesetzten Typen ist jede solche Instanz ein Subtyp von `Pointy`:

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

Parametrische abstrakte Typen sind invariant, ebenso wie parametrische zusammengesetzte Typen:

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

Die Notation `Pointy{<:Real}` kann verwendet werden, um das Julia-Äquivalent eines *kovarianten* Typs auszudrücken, während `Pointy{>:Int}` das Äquivalent eines *kontravarianten* Typs darstellt, aber technisch gesehen repräsentieren diese *Mengen* von Typen (siehe [UnionAll Types](@ref)).

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

So wie einfache abstrakte Typen dazu dienen, eine nützliche Hierarchie von Typen über konkreten Typen zu schaffen, dienen parametrische abstrakte Typen demselben Zweck in Bezug auf parametrische zusammengesetzte Typen. Wir könnten zum Beispiel `Point{T}` als Untertyp von `Pointy{T}` wie folgt deklariert haben:

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

Gegeben eine solche Deklaration haben wir für jede Wahl von `T` `Point{T}` als einen Subtyp von `Pointy{T}`:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

Diese Beziehung ist ebenfalls invariant:

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

Parametrische abstrakte Typen wie `Pointy` dienen dazu, eine flexible und wiederverwendbare Schnittstelle für verschiedene Implementierungen von Punkten zu schaffen. Sie ermöglichen es, verschiedene Punktarten zu definieren, die unterschiedliche Eigenschaften oder Verhaltensweisen haben, während sie dennoch eine gemeinsame Basis teilen.

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

Jetzt sind sowohl `Point{Float64}` als auch `DiagPoint{Float64}` Implementierungen der Abstraktion `Pointy{Float64}`, und ähnlich für jede andere mögliche Wahl des Typs `T`. Dies ermöglicht das Programmieren über eine gemeinsame Schnittstelle, die von allen `Pointy`-Objekten geteilt wird, die sowohl für `Point` als auch für `DiagPoint` implementiert ist. Dies kann jedoch nicht vollständig demonstriert werden, bis wir Methoden und Dispatch im nächsten Abschnitt, [Methods](@ref), eingeführt haben.

Es gibt Situationen, in denen es möglicherweise keinen Sinn macht, dass Typparameter frei über alle möglichen Typen variieren. In solchen Situationen kann man den Bereich von `T` wie folgt einschränken:

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

Mit einer solchen Deklaration ist es akzeptabel, jeden Typ zu verwenden, der ein Subtyp von [`Real`](@ref) anstelle von `T` ist, jedoch keine Typen, die keine Subtypen von `Real` sind:

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

Typparameter für parametrische zusammengesetzte Typen können auf die gleiche Weise eingeschränkt werden:

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

Um ein reales Beispiel dafür zu geben, wie all diese parametrischen Typen nützlich sein können, hier ist die tatsächliche Definition von Julias [`Rational`](@ref) unveränderlichem Typ (außer dass wir den Konstruktor hier der Einfachheit halber weglassen), der ein genaues Verhältnis von Ganzzahlen darstellt:

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

Es macht nur Sinn, Verhältnisse von Ganzzahlen zu bilden, daher ist der Parameter-Typ `T` auf einen Untertyp von [`Integer`](@ref) beschränkt, und ein Verhältnis von Ganzzahlen stellt einen Wert auf der reellen Zahlengeraden dar, sodass jede [`Rational`](@ref) eine Instanz der [`Real`](@ref) Abstraktion ist.

### Tuple Types

Tupel sind eine Abstraktion der Argumente einer Funktion – ohne die Funktion selbst. Die wesentlichen Aspekte der Argumente einer Funktion sind ihre Reihenfolge und ihre Typen. Daher ähnelt ein Tupeltyp einem parametrisierten unveränderlichen Typ, bei dem jeder Parameter der Typ eines Feldes ist. Zum Beispiel ähnelt ein Tupeltyp mit 2 Elementen dem folgenden unveränderlichen Typ:

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

Es gibt jedoch drei wesentliche Unterschiede:

  * Tuple-Typen können beliebig viele Parameter haben.
  * Tuple-Typen sind *kovariant* in ihren Parametern: `Tuple{Int}` ist ein Subtyp von `Tuple{Any}`. Daher wird `Tuple{Any}` als abstrakter Typ betrachtet, und Tuple-Typen sind nur konkret, wenn ihre Parameter es sind.
  * Tupel haben keine Feldnamen; Felder werden nur über den Index zugegriffen.

Tupelwerte werden mit Klammern und Kommas geschrieben. Wenn ein Tupel erstellt wird, wird bei Bedarf ein entsprechender Tupeltyp generiert:

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

Beachten Sie die Implikationen der Kovarianz:

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

Intuitiv bedeutet dies, dass der Typ der Argumente einer Funktion ein Subtyp der Signatur der Funktion ist (wenn die Signatur übereinstimmt).

### Vararg Tuple Types

Der letzte Parameter eines Tupeltyps kann der spezielle Wert [`Vararg`](@ref) sein, der eine beliebige Anzahl von nachfolgenden Elementen bezeichnet:

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

Darüber hinaus entspricht `Vararg{T}` null oder mehr Elementen des Typs `T`. Vararg-Tupeltypen werden verwendet, um die Argumente darzustellen, die von Varargs-Methoden akzeptiert werden (siehe [Varargs Functions](@ref)).

Der spezielle Wert `Vararg{T,N}` (wenn er als letzter Parameter eines Tupeltyps verwendet wird) entspricht genau `N` Elementen des Typs `T`. `NTuple{N,T}` ist ein praktischer Alias für `Tuple{Vararg{T,N}}`, d.h. ein Tupeltyp, der genau `N` Elemente des Typs `T` enthält.

### Named Tuple Types

Benannte Tupel sind Instanzen des [`NamedTuple`](@ref) Typs, der zwei Parameter hat: ein Tupel von Symbolen, das die Feldnamen angibt, und einen Tupeltyp, der die Feldtypen angibt. Zur Vereinfachung werden `NamedTuple`-Typen mit dem [`@NamedTuple`](@ref) Makro ausgegeben, das eine bequeme `struct`-ähnliche Syntax für die Deklaration dieser Typen über `key::Type`-Deklarationen bietet, wobei ein ausgelassener `::Type` `::Any` entspricht.

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

Die `begin ... end`-Form des `@NamedTuple`-Makros ermöglicht es, die Deklarationen über mehrere Zeilen zu verteilen (ähnlich einer Strukturdeklaration), ist jedoch ansonsten gleichwertig:

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

Ein `NamedTuple`-Typ kann als Konstruktor verwendet werden, der ein einzelnes Tupel-Argument akzeptiert. Der konstruierte `NamedTuple`-Typ kann entweder ein konkreter Typ sein, bei dem beide Parameter angegeben sind, oder ein Typ, der nur Feldnamen angibt:

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

Wenn die Feldtypen angegeben sind, werden die Argumente konvertiert. Andernfalls werden die Typen der Argumente direkt verwendet.

### Parametric Primitive Types

Primitive-Typen können auch parametrisch deklariert werden. Zum Beispiel werden Zeiger als primitive Typen dargestellt, die in Julia wie folgt deklariert werden:

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

Die leicht seltsame Eigenschaft dieser Deklarationen im Vergleich zu typischen parametrischen zusammengesetzten Typen besteht darin, dass der Typparameter `T` in der Definition des Typs selbst nicht verwendet wird – er ist nur ein abstrakter Tag, der im Wesentlichen eine gesamte Familie von Typen mit identischer Struktur definiert, die sich nur durch ihren Typparameter unterscheiden. Daher sind `Ptr{Float64}` und `Ptr{Int64}` unterschiedliche Typen, obwohl sie identische Darstellungen haben. Und natürlich sind alle spezifischen Zeigertypen Untertypen des übergeordneten [`Ptr`](@ref) Typs:

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

Wir haben gesagt, dass ein parametrischer Typ wie `Ptr` als Supertyp aller seiner Instanzen (`Ptr{Int64}` usw.) fungiert. Wie funktioniert das? `Ptr` selbst kann kein normaler Datentyp sein, da der Typ der referenzierten Daten ohne Kenntnis nicht für Speicheroperationen verwendet werden kann. Die Antwort ist, dass `Ptr` (oder andere parametrische Typen wie `Array`) eine andere Art von Typ ist, die als [`UnionAll`](@ref)-Typ bezeichnet wird. Ein solcher Typ drückt die *iterierte Vereinigung* von Typen für alle Werte eines bestimmten Parameters aus.

`UnionAll`-Typen werden normalerweise mit dem Schlüsselwort `where` geschrieben. Zum Beispiel könnte `Ptr` genauer als `Ptr{T} where T` geschrieben werden, was bedeutet, dass alle Werte, deren Typ `Ptr{T}` für einen bestimmten Wert von `T` ist. In diesem Kontext wird der Parameter `T` auch oft als "Typvariable" bezeichnet, da er wie eine Variable ist, die über Typen variiert. Jede `where`-Klausel führt eine einzelne Typvariable ein, sodass diese Ausdrücke für Typen mit mehreren Parametern geschachtelt sind, zum Beispiel `Array{T,N} where N where T`.

Die Typanwendungssyntax `A{B,C}` erfordert, dass `A` ein `UnionAll`-Typ ist, und ersetzt zuerst `B` für die äußerste Typvariable in `A`. Das Ergebnis wird als ein weiterer `UnionAll`-Typ erwartet, in den dann `C` substituiert wird. Daher ist `A{B,C}` äquivalent zu `A{B}{C}`. Dies erklärt, warum es möglich ist, einen Typ teilweise zu instanziieren, wie zum Beispiel `Array{Float64}`: Der erste Parameterwert wurde festgelegt, aber der zweite variiert über alle möglichen Werte. Mit der expliziten `where`-Syntax können beliebige Teilmengen von Parametern festgelegt werden. Zum Beispiel kann der Typ aller eindimensionalen Arrays als `Array{T,1} where T` geschrieben werden.

Typvariablen können durch Subtypbeziehungen eingeschränkt werden. `Array{T} where T<:Integer` bezieht sich auf alle Arrays, deren Elementtyp eine Art von [`Integer`](@ref) ist. Die Syntax `Array{<:Integer}` ist eine praktische Abkürzung für `Array{T} where T<:Integer`. Typvariablen können sowohl untere als auch obere Grenzen haben. `Array{T} where Int<:T<:Number` bezieht sich auf alle Arrays von [`Number`](@ref)s, die in der Lage sind, `Int`s zu enthalten (da `T` mindestens so groß wie `Int` sein muss). Die Syntax `where T>:Int` funktioniert ebenfalls, um nur die untere Grenze einer Typvariablen anzugeben, und `Array{>:Int}` ist äquivalent zu `Array{T} where T>:Int`.

Da `where`-Ausdrücke geschachtelt sind, können Typvariablenbeschränkungen auf äußere Typvariablen verweisen. Zum Beispiel bezieht sich `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real` auf 2-Tupel, deren erstes Element ein [`Real`](@ref) ist und dessen zweites Element ein `Array` beliebiger Art von Array ist, dessen Elementtyp den Typ des ersten Tupel-Elements enthält.

Das `where`-Schlüsselwort kann selbst in einer komplexeren Deklaration geschachtelt werden. Betrachten Sie beispielsweise die beiden Typen, die durch die folgenden Deklarationen erstellt wurden:

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

Der Typ `T1` definiert ein eindimensionales Array von eindimensionalen Arrays; jedes der inneren Arrays besteht aus Objekten desselben Typs, aber dieser Typ kann von einem inneren Array zum nächsten variieren. Andererseits definiert der Typ `T2` ein eindimensionales Array von eindimensionalen Arrays, deren innere Arrays alle denselben Typ haben müssen. Beachten Sie, dass `T2` ein abstrakter Typ ist, z. B. `Array{Array{Int,1},1} <: T2`, während `T1` ein konkreter Typ ist. Infolgedessen kann `T1` mit einem Null-Argument-Konstruktor `a=T1()` konstruiert werden, `T2` jedoch nicht.

Es gibt eine praktische Syntax zur Benennung solcher Typen, ähnlich der Kurzform der Funktionsdefinitionssyntax:

```julia
Vector{T} = Array{T, 1}
```

Dies entspricht `const Vector = Array{T,1} where T`. Das Schreiben von `Vector{Float64}` ist äquivalent zum Schreiben von `Array{Float64,1}`, und der Übertyp `Vector` hat als Instanzen alle `Array`-Objekte, bei denen der zweite Parameter – die Anzahl der Array-Dimensionen – 1 ist, unabhängig davon, welcher Elementtyp vorliegt. In Sprachen, in denen parametrische Typen immer vollständig angegeben werden müssen, ist dies nicht besonders hilfreich, aber in Julia ermöglicht es, einfach `Vector` für den abstrakten Typ zu schreiben, der alle eindimensionalen dichten Arrays eines beliebigen Elementtyps umfasst.

## [Singleton types](@id man-singleton-types)

Unveränderliche zusammengesetzte Typen ohne Felder werden *Singletons* genannt. Formal, wenn

1. `T` ist ein unveränderlicher zusammengesetzter Typ (d.h. definiert mit `struct`),
2. `a ist T && b ist T` impliziert `a === b`,

dann ist `T` ein Singleton-Typ.[^2] [`Base.issingletontype`](@ref) kann verwendet werden, um zu überprüfen, ob ein Typ ein Singleton-Typ ist. [Abstract types](@ref man-abstract-types) können von der Konstruktion her keine Singleton-Typen sein.

Aus der Definition folgt, dass es nur eine Instanz solcher Typen geben kann:

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

Die [`===`](@ref)-Funktion bestätigt, dass die konstruierten Instanzen von `NoFields` tatsächlich ein und dieselbe sind.

Parametrische Typen können Singleton-Typen sein, wenn die oben genannte Bedingung erfüllt ist. Zum Beispiel,

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

Jede Funktion hat ihren eigenen Typ, der ein Subtyp von `Function` ist.

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

Beachten Sie, wie `typeof(foo41)` sich selbst ausgibt. Dies ist lediglich eine Konvention für die Ausgabe, da es sich um ein erstklassiges Objekt handelt, das wie jeder andere Wert verwendet werden kann:

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

Arten von Funktionen, die auf der obersten Ebene definiert sind, sind Singletons. Wenn nötig, können Sie sie mit [`===`](@ref) vergleichen.

[Closures](@ref man-anonymous-functions) haben auch ihren eigenen Typ, der normalerweise mit Namen gedruckt wird, die mit `#<number>` enden. Namen und Typen für Funktionen, die an verschiedenen Orten definiert sind, sind unterschiedlich, aber es ist nicht garantiert, dass sie in verschiedenen Sitzungen auf die gleiche Weise gedruckt werden.

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

Arten von Closures sind nicht unbedingt Singletons.

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

Für jeden Typ `T` ist `Type{T}` ein abstrakter parametrischer Typ, dessen einzige Instanz das Objekt `T` ist. Bis wir [Parametric Methods](@ref) und [conversions](@ref conversion-and-promotion) besprechen, ist es schwierig, den Nutzen dieses Konstrukts zu erklären, aber kurz gesagt, es ermöglicht, das Verhalten von Funktionen auf spezifische Typen als *Werte* zu spezialisieren. Dies ist nützlich, um Methoden (insbesondere parametrische) zu schreiben, deren Verhalten von einem Typ abhängt, der als explizites Argument angegeben wird, anstatt durch den Typ eines ihrer Argumente impliziert zu werden.

Da die Definition etwas schwer zu verstehen ist, schauen wir uns einige Beispiele an:

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

Mit anderen Worten, [`isa(A, Type{B})`](@ref) ist wahr, wenn und nur wenn `A` und `B` dasselbe Objekt sind und dieses Objekt ein Typ ist.

Insbesondere, da parametrische Typen [invariant](@ref man-parametric-composite-types) sind, haben wir

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

Ohne den Parameter ist `Type` einfach ein abstrakter Typ, der alle Typobjekte als seine Instanzen hat:

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

Jedes Objekt, das kein Typ ist, ist keine Instanz von `Type`:

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

Während `Type` Teil von Julias Typ-Hierarchie ist, wie jeder andere abstrakte parametrische Typ, wird es außerhalb von Methodensignaturen nicht häufig verwendet, außer in einigen speziellen Fällen. Ein weiterer wichtiger Anwendungsfall für `Type` ist das Schärfen von Feldtypen, die ansonsten weniger präzise erfasst werden würden, z. B. als [`DataType`](@ref man-declared-types) im folgenden Beispiel, wo der Standardkonstruktor zu Leistungsproblemen in Code führen könnte, der auf den präzisen umschlossenen Typ angewiesen ist (ähnlich wie [abstract type parameters](@ref man-performance-abstract-container)).

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

Manchmal ist es praktisch, einen neuen Namen für einen bereits ausdrückbaren Typ einzuführen. Dies kann mit einer einfachen Zuweisungsanweisung erfolgen. Zum Beispiel wird `UInt` entweder auf [`UInt32`](@ref) oder [`UInt64`](@ref) aliasiert, je nach Größe der Zeiger im System:

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

Dies wird durch den folgenden Code in `base/boot.jl` erreicht:

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

Natürlich hängt das davon ab, was `Int` aliasiert ist – aber das ist vordefiniert, um den richtigen Typ zu sein – entweder [`Int32`](@ref) oder [`Int64`](@ref).

(Hinweis: Im Gegensatz zu `Int` existiert `Float` nicht als Typalias für eine spezifische Größe [`AbstractFloat`](@ref). Im Gegensatz zu Ganzzahlregistern, bei denen die Größe von `Int` der Größe eines nativen Zeigers auf dieser Maschine entspricht, werden die Größen der Gleitkommaregister durch den IEEE-754-Standard festgelegt.)

Typaliasen können parametrisiert werden:

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

Da Typen in Julia selbst Objekte sind, können gewöhnliche Funktionen auf ihnen operieren. Einige Funktionen, die besonders nützlich sind, um mit Typen zu arbeiten oder sie zu erkunden, wurden bereits eingeführt, wie der `<:`-Operator, der angibt, ob sein linkes Operanden ein Subtyp seines rechten Operanden ist.

Die [`isa`](@ref)-Funktion testet, ob ein Objekt von einem bestimmten Typ ist, und gibt true oder false zurück:

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

Die [`typeof`](@ref)-Funktion, die bereits im gesamten Handbuch in Beispielen verwendet wurde, gibt den Typ ihres Arguments zurück. Da, wie oben erwähnt, Typen Objekte sind, haben sie auch Typen, und wir können fragen, was ihre Typen sind:

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

Was passiert, wenn wir den Prozess wiederholen? Was ist der Typ eines Typs eines Typs? Wie es der Fall ist, sind Typen alle zusammengesetzte Werte und haben daher alle den Typ `DataType`:

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType` ist sein eigener Typ.

Eine weitere Operation, die auf einige Typen angewendet wird, ist [`supertype`](@ref), die den Supertyp eines Typs offenbart. Nur deklarierte Typen (`DataType`) haben eindeutige Supertypen:

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

Wenn Sie [`supertype`](@ref) auf andere Typobjekte (oder Nicht-Typobjekte) anwenden, wird ein [`MethodError`](@ref) ausgelöst:

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

Oft möchte man anpassen, wie Instanzen eines Typs angezeigt werden. Dies wird erreicht, indem die [`show`](@ref)-Funktion überladen wird. Zum Beispiel, nehmen wir an, wir definieren einen Typ, um komplexe Zahlen in polarer Form darzustellen:

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

Hier haben wir eine benutzerdefinierte Konstruktorfunktion hinzugefügt, damit sie Argumente verschiedener [`Real`](@ref)-Typen annehmen und sie in einen gemeinsamen Typ umwandeln kann (siehe [Constructors](@ref man-constructors) und [Conversion and Promotion](@ref conversion-and-promotion)). (Natürlich müssten wir auch viele andere Methoden definieren, um es wie ein [`Number`](@ref) agieren zu lassen, z.B. `+`, `*`, `one`, `zero`, Promotionsregeln usw.) Standardmäßig zeigen Instanzen dieses Typs recht einfach Informationen über den Typnamen und die Feldwerte an, z.B. `Polar{Float64}(3.0,4.0)`.

Wenn wir möchten, dass es stattdessen als `3.0 * exp(4.0im)` angezeigt wird, würden wir die folgende Methode definieren, um das Objekt an ein bestimmtes Ausgabegerät `io` (das eine Datei, ein Terminal, einen Puffer usw. darstellt; siehe [Networking and Streams](@ref)) auszugeben:

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

Eine feinere Steuerung über die Anzeige von `Polar`-Objekten ist möglich. Insbesondere möchte man manchmal sowohl ein ausführliches mehrzeiliges Druckformat, das zur Anzeige eines einzelnen Objekts in der REPL und anderen interaktiven Umgebungen verwendet wird, als auch ein kompakteres einzeiliges Format, das für [`print`](@ref) oder zur Anzeige des Objekts als Teil eines anderen Objekts (z. B. in einem Array) verwendet wird. Obwohl standardmäßig die Funktion `show(io, z)` in beiden Fällen aufgerufen wird, können Sie ein *anderes* mehrzeiliges Format zur Anzeige eines Objekts definieren, indem Sie eine dreiarugumentige Form von `show` überladen, die den MIME-Typ `text/plain` als zweiten Parameter verwendet (siehe [Multimedia I/O](@ref Multimedia-I/O)), zum Beispiel:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

(Beachten Sie, dass `print(..., z)` hier die 2-Argumente-Methode `show(io, z)` aufruft.) Dies führt zu:

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

wo die einzeilige `show(io, z)`-Form weiterhin für ein Array von `Polar`-Werten verwendet wird. Technisch gesehen ruft die REPL `display(z)` auf, um das Ergebnis der Ausführung einer Zeile anzuzeigen, was standardmäßig `show(stdout, MIME("text/plain"), z)` entspricht, was wiederum standardmäßig `show(stdout, z)` entspricht, aber Sie sollten *keine* neuen [`display`](@ref)-Methoden definieren, es sei denn, Sie definieren einen neuen Multimedia-Anzeigebehandler (siehe [Multimedia I/O](@ref Multimedia-I/O)).

Darüber hinaus können Sie auch `show`-Methoden für andere MIME-Typen definieren, um eine reichhaltigere Anzeige (HTML, Bilder usw.) von Objekten in Umgebungen zu ermöglichen, die dies unterstützen (z. B. IJulia). Zum Beispiel können wir die formatierte HTML-Anzeige von `Polar`-Objekten mit Hochzahlen und Kursivschrift definieren, über:

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

Ein `Polar`-Objekt wird dann automatisch mit HTML in einer Umgebung angezeigt, die die HTML-Darstellung unterstützt, aber Sie können `show` manuell aufrufen, um HTML-Ausgaben zu erhalten, wenn Sie möchten:

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

Als Faustregel sollte die einzeilige `show`-Methode einen gültigen Julia-Ausdruck drucken, um das angezeigte Objekt zu erstellen. Wenn diese `show`-Methode infix-Operatoren enthält, wie zum Beispiel den Multiplikationsoperator (`*`) in unserer einzeiligen `show`-Methode für `Polar` oben, kann es sein, dass sie nicht korrekt geparst wird, wenn sie als Teil eines anderen Objekts gedruckt wird. Um dies zu sehen, betrachten Sie das Ausdrucksobjekt (siehe [Program representation](@ref)), das das Quadrat einer bestimmten Instanz unseres `Polar`-Typs nimmt:

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

Weil der Operator `^` eine höhere Priorität als `*` hat (siehe [Operator Precedence and Associativity](@ref)), stellt diese Ausgabe den Ausdruck `a ^ 2` nicht treu dar, der gleich `(3.0 * exp(4.0im)) ^ 2` sein sollte. Um dieses Problem zu lösen, müssen wir eine benutzerdefinierte Methode für `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)` erstellen, die intern vom Ausdrucksobjekt beim Drucken aufgerufen wird:

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

Die oben definierte Methode fügt Klammern um den Aufruf von `show` hinzu, wenn die Priorität des aufrufenden Operators höher oder gleich der Priorität der Multiplikation ist. Diese Überprüfung ermöglicht es, Ausdrücke, die ohne die Klammern korrekt geparst werden (wie `:($a + 2)` und `:($a == 2)`), beim Drucken wegzulassen:

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

In einigen Fällen ist es nützlich, das Verhalten von `show`-Methoden je nach Kontext anzupassen. Dies kann über den [`IOContext`](@ref)-Typ erreicht werden, der es ermöglicht, kontextuelle Eigenschaften zusammen mit einem umschlossenen IO-Stream zu übergeben. Zum Beispiel können wir eine kürzere Darstellung in unserer `show`-Methode erstellen, wenn die `:compact`-Eigenschaft auf `true` gesetzt ist, und auf die lange Darstellung zurückgreifen, wenn die Eigenschaft `false` oder nicht vorhanden ist:

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

Diese neue kompakte Darstellung wird verwendet, wenn der übergebene IO-Stream ein `IOContext`-Objekt mit der `:compact`-Eigenschaft gesetzt ist. Insbesondere ist dies der Fall, wenn Arrays mit mehreren Spalten (wo der horizontale Platz begrenzt ist) gedruckt werden:

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

Siehe die [`IOContext`](@ref) Dokumentation für eine Liste von gängigen Eigenschaften, die verwendet werden können, um das Drucken anzupassen.

## "Value types"

In Julia kannst du nicht auf einen *Wert* wie `true` oder `false` dispatchen. Du kannst jedoch auf parametrische Typen dispatchen, und Julia erlaubt es dir, "einfache Bits"-Werte (Typen, Symbole, Ganzzahlen, Fließkommazahlen, Tupel usw.) als Typparameter einzuschließen. Ein häufiges Beispiel ist der Dimensionsparameter in `Array{T,N}`, wobei `T` ein Typ ist (z. B. [`Float64`](@ref)), aber `N` ist einfach ein `Int`.

Sie können Ihre eigenen benutzerdefinierten Typen erstellen, die Werte als Parameter annehmen, und diese verwenden, um die Zustellung benutzerdefinierter Typen zu steuern. Um diese Idee zu veranschaulichen, lassen Sie uns den parametrischen Typ `Val{x}` einführen und seinen Konstruktor `Val(x) = Val{x}()`, der als übliche Methode dient, um diese Technik in Fällen zu nutzen, in denen Sie keine ausgeklügeltere Hierarchie benötigen.

[`Val`](@ref) wird definiert als:

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

Es gibt nichts Weiteres zur Implementierung von `Val` als dies. Einige Funktionen in Julias Standardbibliothek akzeptieren `Val`-Instanzen als Argumente, und Sie können es auch verwenden, um Ihre eigenen Funktionen zu schreiben. Zum Beispiel:

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

Für Konsistenz in Julia sollte der Aufruf immer eine `Val` *Instanz* übergeben, anstatt einen *Typ* zu verwenden, d.h. verwende `foo(Val(:bar))` anstelle von `foo(Val{:bar})`.

Es ist erwähnenswert, dass es extrem einfach ist, parametrische "Wert"-Typen, einschließlich `Val`, falsch zu verwenden; in ungünstigen Fällen kann es leicht passieren, dass die Leistung Ihres Codes viel *schlechter* wird. Insbesondere sollten Sie niemals tatsächlichen Code wie oben dargestellt schreiben. Für weitere Informationen über die richtigen (und falschen) Verwendungen von `Val` lesen Sie bitte [the more extensive discussion in the performance tips](@ref man-performance-value-type).

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.

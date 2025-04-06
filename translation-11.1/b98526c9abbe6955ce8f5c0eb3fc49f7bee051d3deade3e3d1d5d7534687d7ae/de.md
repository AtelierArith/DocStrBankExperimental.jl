# [Constructors](@id man-constructors)

Konstruktoren [^1] sind Funktionen, die neue Objekte erstellen – spezifisch Instanzen von [Composite Types](@ref). In Julia dienen Typobjekte auch als Konstruktionsfunktionen: Sie erstellen neue Instanzen von sich selbst, wenn sie auf ein Argument-Tuple als Funktion angewendet werden. Dies wurde bereits kurz erwähnt, als zusammengesetzte Typen eingeführt wurden. Zum Beispiel:

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

Für viele Typen ist es ausreichend, neue Objekte zu bilden, indem ihre Feldwerte zusammengebunden werden, um Instanzen zu erstellen. In einigen Fällen ist jedoch mehr Funktionalität erforderlich, wenn zusammengesetzte Objekte erstellt werden. Manchmal müssen Invarianten durch Überprüfung der Argumente oder durch deren Transformation durchgesetzt werden. [Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29), insbesondere solche, die selbstreferenziell sein können, können oft nicht sauber konstruiert werden, ohne zuerst in einem unvollständigen Zustand erstellt und dann programmatisch verändert zu werden, um vollständig zu sein, als ein separater Schritt von der Objekterstellung. Manchmal ist es einfach praktisch, Objekte mit weniger oder anderen Arten von Parametern zu konstruieren, als sie Felder haben. Julias System zur Objekterstellung behandelt all diese Fälle und mehr.

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

Ein Konstruktor ist genau wie jede andere Funktion in Julia, da sein Gesamtverhalten durch das kombinierte Verhalten seiner Methoden definiert ist. Dementsprechend können Sie die Funktionalität eines Konstruktors hinzufügen, indem Sie einfach neue Methoden definieren. Angenommen, Sie möchten eine Konstruktormethode für `Foo`-Objekte hinzufügen, die nur ein Argument annimmt und den gegebenen Wert sowohl für die Felder `bar` als auch `baz` verwendet. Das ist einfach:

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

Sie könnten auch eine Null-Argumente `Foo` Konstruktor-Methode hinzufügen, die Standardwerte für sowohl die `bar` als auch die `baz` Felder bereitstellt:

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

Hier ruft die Null-Argument-Konstruktor-Methode die Einzel-Argument-Konstruktor-Methode auf, die wiederum die automatisch bereitgestellte Zwei-Argument-Konstruktor-Methode aufruft. Aus Gründen, die gleich klar werden, werden zusätzliche Konstruktor-Methoden, die wie normale Methoden deklariert sind, als *äußere* Konstruktor-Methoden bezeichnet. Äußere Konstruktor-Methoden können nur dann eine neue Instanz erstellen, wenn sie eine andere Konstruktor-Methode aufrufen, wie die automatisch bereitgestellten Standardmethoden.

## [Inner Constructor Methods](@id man-inner-constructor-methods)

Während äußere Konstruktormethoden erfolgreich das Problem lösen, zusätzliche Hilfsmethoden zum Erstellen von Objekten bereitzustellen, adressieren sie nicht die beiden anderen Anwendungsfälle, die in der Einleitung dieses Kapitels erwähnt wurden: das Durchsetzen von Invarianten und die Ermöglichung der Konstruktion selbstreferenzieller Objekte. Für diese Probleme benötigt man *innere* Konstruktormethoden. Eine innere Konstruktormethode ist wie eine äußere Konstruktormethode, mit zwei Unterschieden:

1. Es wird innerhalb des Blocks einer Typdeklaration deklariert, anstatt wie normale Methoden außerhalb davon.
2. Es hat Zugriff auf eine spezielle lokal vorhandene Funktion namens [`new`](@ref), die Objekte des Typs des Blocks erstellt.

Zum Beispiel, nehmen wir an, man möchte einen Typ deklarieren, der ein Paar von reellen Zahlen hält, unter der Bedingung, dass die erste Zahl nicht größer als die zweite ist. Man könnte es so deklarieren:

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

Jetzt können `OrderedPair`-Objekte nur so konstruiert werden, dass `x <= y` ist:

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

Wenn der Typ als `mutable` deklariert wäre, könntest du direkt in die Feldwerte eingreifen und diese ändern, um diese Invarianz zu verletzen. Natürlich ist es schlechte Praxis, ohne Einladung mit den Interna eines Objekts herumzuspielen. Du (oder jemand anderes) kannst auch später zusätzliche äußere Konstruktormethoden bereitstellen, aber sobald ein Typ deklariert ist, gibt es keine Möglichkeit, weitere innere Konstruktormethoden hinzuzufügen. Da äußere Konstruktormethoden Objekte nur durch den Aufruf anderer Konstruktormethoden erstellen können, muss letztendlich eine innere Konstruktor aufgerufen werden, um ein Objekt zu erstellen. Dies garantiert, dass alle Objekte des deklarierten Typs durch einen Aufruf einer der mit dem Typ bereitgestellten inneren Konstruktormethoden entstehen müssen, wodurch ein gewisses Maß an Durchsetzung der Invarianten eines Typs gewährleistet wird.

Wenn eine innere Konstruktormethode definiert ist, wird keine Standardkonstruktormethode bereitgestellt: Es wird davon ausgegangen, dass Sie sich selbst mit allen benötigten inneren Konstruktoren versorgt haben. Der Standardkonstruktor entspricht dem Schreiben Ihrer eigenen inneren Konstruktormethode, die alle Felder des Objekts als Parameter entgegennimmt (eingeschränkt auf den richtigen Typ, wenn das entsprechende Feld einen Typ hat) und sie an `new` übergibt, wobei das resultierende Objekt zurückgegeben wird:

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

Diese Deklaration hat die gleiche Wirkung wie die frühere Definition des `Foo`-Typs ohne eine explizite innere Konstruktormethode. Die folgenden beiden Typen sind äquivalent – einer mit einem Standardkonstruktor, der andere mit einem expliziten Konstruktor:

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

Es ist eine gute Praxis, so wenige innere Konstruktoren wie möglich bereitzustellen: nur diejenigen, die alle Argumente explizit annehmen und wesentliche Fehlerprüfungen und Transformationen durchsetzen. Zusätzliche Komfortkonstruktoren, die Standardwerte oder Hilfstransformationen bereitstellen, sollten als äußere Konstruktoren bereitgestellt werden, die die inneren Konstruktoren aufrufen, um die Hauptarbeit zu erledigen. Diese Trennung ist typischerweise ganz natürlich.

## Incomplete Initialization

Das letzte Problem, das noch nicht angesprochen wurde, ist der Bau von selbstreferenziellen Objekten oder allgemeiner gesagt, rekursiven Datenstrukturen. Da die grundlegende Schwierigkeit möglicherweise nicht sofort offensichtlich ist, lassen Sie uns dies kurz erklären. Betrachten Sie die folgende rekursive Typdeklaration:

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

Dieser Typ mag harmlos genug erscheinen, bis man darüber nachdenkt, wie man eine Instanz davon erstellt. Wenn `a` eine Instanz von `SelfReferential` ist, kann eine zweite Instanz durch den Aufruf erstellt werden:

```julia-repl
julia> b = SelfReferential(a)
```

Aber wie konstruiert man die erste Instanz, wenn keine Instanz existiert, die als gültiger Wert für das Feld `obj` dienen kann? Die einzige Lösung besteht darin, die Erstellung einer unvollständig initialisierten Instanz von `SelfReferential` mit einem nicht zugewiesenen `obj`-Feld zuzulassen und diese unvollständige Instanz als gültigen Wert für das `obj`-Feld einer anderen Instanz zu verwenden, wie zum Beispiel sich selbst.

Um die Erstellung von unvollständig initialisierten Objekten zu ermöglichen, erlaubt Julia, dass die [`new`](@ref)-Funktion mit weniger Feldern als der Typ hat, aufgerufen wird, wobei ein Objekt mit den nicht spezifizierten Feldern uninitialisiert zurückgegeben wird. Die innere Konstruktormethode kann dann das unvollständige Objekt verwenden und seine Initialisierung abschließen, bevor es zurückgegeben wird. Hier ist zum Beispiel ein weiterer Versuch, den `SelfReferential`-Typ zu definieren, diesmal mit einem inneren Konstruktor ohne Argumente, der Instanzen zurückgibt, deren `obj`-Felder auf sich selbst zeigen:

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

Wir können überprüfen, dass dieser Konstruktor funktioniert und Objekte erstellt, die tatsächlich selbstreferenziell sind:

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

Obwohl es im Allgemeinen eine gute Idee ist, ein vollständig initialisiertes Objekt aus einem inneren Konstruktor zurückzugeben, ist es möglich, unvollständig initialisierte Objekte zurückzugeben:

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

Während es Ihnen erlaubt ist, Objekte mit nicht initialisierten Feldern zu erstellen, ist jeder Zugriff auf eine nicht initialisierte Referenz ein sofortiger Fehler:

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

Dies vermeidet die Notwendigkeit, ständig nach `null`-Werten zu suchen. Allerdings sind nicht alle Objektfelder Referenzen. Julia betrachtet einige Typen als "einfache Daten", was bedeutet, dass alle ihre Daten selbstenthalten sind und keine anderen Objekte referenzieren. Die einfachen Datentypen bestehen aus primitiven Typen (z. B. `Int`) und unveränderlichen Strukturen anderer einfacher Datentypen (siehe auch: [`isbits`](@ref), [`isbitstype`](@ref)). Der anfängliche Inhalt eines einfachen Datentyps ist undefiniert:

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

Arrays von einfachen Datentypen zeigen dasselbe Verhalten.

Sie können unvollständige Objekte von inneren Konstruktoren an andere Funktionen übergeben, um deren Vollständigkeit zu delegieren:

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

Wie bei unvollständigen Objekten, die von Konstruktoren zurückgegeben werden, wird ein Fehler sofort ausgelöst, wenn `complete_me` oder einer seiner Aufrufer versucht, auf das `data`-Feld des `Lazy`-Objekts zuzugreifen, bevor es initialisiert wurde.

## Parametric Constructors

Parametrische Typen fügen der Geschichte der Konstruktoren einige Feinheiten hinzu. Erinnern Sie sich an [Parametric Types](@ref), dass Instanzen parametrischer zusammengesetzter Typen standardmäßig entweder mit ausdrücklich angegebenen Typparametern oder mit Typparametern, die durch die Typen der Argumente, die dem Konstruktor übergeben werden, impliziert werden, konstruiert werden können. Hier sind einige Beispiele:

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

Wie Sie sehen können, werden bei Konstruktoraufrufen mit expliziten Typparametern die Argumente in die impliziten Feldtypen konvertiert: `Point{Int64}(1,2)` funktioniert, aber `Point{Int64}(1.0,2.5)` löst einen [`InexactError`](@ref) aus, wenn `2.5` in [`Int64`](@ref) konvertiert wird. Wenn der Typ durch die Argumente des Konstruktoraufrufs impliziert wird, wie in `Point(1,2)`, müssen die Typen der Argumente übereinstimmen – andernfalls kann das `T` nicht bestimmt werden – aber jedes Paar von reellen Argumenten mit übereinstimmendem Typ kann dem generischen `Point`-Konstruktor übergeben werden.

Was hier wirklich vor sich geht, ist, dass `Point`, `Point{Float64}` und `Point{Int64}` allesamt verschiedene Konstruktorfunktionen sind. Tatsächlich ist `Point{T}` eine eigene Konstruktorfunktion für jeden Typ `T`. Ohne ausdrücklich bereitgestellte innere Konstruktoren stellt die Deklaration des zusammengesetzten Typs `Point{T<:Real}` automatisch einen inneren Konstruktor `Point{T}` für jeden möglichen Typ `T<:Real` bereit, der sich genau wie nicht-parametrische Standard-Innenkonstruktoren verhält. Es wird auch einen einzigen allgemeinen äußeren `Point`-Konstruktor bereitgestellt, der Paare von reellen Argumenten entgegennimmt, die vom gleichen Typ sein müssen. Diese automatische Bereitstellung von Konstruktoren entspricht der folgenden expliziten Deklaration:

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

Beachten Sie, dass jede Definition wie der Aufruf eines Konstruktors aussieht, den sie behandelt. Der Aufruf `Point{Int64}(1,2)` ruft die Definition `Point{T}(x,y)` innerhalb des `struct`-Blocks auf. Die äußere Konstruktordeklaration hingegen definiert eine Methode für den allgemeinen `Point`-Konstruktor, die nur für Paare von Werten desselben realen Typs gilt. Diese Deklaration ermöglicht es, Konstruktorausführungen ohne explizite Typparameter, wie `Point(1,2)` und `Point(1.0,2.5)`, zu verwenden. Da die Methodendeklaration die Argumente auf denselben Typ beschränkt, führen Aufrufe wie `Point(1,2.5)`, bei denen die Argumente unterschiedliche Typen haben, zu "keine Methode"-Fehlern.

Angenommen, wir möchten den Konstruktoraufruf `Point(1,2.5)` zum Funktionieren bringen, indem wir den ganzzahligen Wert `1` in den Gleitkommawert `1.0` "fördern". Der einfachste Weg, dies zu erreichen, besteht darin, die folgende zusätzliche äußere Konstruktormethode zu definieren:

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

Diese Methode verwendet die [`convert`](@ref) Funktion, um `x` explizit in [`Float64`](@ref) zu konvertieren und delegiert dann die Konstruktion an den allgemeinen Konstruktor für den Fall, dass beide Argumente `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566` sind. Mit dieser Methodendefinition wird das, was zuvor ein [`MethodError`](@ref) war, jetzt erfolgreich zu einem Punkt vom Typ `Point{Float64}` erstellt:

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

Allerdings funktionieren andere ähnliche Anrufe immer noch nicht:

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

For a more general way to make all such calls work sensibly, see [Conversion and Promotion](@ref conversion-and-promotion). At the risk of spoiling the suspense, we can reveal here that all it takes is the following outer method definition to make all calls to the general `Point` constructor work as one would expect:

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

Die `promote`-Funktion konvertiert alle ihre Argumente in einen gemeinsamen Typ – in diesem Fall [`Float64`](@ref). Mit dieser Methodendefinition fördert der `Point`-Konstruktor seine Argumente auf die gleiche Weise, wie es numerische Operatoren wie [`+`](@ref) tun, und funktioniert für alle Arten von reellen Zahlen:

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

So sind die impliziten Typ-Parameter-Konstruktoren, die standardmäßig in Julia bereitgestellt werden, zwar recht streng, aber es ist möglich, sie auf eine entspannendere, aber sinnvolle Weise zu gestalten. Darüber hinaus können Konstruktoren die gesamte Leistungsfähigkeit des Typsystems, der Methoden und des mehrfachen Dispatchs nutzen, sodass die Definition komplexer Verhaltensweisen in der Regel recht einfach ist.

## Case Study: Rational

Vielleicht ist der beste Weg, all diese Teile zusammenzubringen, ein reales Beispiel für einen parametrischen zusammengesetzten Typ und seine Konstruktor-Methoden zu präsentieren. Zu diesem Zweck implementieren wir unseren eigenen rationalen Zahlentyp `OurRational`, ähnlich dem eingebauten [`Rational`](@ref) Typ in Julia, definiert in [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl):

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

Die erste Zeile – `struct OurRational{T<:Integer} <: Real` – erklärt, dass `OurRational` einen Typparameter eines ganzzahligen Typs annimmt und selbst ein reeller Typ ist. Die Felddeklarationen `num::T` und `den::T` zeigen an, dass die in einem `OurRational{T}`-Objekt gehaltenen Daten ein Paar von Ganzzahlen des Typs `T` sind, wobei eine den Zähler des rationalen Wertes und die andere den Nenner darstellt.

Jetzt wird es interessant. `OurRational` hat eine einzige innere Konstruktormethode, die überprüft, dass `num` und `den` nicht beide null sind und sicherstellt, dass jeder Bruch in "kürzester Form" mit einem nicht-negativen Nenner konstruiert wird. Dies wird erreicht, indem zuerst die Vorzeichen von Zähler und Nenner umgekehrt werden, wenn der Nenner negativ ist. Dann werden beide durch ihren größten gemeinsamen Teiler (der `gcd` gibt immer eine nicht-negative Zahl zurück, unabhängig vom Vorzeichen seiner Argumente) geteilt. Da dies der einzige innere Konstruktor für `OurRational` ist, können wir sicher sein, dass `OurRational`-Objekte immer in dieser normalisierten Form konstruiert werden.

`OurRational` bietet auch mehrere äußere Konstruktormethoden zur Vereinfachung. Der erste ist der "Standard"-Allgemeinkonstruktor, der den Typparameter `T` aus dem Typ des Zählers und des Nenners ableitet, wenn sie denselben Typ haben. Der zweite gilt, wenn die angegebenen Zähler- und Nennerwerte unterschiedliche Typen haben: Er hebt sie auf einen gemeinsamen Typ an und delegiert dann die Konstruktion an den äußeren Konstruktor für Argumente des übereinstimmenden Typs. Der dritte äußere Konstruktor verwandelt Ganzzahlen in Brüche, indem er einen Wert von `1` als Nenner bereitstellt.

Nach den Definitionen des äußeren Konstruktors haben wir eine Reihe von Methoden für den `⊘`-Operator definiert, der eine Syntax zum Schreiben von rationalen Zahlen bereitstellt (z. B. `1 ⊘ 2`). Julias `Rational`-Typ verwendet den [`//`](@ref)-Operator zu diesem Zweck. Vor diesen Definitionen ist `⊘` ein völlig undefinierter Operator mit nur Syntax und keiner Bedeutung. Danach verhält er sich genau wie in [Rational Numbers](@ref) beschrieben – sein gesamtes Verhalten ist in diesen wenigen Zeilen definiert. Beachten Sie, dass die infix Verwendung von `⊘` funktioniert, weil Julia eine Menge von Symbolen hat, die als infix Operatoren erkannt werden. Die erste und grundlegendste Definition macht einfach, dass `a ⊘ b` ein `OurRational` konstruiert, indem der `OurRational`-Konstruktor auf `a` und `b` angewendet wird, wenn sie ganze Zahlen sind. Wenn einer der Operanden von `⊘` bereits eine rationale Zahl ist, konstruieren wir eine neue rationale Zahl für das resultierende Verhältnis etwas anders; dieses Verhalten ist tatsächlich identisch mit der Division einer rationalen Zahl durch eine ganze Zahl. Schließlich erzeugt die Anwendung von `⊘` auf komplexe ganzzahlige Werte eine Instanz von `Complex{<:OurRational}` – eine komplexe Zahl, deren reelle und imaginäre Teile rational sind:

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

Somit gibt der `⊘`-Operator normalerweise eine Instanz von `OurRational` zurück. Wenn jedoch einer seiner Argumente komplexe Ganzzahlen sind, gibt er stattdessen eine Instanz von `Complex{<:OurRational}` zurück. Der interessierte Leser sollte in Betracht ziehen, den Rest von [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) zu durchstöbern: Es ist kurz, eigenständig und implementiert einen gesamten grundlegenden Julia-Typ.

## Outer-only constructors

Wie wir gesehen haben, hat ein typischer parametrischer Typ innere Konstruktoren, die aufgerufen werden, wenn die Typparameter bekannt sind; z.B. gelten sie für `Point{Int}`, aber nicht für `Point`. Optional können äußere Konstruktoren hinzugefügt werden, die die Typparameter automatisch bestimmen, zum Beispiel durch die Konstruktion eines `Point{Int}` aus dem Aufruf `Point(1,2)`. Äußere Konstruktoren rufen innere Konstruktoren auf, um tatsächlich Instanzen zu erstellen. In einigen Fällen möchte man jedoch lieber keine inneren Konstruktoren bereitstellen, sodass spezifische Typparameter nicht manuell angefordert werden können.

Zum Beispiel, sagen wir, wir definieren einen Typ, der einen Vektor speichert, zusammen mit einer genauen Darstellung seiner Summe:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

Das Problem ist, dass wir möchten, dass `S` ein größerer Typ als `T` ist, damit wir viele Elemente mit weniger Informationsverlust summieren können. Zum Beispiel, wenn `T` [`Int32`](@ref) ist, möchten wir, dass `S` [`Int64`](@ref) ist. Daher möchten wir eine Schnittstelle vermeiden, die es dem Benutzer ermöglicht, Instanzen des Typs `SummedArray{Int32,Int32}` zu erstellen. Eine Möglichkeit, dies zu tun, besteht darin, einen Konstruktor nur für `SummedArray` bereitzustellen, aber innerhalb des `struct`-Definitionsblocks die Generierung von Standardkonstruktoren zu unterdrücken:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

Dieser Konstruktor wird mit der Syntax `SummedArray(a)` aufgerufen. Die Syntax `new{T,S}` ermöglicht es, Parameter für den zu konstruierenden Typ anzugeben, d.h. dieser Aufruf gibt ein `SummedArray{T,S}` zurück. `new{T,S}` kann in jeder Konstruktordefinition verwendet werden, aber zur Vereinfachung werden die Parameter für `new{}` automatisch aus dem zu konstruierenden Typ abgeleitet, wenn dies möglich ist.

## Constructors are just callable objects

Ein Objekt beliebigen Typs kann [made callable](@ref "Function-like objects") sein, indem eine Methode definiert wird. Dazu gehören Typen, d.h. Objekte des Typs [`Type`](@ref); und Konstruktoren können tatsächlich als einfach aufrufbare Typobjekte betrachtet werden. Zum Beispiel gibt es viele Methoden, die auf `Bool` und verschiedenen Supertypen davon definiert sind:

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

Die übliche Konstruktor-Syntax ist genau gleichwertig zur funktionsähnlichen Objektsyntax, sodass der Versuch, eine Methode mit jeder Syntax zu definieren, dazu führen wird, dass die erste Methode von der nächsten überschrieben wird:

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```

# Style Guide

Die folgenden Abschnitte erklären einige Aspekte des idiomatischen Julia-Coding-Stils. Keine dieser Regeln ist absolut; sie sind nur Vorschläge, um Ihnen zu helfen, sich mit der Sprache vertraut zu machen und um Ihnen bei der Auswahl zwischen alternativen Designs zu helfen.

## Indentation

Verwenden Sie 4 Leerzeichen pro Einrückungsstufe.

## Write functions, not just scripts

Das Schreiben von Code als eine Reihe von Schritten auf der obersten Ebene ist eine schnelle Möglichkeit, um mit der Lösung eines Problems zu beginnen, aber Sie sollten versuchen, ein Programm so schnell wie möglich in Funktionen zu unterteilen. Funktionen sind wiederverwendbarer und testbarer und verdeutlichen, welche Schritte unternommen werden und was deren Eingaben und Ausgaben sind. Darüber hinaus neigt der Code innerhalb von Funktionen dazu, viel schneller zu laufen als Code auf oberster Ebene, aufgrund der Funktionsweise des Compilers von Julia.

Es ist auch wichtig zu betonen, dass Funktionen Argumente entgegennehmen sollten, anstatt direkt auf globale Variablen zuzugreifen (abgesehen von Konstanten wie [`pi`](@ref)).

## Avoid writing overly-specific types

Der Code sollte so generisch wie möglich sein. Anstatt zu schreiben:

```julia
Complex{Float64}(x)
```

es ist besser, verfügbare generische Funktionen zu verwenden:

```julia
complex(float(x))
```

Die zweite Version wird `x` in einen geeigneten Typ umwandeln, anstatt immer denselben Typ zu verwenden.

Dieser Stilpunkt ist besonders relevant für Funktionsargumente. Zum Beispiel, deklariere ein Argument nicht als Typ `Int` oder [`Int32`](@ref), wenn es wirklich jede ganze Zahl sein könnte, ausgedrückt mit dem abstrakten Typ [`Integer`](@ref). Tatsächlich kannst du in vielen Fällen den Argumenttyp ganz weglassen, es sei denn, er ist notwendig, um von anderen Methodendefinitionen zu unterscheiden, da ein [`MethodError`](@ref) sowieso ausgelöst wird, wenn ein Typ übergeben wird, der keine der erforderlichen Operationen unterstützt. (Dies ist bekannt als [duck typing](https://en.wikipedia.org/wiki/Duck_typing).)

Zum Beispiel, betrachten Sie die folgenden Definitionen einer Funktion `addone`, die eins zu ihrem Argument zurückgibt:

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

Die letzte Definition von `addone` behandelt jeden Typ, der [`oneunit`](@ref) unterstützt (was 1 im gleichen Typ wie `x` zurückgibt, was unerwünschte Typförderung vermeidet) und die [`+`](@ref)-Funktion mit diesen Argumenten. Das Wichtigste, was man erkennen sollte, ist, dass es *keine Leistungseinbußen* gibt, wenn man *nur* das allgemeine `addone(x) = x + oneunit(x)` definiert, da Julia automatisch spezialisierte Versionen nach Bedarf kompiliert. Zum Beispiel, beim ersten Aufruf von `addone(12)` wird Julia automatisch eine spezialisierte `addone`-Funktion für `x::Int`-Argumente kompilieren, wobei der Aufruf von `oneunit` durch seinen inlined Wert `1` ersetzt wird. Daher sind die ersten drei Definitionen von `addone` oben vollständig redundant mit der vierten Definition.

## Handle excess argument diversity in the caller

Stattdessen:

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

benutzen:

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

Dies ist der bessere Stil, weil `foo` nicht wirklich Zahlen aller Typen akzeptiert; es benötigt tatsächlich `Int`s.

Ein Problem hierbei ist, dass wenn eine Funktion von Natur aus Ganzzahlen erfordert, es besser sein könnte, den Aufrufer zu zwingen zu entscheiden, wie Nicht-Ganzzahlen konvertiert werden sollen (z. B. Abrunden oder Aufrunden). Ein weiteres Problem ist, dass die Deklaration spezifischerer Typen mehr "Raum" für zukünftige Methodendefinitionen lässt.

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

Stattdessen:

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

benutzen:

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Base verwendet diese Konvention durchgehend und enthält Beispiele für Funktionen mit sowohl kopierenden als auch modifizierenden Formen (z. B. [`sort`](@ref) und [`sort!`](@ref)), sowie andere, die nur modifizieren (z. B. [`push!`](@ref), [`pop!`](@ref), [`splice!`](@ref)). Es ist typisch, dass solche Funktionen auch das modifizierte Array zur Bequemlichkeit zurückgeben.

Funktionen, die mit IO oder der Verwendung von Zufallszahlengeneratoren (RNG) zu tun haben, sind bemerkenswerte Ausnahmen: Da diese Funktionen fast immer das IO oder den RNG mutieren müssen, werden Funktionen, die mit `!` enden, verwendet, um eine Mutation *außer* der Mutation des IO oder dem Fortschreiten des RNG-Zustands zu kennzeichnen. Zum Beispiel mutiert `rand(x)` den RNG, während `rand!(x)` sowohl den RNG als auch `x` mutiert; ähnlich mutiert `read(io)` `io`, während `read!(io, x)` beide Argumente mutiert.

## Avoid strange type `Union`s

Typen wie `Union{Function,AbstractString}` sind oft ein Zeichen dafür, dass das Design etwas klarer sein könnte.

## Avoid elaborate container types

Es ist normalerweise nicht sehr hilfreich, Arrays wie die folgenden zu konstruieren:

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

In diesem Fall ist `Vector{Any}(undef, n)` besser. Es ist auch hilfreicher für den Compiler, spezifische Verwendungen zu annotieren (z. B. `a[i]::Int`), als zu versuchen, viele Alternativen in einen Typ zu packen.

## Prefer exported methods over direct field access

Idiomatic Julia-Code sollte im Allgemeinen die exportierten Methoden eines Moduls als Schnittstelle zu seinen Typen behandeln. Die Felder eines Objekts werden im Allgemeinen als Implementierungsdetails betrachtet, und der Benutzer-Code sollte nur dann direkt auf sie zugreifen, wenn dies als Teil der API angegeben ist. Dies hat mehrere Vorteile:

  * Paketentwickler sind freier, die Implementierung zu ändern, ohne den Benutzercode zu brechen.
  * Methoden können an höherwertige Konstrukte wie [`map`](@ref) (z. B. `map(imag, zs)`) übergeben werden, anstatt `[z.im for z in zs]`.
  * Methoden können auf abstrakten Typen definiert werden.
  * Methoden können eine konzeptionelle Operation beschreiben, die über verschiedene Typen hinweg geteilt werden kann (z. B. `real(z)` funktioniert mit komplexen Zahlen oder Quaternionen).

Julias Dispatch-System fördert diesen Stil, da `play(x::MyType)` nur die `play`-Methode für diesen bestimmten Typ definiert und anderen Typen ihre eigene Implementierung überlässt.

Ähnlich sind nicht exportierte Funktionen typischerweise intern und Änderungen unterworfen, es sei denn, die Dokumentation besagt etwas anderes. Namen erhalten manchmal ein `_`-Präfix (oder -Suffix), um weiter zu suggerieren, dass etwas "intern" oder ein Implementierungsdetail ist, aber es ist keine Regel.

Gegenbeispiele zu dieser Regel sind [`NamedTuple`](@ref), [`RegexMatch`](@ref match), [`StatStruct`](@ref stat).

## Use naming conventions consistent with Julia `base/`

  * Module- und Typnamen verwenden Großschreibung und CamelCase: `module SparseArrays`, `struct UnitRange`.
  * funktionen*sind*kleinbuchstaben([`maximum`](@ref), [`convert`](@ref)) und, wenn*lesbar, mit*mehreren*wörtern*zusammengedrückt([`isequal`](@ref), [`haskey`](@ref)). Wenn*nötig, verwende*unterstriche*als*worttrennzeichen. Unterstriche*werden*auch*verwendet, um*eine*kombination*von*konzepten*anzuzeigen([`remotecall_fetch`](@ref) als*effizientere*implementierung*von `fetch(remotecall(...))`) oder*als_modifikatoren.
  * Funktionen, die mindestens eines ihrer Argumente verändern, enden mit `!`.
  * Kürze wird geschätzt, aber Abkürzungen sollten vermieden werden ([`indexin`](@ref) anstelle von `indxin`), da es schwierig wird, sich zu erinnern, ob und wie bestimmte Wörter abgekürzt werden.

Wenn ein Funktionsname mehrere Wörter erfordert, überlegen Sie, ob er möglicherweise mehr als ein Konzept darstellt und besser in Teile aufgeteilt werden könnte.

## Write functions with argument ordering similar to Julia Base

Als allgemeine Regel verwendet die Base-Bibliothek die folgende Reihenfolge der Argumente für Funktionen, sofern zutreffend:

1. **Funktionsargument**. Das Setzen eines Funktionsarguments an die erste Stelle ermöglicht die Verwendung von [`do`](@ref)-Blöcken zum Übergeben mehrzeiliger anonymer Funktionen.
2. **I/O-Stream**. Das Festlegen des `IO`-Objekts zuerst ermöglicht das Übergeben der Funktion an Funktionen wie [`sprint`](@ref), z.B. `sprint(show, x)`.
3. **Eingabe wird verändert**. Zum Beispiel, in [`fill!(x, v)`](@ref fill!), ist `x` das Objekt, das verändert wird und es erscheint vor dem Wert, der in `x` eingefügt werden soll.
4. **Typ**. Ein Typ zu übergeben bedeutet typischerweise, dass die Ausgabe den angegebenen Typ haben wird. In [`parse(Int, "1")`](@ref parse) kommt der Typ vor dem zu parsenden String. Es gibt viele solcher Beispiele, bei denen der Typ zuerst erscheint, aber es ist nützlich zu beachten, dass in [`read(io, String)`](@ref read) das `IO`-Argument vor dem Typ erscheint, was mit der hier skizzierten Reihenfolge übereinstimmt.
5. **Eingabe wird nicht verändert**. In `fill!(x, v)` wird `v` *nicht* verändert und es kommt nach `x`.
6. **Schlüssel**. Für assoziative Sammlungen ist dies der Schlüssel des Schlüssel-Wert-Paares. Für andere indizierte Sammlungen ist dies der Index.
7. **Wert**. Für assoziative Sammlungen ist dies der Wert des Schlüssel-Wert-Paares. In Fällen wie [`fill!(x, v)`](@ref fill!) ist dies `v`.
8. **Alles andere**. Alle anderen Argumente.
9. **Varargs**. Dies bezieht sich auf Argumente, die am Ende eines Funktionsaufrufs unbegrenzt aufgelistet werden können. Zum Beispiel können die Dimensionen in `Matrix{T}(undef, dims)` als [`Tuple`](@ref) angegeben werden, z.B. `Matrix{T}(undef, (1,2))`, oder als [`Vararg`](@ref), z.B. `Matrix{T}(undef, 1, 2)`.
10. **Schlüsselwörter**. In Julia müssen Schlüsselwörter in Funktionsdefinitionen ohnehin zuletzt kommen; sie werden hier der Vollständigkeit halber aufgeführt.

Die überwiegende Mehrheit der Funktionen wird nicht jede Art von Argumenten verwenden, die oben aufgeführt sind; die Zahlen geben lediglich die Priorität an, die für alle anwendbaren Argumente einer Funktion verwendet werden sollte.

Es gibt natürlich einige Ausnahmen. Zum Beispiel sollte in [`convert`](@ref) der Typ immer zuerst kommen. In [`setindex!`](@ref) kommt der Wert vor den Indizes, damit die Indizes als varargs bereitgestellt werden können.

Beim Entwerfen von APIs ist es wahrscheinlich, dass die Einhaltung dieser allgemeinen Reihenfolge so weit wie möglich den Benutzern Ihrer Funktionen ein konsistenteres Erlebnis bietet.

## Don't overuse try-catch

Es ist besser, Fehler zu vermeiden, als sich darauf zu verlassen, sie zu erkennen.

## Don't parenthesize conditions

Julia benötigt keine Klammern um Bedingungen in `if` und `while`. Schreibe:

```julia
if a == b
```

stattdessen:

```julia
if (a == b)
```

## Don't overuse `...`

Das Verketten von Funktionsargumenten kann süchtig machen. Anstelle von `[a..., b...]` verwenden Sie einfach `[a; b]`, das bereits Arrays zusammenfügt. [`collect(a)`](@ref) ist besser als `[a...]`, aber da `a` bereits iterierbar ist, ist es oft sogar besser, es in Ruhe zu lassen und nicht in ein Array umzuwandeln.

## Ensure constructors return an instance of their own type

When a method `T(x)` is called on a type `T`, it is generally expected to return a value of type T. Defining a [constructor](@ref man-constructors) that returns an unexpected type can lead to confusing and unpredictable behavior:

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

Um die Klarheit des Codes zu gewährleisten und die Typkonsistenz sicherzustellen, sollten Konstruktoren immer so gestaltet werden, dass sie eine Instanz des Typs zurückgeben, den sie konstruieren sollen.

## Don't use unnecessary static parameters

Eine Funktionssignatur:

```julia
foo(x::T) where {T<:Real} = ...
```

sollte geschrieben werden als:

```julia
foo(x::Real) = ...
```

stattdessen, insbesondere wenn `T` im Funktionskörper nicht verwendet wird. Selbst wenn `T` verwendet wird, kann es bei Bedarf durch [`typeof(x)`](@ref) ersetzt werden. Es gibt keinen Leistungsunterschied. Beachten Sie, dass dies keine allgemeine Warnung gegen statische Parameter ist, sondern nur gegen Verwendungen, bei denen sie nicht benötigt werden.

Beachten Sie auch, dass Containertypen möglicherweise Typparameter in Funktionsaufrufen benötigen. Weitere Informationen finden Sie im FAQ [Avoid fields with abstract containers](@ref).

## Avoid confusion about whether something is an instance or a type

Sätze von Definitionen wie die folgenden sind verwirrend:

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

Entscheiden Sie, ob das betreffende Konzept als `MyType` oder `MyType()` geschrieben wird, und halten Sie sich daran.

Der bevorzugte Stil ist es, standardmäßig Instanzen zu verwenden und nur dann Methoden hinzuzufügen, die `Type{MyType}` betreffen, wenn sie notwendig werden, um einige Probleme zu lösen.

Wenn ein Typ effektiv eine Enumeration ist, sollte er als ein einzelner (idealerweise unveränderlicher Struktur- oder primitiver) Typ definiert werden, wobei die Enumerationswerte Instanzen davon sind. Konstruktoren und Konvertierungen können überprüfen, ob Werte gültig sind. Dieses Design wird bevorzugt, anstatt die Enumeration als abstrakten Typ zu gestalten, wobei die "Werte" Untertypen sind.

## Don't overuse macros

Sei dir bewusst, wann ein Makro wirklich eine Funktion sein könnte.

Das Aufrufen von [`eval`](@ref) innerhalb eines Makros ist ein besonders gefährliches Warnsignal; es bedeutet, dass das Makro nur funktioniert, wenn es auf der obersten Ebene aufgerufen wird. Wenn ein solches Makro stattdessen als Funktion geschrieben wird, hat es natürlich Zugriff auf die zur Laufzeit benötigten Werte.

## Don't expose unsafe operations at the interface level

Wenn Sie einen Typ haben, der einen nativen Zeiger verwendet:

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

Bitte schreiben Sie keine Definitionen wie die folgende:

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

Das Problem ist, dass Benutzer dieses Typs `x[i]` schreiben können, ohne zu erkennen, dass die Operation unsicher ist, und dann anfällig für Speicherfehler werden.

Eine solche Funktion sollte entweder die Operation überprüfen, um sicherzustellen, dass sie sicher ist, oder `unsafe` irgendwo in ihrem Namen haben, um die Aufrufer zu warnen.

## Don't overload methods of base container types

Es ist möglich, Definitionen wie die folgenden zu schreiben:

```julia
show(io::IO, v::Vector{MyType}) = ...
```

Dies würde eine benutzerdefinierte Anzeige von Vektoren mit einem bestimmten neuen Elementtyp ermöglichen. Auch wenn es verlockend ist, sollte dies vermieden werden. Das Problem ist, dass die Benutzer erwarten, dass ein bekannter Typ wie `Vector()` sich auf eine bestimmte Weise verhält, und eine übermäßige Anpassung seines Verhaltens kann es schwieriger machen, damit zu arbeiten.

## [Avoid type piracy](@id avoid-type-piracy)

"Typenpiraterie" bezieht sich auf die Praxis, Methoden in Base oder anderen Paketen für Typen zu erweitern oder neu zu definieren, die Sie nicht definiert haben. In extremen Fällen können Sie Julia zum Absturz bringen (z. B. wenn Ihre Methoden-Erweiterung oder -Neudefinition ungültige Eingaben an einen `ccall` übergibt). Typenpiraterie kann das Nachdenken über Code komplizieren und kann Inkompatibilitäten einführen, die schwer vorherzusagen und zu diagnostizieren sind.

Als Beispiel, nehmen wir an, Sie möchten die Multiplikation von Symbolen in einem Modul definieren:

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

Das Problem ist, dass jetzt jedes andere Modul, das `Base.*` verwendet, auch diese Definition sehen wird. Da `Symbol` in Base definiert ist und von anderen Modulen verwendet wird, kann dies das Verhalten von nicht verwandtem Code unerwartet ändern. Es gibt mehrere Alternativen, einschließlich der Verwendung eines anderen Funktionsnamens oder der Einbettung der `Symbol`s in einen anderen Typ, den Sie definieren.

Manchmal können gekoppelte Pakete Typenpiraterie betreiben, um Funktionen von Definitionen zu trennen, insbesondere wenn die Pakete von kooperierenden Autoren entworfen wurden und die Definitionen wiederverwendbar sind. Zum Beispiel könnte ein Paket einige Typen bereitstellen, die nützlich für die Arbeit mit Farben sind; ein anderes Paket könnte Methoden für diese Typen definieren, die Konversionen zwischen Farbmodellen ermöglichen. Ein weiteres Beispiel könnte ein Paket sein, das als dünner Wrapper für einen C-Code fungiert, den ein anderes Paket dann piratieren könnte, um eine höherstufige, Julia-freundliche API zu implementieren.

## Be careful with type equality

Sie möchten im Allgemeinen [`isa`](@ref) und [`<:`](@ref) zum Testen von Typen verwenden, nicht `==`. Der Vergleich von Typen auf exakte Gleichheit macht normalerweise nur Sinn, wenn man mit einem bekannten konkreten Typ vergleicht (z. B. `T == Float64`), oder wenn Sie *wirklich, wirklich* wissen, was Sie tun.

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

Da höhere Funktionen oft mit anonymen Funktionen aufgerufen werden, ist es leicht zu schließen, dass dies wünschenswert oder sogar notwendig ist. Aber jede Funktion kann direkt übergeben werden, ohne in einer anonymen Funktion "eingewickelt" zu werden. Anstatt `map(x->f(x), a)` zu schreiben, schreibe [`map(f, a)`](@ref).

## Avoid using floats for numeric literals in generic code when possible

Wenn Sie generischen Code schreiben, der mit Zahlen arbeitet und der voraussichtlich mit vielen verschiedenen numerischen Typ-Argumenten ausgeführt wird, versuchen Sie, Literale eines numerischen Typs zu verwenden, der die Argumente durch Promotion so wenig wie möglich beeinflusst.

Zum Beispiel,

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

während

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

Wie Sie sehen können, hat die zweite Version, in der wir ein `Int`-Literal verwendet haben, den Typ des Eingabearguments beibehalten, während die erste dies nicht tat. Das liegt daran, dass z.B. `promote_type(Int, Float64) == Float64` ist, und die Promotion erfolgt mit der Multiplikation. Ähnlich sind [`Rational`](@ref) Literale weniger typstörend als [`Float64`](@ref) Literale, aber störender als `Int`s:

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

Verwenden Sie daher `Int` Literale, wenn möglich, und `Rational{Int}` für literale Nicht-Ganzzahlen, um die Verwendung Ihres Codes zu erleichtern.

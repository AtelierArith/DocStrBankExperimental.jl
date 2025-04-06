# [Scoped Values](@id scoped-values)

Scoped-Werte bieten eine Implementierung von dynamischem Scoping in Julia.

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables) ist das Standardverhalten in Julia. Unter lexikalischer Bindung wird der Geltungsbereich einer Variablen durch die lexikalische (textuelle) Struktur eines Programms bestimmt. Unter dynamischer Bindung wird eine Variable an den zuletzt zugewiesenen Wert während der Programmausführung gebunden.


Der Zustand eines Scoped-Werts hängt vom Ausführungspfad des Programms ab. Das bedeutet, dass Sie für einen Scoped-Wert möglicherweise mehrere unterschiedliche Werte gleichzeitig beobachten können.

!!! compat "Julia 1.11"
    Scoped-Werte wurden in Julia 1.11 eingeführt. In Julia 1.8+ ist eine kompatible Implementierung im Paket ScopedValues.jl verfügbar.


In seiner einfachsten Form können Sie ein [`ScopedValue`](@ref Base.ScopedValues.ScopedValue) mit einem Standardwert erstellen und dann [`with`](@ref Base.ScopedValues.with) oder [`@with`](@ref Base.ScopedValues.@with) verwenden, um einen neuen dynamischen Geltungsbereich zu betreten. Der neue Geltungsbereich erbt alle Werte aus dem übergeordneten Geltungsbereich (und rekursiv aus allen äußeren Geltungsbereichen), wobei der bereitgestellte Geltungswert Vorrang vor vorherigen Definitionen hat.

Lass uns zunächst ein Beispiel für **lexikalischen** Scope betrachten. Eine `let`-Anweisung beginnt einen neuen lexikalischen Scope, innerhalb dessen die äußere Definition von `x` von ihrer inneren Definition überschattet wird.

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

Im folgenden Beispiel bezieht sich die Variable `x` im Körper von `f` auf das `x`, das im globalen Geltungsbereich definiert ist, und das Betreten eines `let`-Geltungsbereichs ändert nicht den Wert, den `f` beobachtet.

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

Jetzt können wir mit einem `ScopedValue` **dynamisches** Scoping verwenden.

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

Beachten Sie, dass der beobachtete Wert des `ScopedValue` von dem Ausführungspfad des Programms abhängt.

Es macht oft Sinn, eine `const`-Variable zu verwenden, um auf einen Scoped-Wert zu verweisen, und Sie können den Wert mehrerer `ScopedValue`s mit einem einzigen Aufruf von `with` festlegen.

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues` bietet eine Makroversion von `with`. Der Ausdruck `@with var=>val expr` bewertet `expr` in einem neuen dynamischen Gültigkeitsbereich mit `var`, das auf `val` gesetzt ist. `@with var=>val expr` ist äquivalent zu `with(var=>val) do expr end`. Allerdings erfordert `with` einen Null-Argument-Closure oder eine Funktion, was zu einem zusätzlichen Aufrufrahmen führt. Als Beispiel betrachten wir die folgende Funktion `f`:

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

Wenn Sie `f` in einem dynamischen Geltungsbereich mit `a`, das auf `2` gesetzt ist, ausführen möchten, können Sie `with` verwenden:

```julia
with(() -> f(10), a=>2)
```

Allerdings erfordert dies, dass `f` in eine Null-Argument-Funktion gewickelt wird. Wenn Sie den zusätzlichen Aufrufrahmen vermeiden möchten, können Sie das `@with`-Makro verwenden:

```julia
@with a=>2 f(10)
```

!!! note
    Dynamische Scopes werden von [`Task`](@ref) zum Zeitpunkt der Aufgabenerstellung geerbt. Dynamische Scopes werden **nicht** durch `Distributed.jl`-Operationen propagiert.


Im folgenden Beispiel öffnen wir einen neuen dynamischen Geltungsbereich, bevor wir eine Aufgabe starten. Die übergeordnete Aufgabe und die beiden untergeordneten Aufgaben beobachten gleichzeitig unabhängige Werte desselben Geltungswerts.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

Scoped-Werte sind konstant innerhalb eines Geltungsbereichs, aber Sie können veränderlichen Zustand in einem Scoped-Wert speichern. Denken Sie nur daran, dass die üblichen Vorbehalte für globale Variablen im Kontext der nebenläufigen Programmierung gelten.

Vorsicht ist auch geboten, wenn man Referenzen auf veränderlichen Zustand in bereichsspezifischen Werten speichert. Möglicherweise möchten Sie explizit [unshare mutable state](@ref unshare_mutable_state) festlegen, wenn Sie einen neuen dynamischen Bereich betreten.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

Im folgenden Beispiel verwenden wir einen Scoped-Wert, um eine Berechtigungsprüfung in einer Webanwendung zu implementieren. Nachdem die Berechtigungen der Anfrage bestimmt wurden, wird ein neuer dynamischer Scope betreten und der Scoped-Wert `LEVEL` gesetzt. Andere Teile der Anwendung können den Scoped-Wert abfragen und erhalten den entsprechenden Wert. Andere Alternativen wie task-lokale Speicherung und globale Variablen sind für diese Art der Propagation nicht gut geeignet; unsere einzige Alternative wäre gewesen, einen Wert durch die gesamte Aufrufkette zu leiten.

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

Um auf den Wert eines Scoped-Werts zuzugreifen, muss der Scoped-Wert selbst im (lexikalischen) Geltungsbereich sein. Das bedeutet, dass Sie Scoped-Werte am häufigsten als konstante globale Werte verwenden möchten.

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

In der Tat kann man sich scoped values als versteckte Funktionsargumente vorstellen.

Dies schließt ihre Verwendung als Nicht-Globale nicht aus.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

Aber es wäre in diesen Fällen vielleicht einfacher gewesen, das Funktionsargument direkt zu übergeben.

### Very many ScopedValues

Wenn Sie feststellen, dass Sie viele `ScopedValue` für ein bestimmtes Modul erstellen, kann es besser sein, eine dedizierte Struktur zu verwenden, um sie zu halten.

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

`Scope`s verwenden ein persistentes Wörterbuch. Die Suche und Einfügung ist `O(log(32, n))`, beim Eintritt in den dynamischen Geltungsbereich wird eine kleine Menge an Daten kopiert und die unveränderten Daten werden unter anderen Geltungsbereichen geteilt.

Das `Scope`-Objekt selbst ist nicht benutzerorientiert und kann in einer zukünftigen Version von Julia geändert werden.

## Design inspiration

Dieses Design wurde stark inspiriert von [JEPS-429](https://openjdk.org/jeps/429), das wiederum von dynamisch gebundenen freien Variablen in vielen Lisp-Dialekten inspiriert wurde. Insbesondere von Interlisp-D und seiner tiefen Bindungsstrategie.

Ein vorheriges besprochenes Design waren Kontextvariablen ala [PEPS-567](https://peps.python.org/pep-0567/) und in Julia implementiert als [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl).

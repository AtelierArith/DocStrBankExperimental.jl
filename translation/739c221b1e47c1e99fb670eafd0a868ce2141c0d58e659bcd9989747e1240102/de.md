```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

Die Zufallszahlengenerierung in Julia verwendet standardmäßig den [Xoshiro256++](https://prng.di.unimi.it/) Algorithmus mit zustandsabhängiger `Task`. Andere RNG-Typen können durch Vererbung des `AbstractRNG` Typs integriert werden; sie können dann verwendet werden, um mehrere Ströme von Zufallszahlen zu erhalten.

Die PRNGs (pseudorandom number generatoren), die vom `Random`-Paket exportiert werden, sind:

  * `TaskLocalRNG`: ein Token, das die Verwendung des derzeit aktiven aufgabenlokalen Streams darstellt, der deterministisch aus der übergeordneten Aufgabe oder durch `RandomDevice` (mit Systemzufälligkeit) beim Programmstart initialisiert wird.
  * `Xoshiro`: erzeugt einen hochwertigen Strom von Zufallszahlen mit einem kleinen Zustandsvektor und hoher Leistung unter Verwendung des Xoshiro256++-Algorithmus.
  * `RandomDevice`: für vom Betriebssystem bereitgestellte Entropie. Dies kann für kryptografisch sichere Zufallszahlen (CS(P)RNG) verwendet werden.
  * `MersenneTwister`: ein alternativer hochwertiger PRNG, der in älteren Versionen von Julia standardmäßig verwendet wurde und ebenfalls recht schnell ist, jedoch viel mehr Speicherplatz benötigt, um den Zustandsvektor zu speichern und eine Zufallssequenz zu erzeugen.

Die meisten Funktionen, die mit der zufälligen Generierung zu tun haben, akzeptieren ein optionales `AbstractRNG`-Objekt als erstes Argument. Einige akzeptieren auch Dimensionsspezifikationen `dims...` (die auch als Tuple angegeben werden können), um Arrays mit zufälligen Werten zu generieren. In einem mehrthreadigen Programm sollten Sie im Allgemeinen unterschiedliche RNG-Objekte aus verschiedenen Threads oder Aufgaben verwenden, um thread-sicher zu sein. Der Standard-RNG ist jedoch ab Julia 1.3 thread-sicher (unter Verwendung eines pro-Thread-RNG bis Version 1.6 und pro-Aufgabe danach).

Die bereitgestellten RNGs können gleichmäßig zufällige Zahlen der folgenden Typen generieren: [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref), [`BigFloat`](@ref), [`Bool`](@ref), [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`BigInt`](@ref) (oder komplexe Zahlen dieser Typen). Zufällige Fließkommazahlen werden gleichmäßig im $[0, 1)$ generiert. Da `BigInt` unbegrenzte Ganzzahlen darstellt, muss das Intervall angegeben werden (z. B. `rand(big.(1:6))`).

Zusätzlich werden normale und exponentielle Verteilungen für einige `AbstractFloat`- und `Complex`-Typen implementiert, siehe [`randn`](@ref) und [`randexp`](@ref) für Details.

Um Zufallszahlen aus anderen Verteilungen zu generieren, siehe das [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) Paket.

!!! warning
    Da die genaue Art und Weise, wie Zufallszahlen generiert werden, als Implementierungsdetail betrachtet wird, können Fehlerbehebungen und Geschwindigkeitsverbesserungen den Strom von Zahlen, die nach einer Versionsänderung generiert werden, ändern. Es wird daher davon abgeraten, sich während der Unit-Tests auf einen bestimmten Seed oder einen generierten Zahlenstrom zu verlassen - ziehen Sie stattdessen in Betracht, die Eigenschaften der betreffenden Methoden zu testen.


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

Es gibt zwei weitgehend orthogonale Möglichkeiten, die Funktionalitäten von `Random` zu erweitern:

1. generieren von zufälligen Werten benutzerdefinierter Typen
2. neue Generatoren erstellen

Die API für 1) ist ziemlich funktional, aber relativ neu, sodass sie sich möglicherweise in zukünftigen Versionen des `Random`-Moduls weiterentwickeln muss. Zum Beispiel ist es normalerweise ausreichend, eine `rand`-Methode zu implementieren, damit alle anderen üblichen Methoden automatisch funktionieren.

Die API für 2) ist noch rudimentär und könnte mehr Arbeit erfordern, als unbedingt notwendig ist, um die üblichen Arten von generierten Werten zu unterstützen.

### Generating random values of custom types

Das Generieren von Zufallswerten für einige Verteilungen kann verschiedene Kompromisse mit sich bringen. *Vorab berechnete* Werte, wie [alias table](https://en.wikipedia.org/wiki/Alias_method) für diskrete Verteilungen oder [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling) für univariate Verteilungen, können das Sampling erheblich beschleunigen. Wie viele Informationen vorab berechnet werden sollten, kann von der Anzahl der Werte abhängen, die wir aus einer Verteilung ziehen möchten. Außerdem können einige Zufallszahlengeneratoren bestimmte Eigenschaften haben, die verschiedene Algorithmen ausnutzen möchten.

Das `Random`-Modul definiert ein anpassbares Framework zur Erzeugung von Zufallswerten, das diese Probleme adressieren kann. Jeder Aufruf von `rand` erzeugt einen *Sampler*, der mit den oben genannten Kompromissen im Hinterkopf angepasst werden kann, indem Methoden zu `Sampler` hinzugefügt werden, die wiederum auf den Zufallszahlengenerator, das Objekt, das die Verteilung charakterisiert, und einen Vorschlag für die Anzahl der Wiederholungen zugreifen können. Derzeit werden für letzteres `Val{1}` (für eine einzelne Probe) und `Val{Inf}` (für eine beliebige Anzahl) verwendet, wobei `Random.Repetition` ein Alias für beide ist.

Das von `Sampler` zurückgegebene Objekt wird dann verwendet, um die Zufallswerte zu generieren. Bei der Implementierung der Schnittstelle zur Zufallswertgenerierung für einen Wert `X`, der ausgewählt werden kann, sollte der Implementierer die Methode definieren

```julia
rand(rng, sampler)
```

für den speziellen `sampler`, der von `Sampler(rng, X, repetition)` zurückgegeben wird.

Sampler können beliebige Werte sein, die `rand(rng, sampler)` implementieren, aber für die meisten Anwendungen sind die folgenden vordefinierten Sampler möglicherweise ausreichend:

1. `SamplerType{T}()` kann verwendet werden, um Sampler zu implementieren, die von Typ `T` ziehen (z. B. `rand(Int)`). Dies ist der Standardwert, der von `Sampler` für *Typen* zurückgegeben wird.
2. `SamplerTrivial(self)` ist ein einfacher Wrapper für `self`, der mit `[]` zugegriffen werden kann. Dies ist der empfohlene Sampler, wenn keine vorab berechneten Informationen benötigt werden (z. B. `rand(1:3)`), und ist der Standard, der von `Sampler` für *Werte* zurückgegeben wird.
3. `SamplerSimple(self, data)` enthält auch das zusätzliche `data`-Feld, das verwendet werden kann, um beliebige vorab berechnete Werte zu speichern, die in einer *benutzerdefinierten Methode* von `Sampler` berechnet werden sollten.

Wir geben Beispiele für jedes dieser. Wir gehen hier davon aus, dass die Wahl des Algorithmus unabhängig vom RNG ist, daher verwenden wir `AbstractRNG` in unseren Signaturen.

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

Die Entkopplung der Vorberechnung von der tatsächlichen Generierung der Werte ist Teil der API und steht auch dem Benutzer zur Verfügung. Als Beispiel nehmen wir an, dass `rand(rng, 1:20)` wiederholt in einer Schleife aufgerufen werden muss: Die Möglichkeit, von dieser Entkopplung zu profitieren, ist wie folgt:

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

Dies ist der Mechanismus, der auch in der Standardbibliothek verwendet wird, z. B. durch die Standardimplementierung der zufälligen Array-Generierung (wie in `rand(1:20, 10)`).

#### Generating values from a type

Gegeben einen Typ `T` wird derzeit angenommen, dass, wenn `rand(T)` definiert ist, ein Objekt des Typs `T` erzeugt wird. `SamplerType` ist der *Standard-Sampler für Typen*. Um die zufällige Generierung von Werten des Typs `T` zu definieren, sollte die Methode `rand(rng::AbstractRNG, ::Random.SamplerType{T})` definiert werden und Werte zurückgeben, die dem entsprechen, was `rand(rng, T)` zurückgeben soll.

Lass uns folgendes Beispiel betrachten: Wir implementieren einen `Die`-Typ, mit einer variablen Anzahl `n` von Seiten, nummeriert von `1` bis `n`. Wir möchten, dass `rand(Die)` einen `Die` mit einer zufälligen Anzahl von bis zu 20 Seiten (und mindestens 4) erzeugt:

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

Skalar- und Array-Methoden für `Die` funktionieren jetzt wie erwartet:

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

Hier definieren wir einen Sampler für eine Sammlung. Wenn keine vorab berechneten Daten erforderlich sind, kann er mit einem `SamplerTrivial`-Sampler implementiert werden, der tatsächlich der *Standardfallback für Werte* ist.

Um die Zufallsgenerierung aus Objekten des Typs `S` zu definieren, sollte die folgende Methode definiert werden: `rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`. Hierbei umschließt `sp` einfach ein Objekt des Typs `S`, das über `sp[]` zugegriffen werden kann. Fortfahrend mit dem Beispiel `Die` wollen wir nun `rand(d::Die)` definieren, um eine `Int` zu erzeugen, die einer der Seiten von `d` entspricht:

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

Gegeben einen Sammlungstyp `S` wird derzeit angenommen, dass, wenn `rand(::S)` definiert ist, ein Objekt des Typs `eltype(S)` erzeugt wird. Im letzten Beispiel wird ein `Vector{Any}` erzeugt; der Grund dafür ist, dass `eltype(Die) == Any` ist. Die Lösung besteht darin, `Base.eltype(::Type{Die}) = Int` zu definieren.

#### Generating values for an `AbstractFloat` type

`AbstractFloat`-Typen sind speziell behandelt, da standardmäßig keine Zufallswerte im gesamten Typbereich erzeugt werden, sondern eher im Bereich `[0,1)`. Die folgende Methode sollte für `T <: AbstractFloat` implementiert werden: `Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

Betrachten Sie eine diskrete Verteilung, bei der Zahlen `1:n` mit gegebenen Wahrscheinlichkeiten gezogen werden, die sich zu eins summieren. Wenn viele Werte aus dieser Verteilung benötigt werden, ist die schnellste Methode die Verwendung einer [alias table](https://en.wikipedia.org/wiki/Alias_method). Wir geben hier nicht den Algorithmus zum Erstellen einer solchen Tabelle an, aber nehmen Sie an, dass er stattdessen in `make_alias_table(probabilities)` verfügbar ist, und `draw_number(rng, alias_table)` verwendet werden kann, um eine Zufallszahl daraus zu ziehen.

Angenommen, die Verteilung wird beschrieben durch

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

und dass wir *immer* eine Alias-Tabelle erstellen möchten, unabhängig von der Anzahl der benötigten Werte (wir lernen unten, wie man dies anpasst). Die Methoden

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

sollte definiert werden, um einen Sampler mit vorab berechneten Daten zurückzugeben, dann

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

wird verwendet, um die Werte zu zeichnen.

#### Custom sampler types

Der `SamplerSimple`-Typ ist für die meisten Anwendungsfälle mit vorab berechneten Daten ausreichend. Um jedoch zu demonstrieren, wie man benutzerdefinierte Samplertypen verwendet, implementieren wir hier etwas Ähnliches wie `SamplerSimple`.

Zurück zu unserem `Die`-Beispiel: `rand(::Die)` verwendet die Zufallszahlengenerierung aus einem Bereich, sodass es hier eine Möglichkeit zur Optimierung gibt. Wir nennen unseren benutzerdefinierten Sampler `SamplerDie`.

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

Es ist jetzt möglich, einen Sampler mit `sp = Sampler(rng, die)` zu erhalten und `sp` anstelle von `die` in jedem `rand`-Aufruf zu verwenden, der `rng` betrifft. In dem einfachen obigen Beispiel muss `die` nicht in `SamplerDie` gespeichert werden, aber das ist in der Praxis oft der Fall.

Natürlich ist dieses Muster so häufig, dass der oben verwendete Hilfstyp, nämlich `Random.SamplerSimple`, verfügbar ist, was uns die Definition von `SamplerDie` erspart: Wir hätten unsere Entkopplung mit folgendem umsetzen können:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

Hier bezieht sich `sp.data` auf den zweiten Parameter im Aufruf des Konstruktors `SamplerSimple` (in diesem Fall gleich `Sampler(rng, 1:die.nsides, r)`), während das `Die`-Objekt über `sp[]` zugänglich ist.

Wie `SamplerDie` muss jeder benutzerdefinierte Sampler ein Subtyp von `Sampler{T}` sein, wobei `T` der Typ der generierten Werte ist. Beachten Sie, dass `SamplerSimple(x, data) isa Sampler{eltype(x)}` ist, was einschränkt, was das erste Argument von `SamplerSimple` sein kann (es wird empfohlen, `SamplerSimple` wie im `Die`-Beispiel zu verwenden, wo `x` einfach weitergegeben wird, während eine `Sampler`-Methode definiert wird). Ebenso gilt, dass `SamplerTrivial(x) isa Sampler{eltype(x)}`.

Ein weiterer Hilfstyp ist derzeit für andere Fälle verfügbar, `Random.SamplerTag`, wird jedoch als interne API betrachtet und kann jederzeit ohne ordnungsgemäße Abkündigungen brechen.

#### Using distinct algorithms for scalar or array generation

In einigen Fällen hat es Einfluss auf die Wahl des Algorithmus, ob man nur eine Handvoll Werte oder eine große Anzahl von Werten generieren möchte. Dies wird mit dem dritten Parameter des `Sampler`-Konstruktors behandelt. Angenommen, wir haben zwei Hilfstypen für `Die` definiert, sagen wir `SamplerDie1`, der verwendet werden sollte, um nur wenige zufällige Werte zu generieren, und `SamplerDieMany` für viele Werte. Wir können diese Typen wie folgt verwenden:

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

Natürlich muss `rand` auch für diese Typen definiert werden (d.h. `rand(::AbstractRNG, ::SamplerDie1)` und `rand(::AbstractRNG, ::SamplerDieMany)`). Beachten Sie, dass wie gewohnt `SamplerTrivial` und `SamplerSimple` verwendet werden können, wenn benutzerdefinierte Typen nicht erforderlich sind.

Hinweis: `Sampler(rng, x)` ist einfach eine Abkürzung für `Sampler(rng, x, Val(Inf))`, und `Random.Repetition` ist ein Alias für `Union{Val{1}, Val{Inf}}`.

### Creating new generators

Die API ist noch nicht klar definiert, aber als Faustregel:

1. Jede `rand`-Methode, die "einfache" Typen (`isbitstype` Ganzzahlen und Fließkommatypen in `Base`) erzeugt, sollte für diesen spezifischen RNG definiert werden, falls sie benötigt wird;
2. Andere dokumentierte `rand`-Methoden, die einen `AbstractRNG` akzeptieren, sollten sofort funktionieren (vorausgesetzt, die Methoden aus 1), auf die verwiesen wird, sind implementiert), können jedoch natürlich für diesen RNG spezialisiert werden, wenn Raum für Optimierungen besteht;
3. `copy` für pseudo-RNGs sollte eine unabhängige Kopie zurückgeben, die die exakt gleiche Zufallssequenz wie das Original ab dem Zeitpunkt generiert, an dem sie auf die gleiche Weise aufgerufen wird. Wenn dies nicht möglich ist (z. B. bei hardwarebasierten RNGs), darf `copy` nicht implementiert werden.

Bezüglich 1) kann eine `rand`-Methode zufällig automatisch funktionieren, wird jedoch nicht offiziell unterstützt und kann in einer späteren Version ohne Vorwarnung brechen.

Um eine neue `rand`-Methode für einen hypothetischen `MyRNG`-Generator und eine Wertespezifikation `s` (z. B. `s == Int` oder `s == 1:10`) vom Typ `S==typeof(s)` oder `S==Type{s}` zu definieren, müssen die gleichen beiden Methoden wie zuvor definiert werden:

1. `Sampler(::Type{MyRNG}, ::S, ::Repetition)`, der ein Objekt des Typs `SamplerS` zurückgibt.
2. `rand(rng::MyRNG, sp::SamplerS)`

Es kann vorkommen, dass `Sampler(rng::AbstractRNG, ::S, ::Repetition)` bereits im `Random`-Modul definiert ist. In diesem Fall wäre es möglich, Schritt 1) in der Praxis zu überspringen (wenn man die Generierung für diesen speziellen RNG-Typ spezialisieren möchte), aber der entsprechende `SamplerS`-Typ wird als internes Detail betrachtet und kann ohne Vorwarnung geändert werden.

#### Specializing array generation

In einigen Fällen kann es für einen bestimmten RNG-Typ effizienter sein, ein Array von Zufallswerten mit einer spezialisierten Methode zu generieren, als lediglich die zuvor erklärte Entkopplungstechnik zu verwenden. Dies ist beispielsweise der Fall bei `MersenneTwister`, der nativ Zufallswerte in ein Array schreibt.

Um diese Spezialisierung für `MyRNG` und für eine Spezifikation `s` zu implementieren, die Elemente vom Typ `S` erzeugt, kann die folgende Methode definiert werden: `rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`, wobei `SamplerS` der Typ des Samplers ist, der von `Sampler(MyRNG, s, Val(Inf))` zurückgegeben wird. Anstelle von `AbstractArray` ist es möglich, die Funktionalität nur für einen Untertyp zu implementieren, z. B. `Array{S}`. Die nicht-mutierende Array-Methode von `rand` wird diese Spezialisierung intern automatisch aufrufen.

```@meta
DocTestSetup = nothing
```

# Reproducibility

Durch die Verwendung eines mit einem bestimmten Seed initialisierten RNG-Parameters können Sie die gleiche Pseudorandom-Zahlenfolge reproduzieren, wenn Sie Ihr Programm mehrmals ausführen. Eine kleinere Version von Julia (z. B. 1.3 bis 1.4) *kann* jedoch die Folge der aus einem bestimmten Seed generierten Pseudorandom-Zahlen ändern, insbesondere wenn `MersenneTwister` verwendet wird. (Selbst wenn die von einer Low-Level-Funktion wie [`rand`](@ref) erzeugte Folge sich nicht ändert, kann die Ausgabe von höherstufigen Funktionen wie [`randsubseq`](@ref) aufgrund von Algorithmus-Updates variieren.) Begründung: Die Garantie, dass Pseudorandom-Streams sich niemals ändern, verbietet viele algorithmische Verbesserungen.

Wenn Sie die genaue Reproduzierbarkeit von Zufallsdaten garantieren müssen, ist es ratsam, einfach *die Daten zu speichern* (z. B. als ergänzenden Anhang in einer wissenschaftlichen Veröffentlichung). (Sie können natürlich auch eine bestimmte Julia-Version und ein Paketmanifest angeben, insbesondere wenn Sie eine bitgenaue Reproduzierbarkeit benötigen.)

Softwaretests, die auf *spezifischen* "zufälligen" Daten basieren, sollten in der Regel entweder die Daten speichern, sie in den Testcode einbetten oder Drittanbieter-Pakete wie [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl) verwenden. Auf der anderen Seite können Tests, die für *die meisten* zufälligen Daten bestehen sollten (z. B. das Testen von `A \ (A*x) ≈ x` für eine zufällige Matrix `A = randn(n,n)`), einen RNG mit einem festen Seed verwenden, um sicherzustellen, dass das bloße Ausführen des Tests viele Male nicht auf einen Fehler aufgrund sehr unwahrscheinlicher Daten stößt (z. B. eine extrem schlecht konditionierte Matrix).

Die statistische *Verteilung*, aus der Zufallsstichproben gezogen werden, *ist* garantiert, dass sie über alle kleineren Julia-Versionen hinweg gleich bleibt.

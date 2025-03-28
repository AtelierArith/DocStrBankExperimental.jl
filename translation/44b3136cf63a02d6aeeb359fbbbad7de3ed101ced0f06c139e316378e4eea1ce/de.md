```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia befindet sich in einer schnellen Entwicklung und verfügt über eine umfangreiche Test-Suite, um die Funktionalität auf mehreren Plattformen zu überprüfen. Wenn Sie Julia aus dem Quellcode erstellen, können Sie diese Test-Suite mit `make test` ausführen. Bei einer Binärinstallation können Sie die Test-Suite mit `Base.runtests()` ausführen.

```@docs
Base.runtests
```

## Basic Unit Tests

Das `Test`-Modul bietet einfache *Unit-Testing*-Funktionalität. Unit-Testing ist eine Möglichkeit, um zu überprüfen, ob Ihr Code korrekt ist, indem Sie sicherstellen, dass die Ergebnisse Ihren Erwartungen entsprechen. Es kann hilfreich sein, um sicherzustellen, dass Ihr Code nach Änderungen weiterhin funktioniert, und kann beim Entwickeln verwendet werden, um die Verhaltensweisen zu spezifizieren, die Ihr Code beim Abschluss haben sollte. Sie möchten möglicherweise auch die Dokumentation für [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package) ansehen.

Einfache Unit-Tests können mit den `@test` und `@test_throws` Makros durchgeführt werden:

```@docs
Test.@test
Test.@test_throws
```

Zum Beispiel, nehmen wir an, wir möchten überprüfen, ob unsere neue Funktion `foo(x)` wie erwartet funktioniert:

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

Wenn die Bedingung wahr ist, wird ein `Pass` zurückgegeben:

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

Wenn die Bedingung falsch ist, wird ein `Fail` zurückgegeben und eine Ausnahme ausgelöst:

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

Wenn die Bedingung nicht ausgewertet werden konnte, weil eine Ausnahme ausgelöst wurde, was in diesem Fall geschieht, weil `length` für Symbole nicht definiert ist, wird ein `Error`-Objekt zurückgegeben und eine Ausnahme ausgelöst:

```julia-repl
julia> @test foo(:cat) == 1
Error During Test
  Test threw an exception of type MethodError
  Expression: foo(:cat) == 1
  MethodError: no method matching length(::Symbol)
  The function `length` exists, but no method is defined for this combination of argument types.

  Closest candidates are:
    length(::SimpleVector) at essentials.jl:256
    length(::Base.MethodList) at reflection.jl:521
    length(::MethodTable) at reflection.jl:597
    ...
  Stacktrace:
  [...]
ERROR: There was an error during testing
```

Wenn wir erwarten, dass die Auswertung eines Ausdrucks *eine* Ausnahme auslösen sollte, können wir `@test_throws` verwenden, um zu überprüfen, dass dies geschieht:

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

Typischerweise wird eine große Anzahl von Tests verwendet, um sicherzustellen, dass Funktionen über eine Reihe von Eingaben korrekt arbeiten. Im Falle eines fehlgeschlagenen Tests ist das Standardverhalten, sofort eine Ausnahme auszulösen. Es ist jedoch normalerweise vorzuziehen, zuerst die restlichen Tests auszuführen, um ein besseres Bild davon zu bekommen, wie viele Fehler im getesteten Code vorhanden sind.

!!! note
    Der `@testset` erstellt einen eigenen lokalen Geltungsbereich, wenn die Tests darin ausgeführt werden.


Das `@testset`-Makro kann verwendet werden, um Tests in *Sätze* zu gruppieren. Alle Tests in einem Testsatz werden ausgeführt, und am Ende des Testsatzes wird eine Zusammenfassung gedruckt. Wenn einer der Tests fehlgeschlagen ist oder aufgrund eines Fehlers nicht ausgewertet werden konnte, wird der Testsatz dann eine `TestSetException` auslösen.

```@docs
Test.@testset
Test.TestSetException
```

Wir können unsere Tests für die `foo(x)`-Funktion in einem Testset unterbringen:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

Test-Sets können auch geschachtelt werden:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
```

Sowie Funktionen aufrufen:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

Dies kann verwendet werden, um die Faktorisierung von Testsets zu ermöglichen, was es einfacher macht, einzelne Testsets auszuführen, indem stattdessen die zugehörigen Funktionen aufgerufen werden. Beachten Sie, dass im Fall von Funktionen das Testset den Namen der aufgerufenen Funktion erhält. Falls ein geschachteltes Testset keine Fehler aufweist, wie hier geschehen, wird es in der Zusammenfassung ausgeblendet, es sei denn, die Option `verbose=true` wird übergeben:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset verbose = true "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
  Animals     |    2      2  0.0s
  Arrays 1    |    2      2  0.0s
  Arrays 2    |    2      2  0.0s
  Arrays 3    |    2      2  0.0s
```

Wenn wir einen Testfehler haben, werden nur die Details für die fehlgeschlagenen Testsets angezeigt:

```julia-repl; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @testset "Felines" begin
                   @test foo("cat") == 9
               end
               @testset "Canines" begin
                   @test foo("dog") == 9
               end
           end
           @testset "Arrays" begin
               @test foo(zeros(2)) == 4
               @test foo(fill(1.0, 4)) == 15
           end
       end

Arrays: Test Failed
  Expression: foo(fill(1.0, 4)) == 15
   Evaluated: 16 == 15
[...]
Test Summary: | Pass  Fail  Total  Time
Foo Tests     |    3     1      4  0.0s
  Animals     |    2            2  0.0s
  Arrays      |    1     1      2  0.0s
ERROR: Some tests did not pass: 3 passed, 1 failed, 0 errored, 0 broken.
```

## Testing Log Statements

Man kann das [`@test_logs`](@ref) Makro verwenden, um Protokollanweisungen zu testen, oder ein [`TestLogger`](@ref) verwenden.

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

Da Berechnungen mit Fließkommawerten ungenau sein können, können Sie ungefähre Gleichheitsprüfungen entweder mit `@test a ≈ b` durchführen (wobei `≈`, eingegeben über die Tab-Vervollständigung von `\approx`, die [`isapprox`](@ref)-Funktion ist) oder verwenden Sie `4d61726b646f776e2e436f64652822222c20226973617070726f782229_40726566` direkt.

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

Sie können relative und absolute Toleranzen festlegen, indem Sie die Schlüsselwortargumente `rtol` und `atol` von `isapprox` entsprechend nach dem `≈`-Vergleich einstellen:

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

Beachten Sie, dass dies kein spezifisches Merkmal von `≈` ist, sondern vielmehr ein allgemeines Merkmal des `@test`-Makros: `@test a <op> b key=val` wird vom Makro in `@test op(a, b, key=val)` umgewandelt. Es ist jedoch besonders nützlich für `≈`-Tests.

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

Wenn ein Test konstant fehlschlägt, kann er so geändert werden, dass das `@test_broken`-Makro verwendet wird. Dies kennzeichnet den Test als `Broken`, wenn der Test weiterhin fehlschlägt, und warnt den Benutzer über einen `Error`, wenn der Test erfolgreich ist.

```@docs
Test.@test_broken
```

`@test_skip` ist ebenfalls verfügbar, um einen Test ohne Auswertung zu überspringen, zählt jedoch den übersprungenen Test in der Testberichterstattung. Der Test wird nicht ausgeführt, gibt jedoch ein `Broken` `Result` zurück.

```@docs
Test.@test_skip
```

## Test result types

```@docs
Test.Result
Test.Pass
Test.Fail
Test.Error
Test.Broken
```

## Creating Custom `AbstractTestSet` Types

Pakete können ihre eigenen `AbstractTestSet`-Untertypen erstellen, indem sie die Methoden `record` und `finish` implementieren. Der Untertyp sollte einen Konstruktor mit einem Argument haben, der einen Beschreibungsstring entgegennimmt, wobei alle Optionen als Schlüsselwortargumente übergeben werden.

```@docs
Test.record
Test.finish
```

`Test` übernimmt die Verantwortung für die Verwaltung eines Stapels von geschachtelten Testsets während ihrer Ausführung, aber die Ergebnisakkumulation liegt in der Verantwortung des `AbstractTestSet`-Subtyps. Sie können auf diesen Stapel mit den Methoden `get_testset` und `get_testset_depth` zugreifen. Beachten Sie, dass diese Funktionen nicht exportiert sind.

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test` stellt auch sicher, dass geschachtelte `@testset`-Aufrufe denselben `AbstractTestSet`-Untertyp wie ihr übergeordnetes Element verwenden, es sei denn, dies wird ausdrücklich festgelegt. Es propagiert keine Eigenschaften des Testsets. Das Verhalten der Optionenvererbung kann von Paketen mithilfe der Stapelinfrastruktur, die `Test` bereitstellt, implementiert werden.

Die Definition eines grundlegenden `AbstractTestSet`-Subtyps könnte folgendermaßen aussehen:

```julia
import Test: Test, record, finish
using Test: AbstractTestSet, Result, Pass, Fail, Error
using Test: get_testset_depth, get_testset
struct CustomTestSet <: Test.AbstractTestSet
    description::AbstractString
    foo::Int
    results::Vector
    # constructor takes a description string and options keyword arguments
    CustomTestSet(desc; foo=1) = new(desc, foo, [])
end

record(ts::CustomTestSet, child::AbstractTestSet) = push!(ts.results, child)
record(ts::CustomTestSet, res::Result) = push!(ts.results, res)
function finish(ts::CustomTestSet)
    # just record if we're not the top-level parent
    if get_testset_depth() > 0
        record(get_testset(), ts)
        return ts
    end

    # so the results are printed if we are at the top level
    Test.print_test_results(ts)
    return ts
end
```

Und die Verwendung dieses Testsets sieht folgendermaßen aus:

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

Um ein benutzerdefiniertes Testset zu verwenden und die aufgezeichneten Ergebnisse als Teil eines äußeren Standard-Testsets auszugeben, definieren Sie auch `Test.get_test_counts`. Das könnte so aussehen:

```julia
using Test: AbstractTestSet, Pass, Fail, Error, Broken, get_test_counts, TestCounts, format_duration

function Test.get_test_counts(ts::CustomTestSet)
    passes, fails, errors, broken = 0, 0, 0, 0
    # cumulative results
    c_passes, c_fails, c_errors, c_broken = 0, 0, 0, 0

    for t in ts.results
        # count up results
        isa(t, Pass)   && (passes += 1)
        isa(t, Fail)   && (fails  += 1)
        isa(t, Error)  && (errors += 1)
        isa(t, Broken) && (broken += 1)
        # handle children
        if isa(t, AbstractTestSet)
            tc = get_test_counts(t)::TestCounts
            c_passes += tc.passes + tc.cumulative_passes
            c_fails  += tc.fails + tc.cumulative_fails
            c_errors += tc.errors + tc.cumulative_errors
            c_broken += tc.broken + tc.cumulative_broken
        end
    end
    # get a duration, if we have one
    duration = format_duration(ts)
    return TestCounts(true, passes, fails, errors, broken, c_passes, c_fails, c_errors, c_broken, duration)
end
```

```@docs
Test.TestCounts
Test.get_test_counts
Test.format_duration
Test.print_test_results
```

## Test utilities

```@docs
Test.GenericArray
Test.GenericDict
Test.GenericOrder
Test.GenericSet
Test.GenericString
Test.detect_ambiguities
Test.detect_unbound_args
```

## Workflow for Testing Packages

Mit den uns in den vorherigen Abschnitten zur Verfügung stehenden Werkzeugen, hier ist ein möglicher Arbeitsablauf zur Erstellung eines Pakets und zum Hinzufügen von Tests dazu.

### Generating an Example Package

Für diesen Workflow werden wir ein Paket namens `Example` erstellen:

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

Die wichtigste Voraussetzung für das Testen eines Pakets ist, dass es Funktionalität zum Testen gibt. Dazu werden wir einige einfache Funktionen zu `Example` hinzufügen, die wir testen können. Fügen Sie Folgendes zu `src/Example.jl` hinzu:

```julia
module Example

function greet()
    "Hello world!"
end

function simple_add(a, b)
    a + b
end

function type_multiply(a::Float64, b::Float64)
    a * b
end

export greet, simple_add, type_multiply

end
```

### Creating a Test Environment

Navigieren Sie im Stammverzeichnis des `Example`-Pakets zum `test`-Verzeichnis, aktivieren Sie dort eine neue Umgebung und fügen Sie das `Test`-Paket zur Umgebung hinzu:

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

Jetzt sind wir bereit, Tests zu `Example` hinzuzufügen. Es ist gängige Praxis, eine Datei im `test`-Verzeichnis mit dem Namen `runtests.jl` zu erstellen, die die Testsets enthält, die wir ausführen möchten. Legen Sie diese Datei im `test`-Verzeichnis an und fügen Sie den folgenden Code hinzu:

```julia
using Example
using Test

@testset "Example tests" begin

    @testset "Math tests" begin
        include("math_tests.jl")
    end

    @testset "Greeting tests" begin
        include("greeting_tests.jl")
    end
end
```

Wir müssen die beiden enthaltenen Dateien `math_tests.jl` und `greeting_tests.jl` erstellen und einige Tests hinzufügen.

> **Hinweis:** Beachten Sie, dass wir nicht angeben mussten, `Example` in die `test`-Umgebung von `Project.toml` aufzunehmen. Dies ist ein Vorteil des Testsystems von Julia, dass Sie [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/) hinzufügen konnten.


#### Writing Tests for `math_tests.jl`

Mit unserem Wissen über `Test.jl` sind hier einige Beispieltests, die wir zu `math_tests.jl` hinzufügen könnten:

```julia
@testset "Testset 1" begin
    @test 2 == simple_add(1, 1)
    @test 3.5 == simple_add(1, 2.5)
        @test_throws MethodError simple_add(1, "A")
        @test_throws MethodError simple_add(1, 2, 3)
end

@testset "Testset 2" begin
    @test 1.0 == type_multiply(1.0, 1.0)
        @test isa(type_multiply(2.0, 2.0), Float64)
    @test_throws MethodError type_multiply(1, 2.5)
end
```

#### Writing Tests for `greeting_tests.jl`

Mit unserem Wissen über `Test.jl` sind hier einige Beispieltests, die wir zu `greeting_tests.jl` hinzufügen könnten:

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

Jetzt, da wir unsere Tests und unser `runtests.jl`-Skript im `test`-Verzeichnis hinzugefügt haben, können wir unser `Example`-Paket testen, indem wir zum Stammverzeichnis der `Example`-Paketumgebung zurückkehren und die `Example`-Umgebung reaktivieren:

```julia
shell> cd ..
pkg> activate .
```

Von dort aus können wir schließlich unser Testpaket wie folgt ausführen:

```julia
(Example) pkg> test
     Testing Example
      Status `/tmp/jl_Yngpvy/Project.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [8dfed614] Test `@stdlib/Test`
      Status `/tmp/jl_Yngpvy/Manifest.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [2a0f44e3] Base64 `@stdlib/Base64`
  [b77e0a4c] InteractiveUtils `@stdlib/InteractiveUtils`
  [56ddb016] Logging `@stdlib/Logging`
  [d6f4376e] Markdown `@stdlib/Markdown`
  [9a3f8284] Random `@stdlib/Random`
  [ea8e919c] SHA `@stdlib/SHA`
  [9e88b42a] Serialization `@stdlib/Serialization`
  [8dfed614] Test `@stdlib/Test`
     Testing Running tests...
Test Summary: | Pass  Total
Example tests |    9      9
     Testing Example tests passed
```

Und wenn alles korrekt verlief, sollten Sie eine ähnliche Ausgabe wie oben sehen. Mit `Test.jl` können kompliziertere Tests für Pakete hinzugefügt werden, aber dies sollte idealerweise die Entwickler in die Richtung weisen, wie sie mit dem Testen ihrer eigenen erstellten Pakete beginnen können.

```@meta
DocTestSetup = nothing
```

### Code Coverage

Die Verfolgung der Codeabdeckung während der Tests kann mit dem `pkg> test --coverage`-Flag aktiviert werden (oder auf einer niedrigeren Ebene mit dem [`--code-coverage`](@ref command-line-interface) Julia-Argument). Dies ist standardmäßig im [julia-runtest](https://github.com/julia-actions/julia-runtest) GitHub-Action aktiviert.

To evaluate coverage either manually inspect the `.cov` files that are generated beside the source files locally, or in CI use the [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub action.

!!! compat "Julia 1.11"
    Seit Julia 1.11 wird die Abdeckung während der Phase der Paketvorkompilierung nicht mehr erfasst.


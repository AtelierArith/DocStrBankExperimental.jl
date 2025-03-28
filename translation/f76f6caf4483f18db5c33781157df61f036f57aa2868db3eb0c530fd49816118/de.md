```
@testset [CustomTestSet] [options...] ["Beschreibung"] begin test_ex end
@testset [CustomTestSet] [options...] ["Beschreibung $v"] for v in itr test_ex end
@testset [CustomTestSet] [options...] ["Beschreibung $v, $w"] for v in itrv, w in itrw test_ex end
@testset [CustomTestSet] [options...] ["Beschreibung"] test_func()
@testset let v = v, w = w; test_ex; end
```

# Mit begin/end oder Funktionsaufruf

Wenn @testset verwendet wird, mit begin/end oder einem einzelnen Funktionsaufruf, startet das Makro ein neues Testset, in dem der gegebene Ausdruck ausgewertet wird.

Wenn kein benutzerdefinierter Testset-Typ angegeben ist, wird standardmäßig ein `DefaultTestSet` erstellt. `DefaultTestSet` zeichnet alle Ergebnisse auf und wirft, falls es `Fail`s oder `Error`s gibt, am Ende des obersten (nicht geschachtelten) Testsets eine Ausnahme, zusammen mit einer Zusammenfassung der Testergebnisse.

Jeder benutzerdefinierte Testset-Typ (Untertyp von `AbstractTestSet`) kann angegeben werden und wird auch für alle geschachtelten `@testset`-Aufrufe verwendet. Die angegebenen Optionen werden nur auf das Testset angewendet, in dem sie angegeben sind. Der Standard-Testset-Typ akzeptiert drei boolesche Optionen:

  * `verbose`: wenn `true`, wird die Ergebnisszusammenfassung der geschachtelten Testsets angezeigt, selbst wenn sie alle bestehen (der Standardwert ist `false`).
  * `showtiming`: wenn `true`, wird die Dauer jedes angezeigten Testsets angezeigt (der Standardwert ist `true`).
  * `failfast`: wenn `true`, führt jeder Testfehler oder Fehler dazu, dass das Testset und alle untergeordneten Testsets sofort zurückgegeben werden (der Standardwert ist `false`). Dies kann auch global über die Umgebungsvariable `JULIA_TEST_FAILFAST` festgelegt werden.

!!! compat "Julia 1.8"
    `@testset test_func()` erfordert mindestens Julia 1.8.


!!! compat "Julia 1.9"
    `failfast` erfordert mindestens Julia 1.9.


Der Beschreibungsstring akzeptiert Interpolation von den Schleifenindizes. Wenn keine Beschreibung angegeben ist, wird eine basierend auf den Variablen erstellt. Wenn ein Funktionsaufruf angegeben ist, wird dessen Name verwendet. Explizite Beschreibungsstrings überschreiben dieses Verhalten.

Standardmäßig gibt das `@testset`-Makro das Testset-Objekt selbst zurück, obwohl dieses Verhalten in anderen Testset-Typen angepasst werden kann. Wenn eine `for`-Schleife verwendet wird, sammelt und gibt das Makro eine Liste der Rückgabewerte der `finish`-Methode zurück, die standardmäßig eine Liste der in jeder Iteration verwendeten Testset-Objekte zurückgibt.

Vor der Ausführung des Körpers eines `@testset` erfolgt ein impliziter Aufruf von `Random.seed!(seed)`, wobei `seed` der aktuelle Seed des globalen RNG ist. Darüber hinaus wird nach der Ausführung des Körpers der Zustand des globalen RNG auf den Zustand vor dem `@testset` zurückgesetzt. Dies soll die Reproduzierbarkeit im Falle eines Fehlers erleichtern und nahtlose Umstellungen von `@testset`s unabhängig von ihren Nebenwirkungen auf den Zustand des globalen RNG ermöglichen.

## Beispiele

```jldoctest; filter = r"trigonometric identities |    4      4  [0-9\.]+s"
julia> @testset "trigonometric identities" begin
           θ = 2/3*π
           @test sin(-θ) ≈ -sin(θ)
           @test cos(-θ) ≈ cos(θ)
           @test sin(2θ) ≈ 2*sin(θ)*cos(θ)
           @test cos(2θ) ≈ cos(θ)^2 - sin(θ)^2
       end;
Test Summary:            | Pass  Total  Time
trigonometric identities |    4      4  0.2s
```

# `@testset for`

Wenn `@testset for` verwendet wird, startet das Makro einen neuen Test für jede Iteration der bereitgestellten Schleife. Die Semantik jedes Testsets ist ansonsten identisch mit der des `begin/end`-Falls (als ob es für jede Schleifeniteration verwendet wird).

# `@testset let`

Wenn `@testset let` verwendet wird, startet das Makro ein *transparentes* Testset, wobei das gegebene Objekt als Kontextobjekt zu jedem fehlerhaften Test hinzugefügt wird, der darin enthalten ist. Dies ist nützlich, wenn eine Reihe verwandter Tests an einem größeren Objekt durchgeführt wird und es wünschenswert ist, dieses größere Objekt anzuzeigen, wenn einer der einzelnen Tests fehlschlägt. Transparente Testsets führen nicht zu zusätzlichen Ebenen der Verschachtelung in der Testset-Hierarchie und werden direkt an das übergeordnete Testset weitergegeben (mit dem Kontextobjekt, das an alle fehlerhaften Tests angehängt wird).

!!! compat "Julia 1.9"
    `@testset let` erfordert mindestens Julia 1.9.


!!! compat "Julia 1.10"
    Mehrere `let`-Zuweisungen werden seit Julia 1.10 unterstützt.


## Beispiele

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
Test Failed at none:3
  Expression: !(iszero(real(logi)))
     Context: logi = 0.0 + 1.5707963267948966im

ERROR: Es gab einen Fehler während des Tests

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
Test Failed at none:3
  Expression: op(real(logi))
     Context: logi = 0.0 + 1.5707963267948966im
              op = !iszero

ERROR: Es gab einen Fehler während des Tests
```

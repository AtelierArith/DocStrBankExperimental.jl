```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

Testen Sie, ob der Ausdruck `ex` zu `true` evaluiert. Wenn er innerhalb eines `@testset` ausgeführt wird, geben Sie ein `Pass` `Result` zurück, wenn dies der Fall ist, ein `Fail` `Result`, wenn es `false` ist, und ein `Error` `Result`, wenn es nicht evaluiert werden konnte. Wenn es außerhalb eines `@testset` ausgeführt wird, werfen Sie stattdessen eine Ausnahme, anstatt `Fail` oder `Error` zurückzugeben.

# Beispiele

```jldoctest
julia> @test true
Test Bestanden

julia> @test [1, 2] + [2, 1] == [3, 3]
Test Bestanden
```

Die Form `@test f(args...) key=val...` ist äquivalent zu `@test f(args..., key=val...)`, was nützlich sein kann, wenn der Ausdruck ein Aufruf mit Infix-Syntax ist, wie z. B. ungefähre Vergleiche:

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
Test Bestanden
```

Dies ist äquivalent zu dem unansehnlicheren Test `@test ≈(π, 3.14, atol=0.01)`. Es ist ein Fehler, mehr als einen Ausdruck anzugeben, es sei denn, der erste ist ein Aufrufausdruck und der Rest sind Zuweisungen (`k=v`).

Sie können jeden Schlüssel für die `key=val` Argumente verwenden, außer für `broken` und `skip`, die im Kontext von `@test` spezielle Bedeutungen haben:

  * `broken=cond` zeigt einen Test an, der bestehen sollte, aber derzeit konsequent fehlschlägt, wenn `cond==true`.  Tests, dass der Ausdruck `ex` zu `false` evaluiert oder eine Ausnahme verursacht. Gibt ein `Broken` `Result` zurück, wenn dies der Fall ist, oder ein `Error` `Result`, wenn der Ausdruck zu `true` evaluiert. Der reguläre `@test ex` wird evaluiert, wenn `cond==false`.
  * `skip=cond` kennzeichnet einen Test, der nicht ausgeführt werden sollte, aber in der Testzusammenfassungsberichterstattung als `Broken` enthalten sein sollte, wenn `cond==true`.  Dies kann nützlich sein für Tests, die intermittierend fehlschlagen, oder Tests von noch nicht implementierten Funktionen. Der reguläre `@test ex` wird evaluiert, wenn `cond==false`.

# Beispiele

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
Test Broken
  Ausdruck: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
Test Bestanden

julia> @test 2 + 2 == 5 skip=true
Test Broken
  Übersprungen: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
Test Bestanden
```

!!! compat "Julia 1.7"
    Die Schlüsselwortargumente `broken` und `skip` erfordern mindestens Julia 1.7.


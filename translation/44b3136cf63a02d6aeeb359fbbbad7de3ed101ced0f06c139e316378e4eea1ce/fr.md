```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia est en cours de développement rapide et dispose d'une vaste suite de tests pour vérifier la fonctionnalité sur plusieurs plateformes. Si vous construisez Julia à partir du code source, vous pouvez exécuter cette suite de tests avec `make test`. Dans une installation binaire, vous pouvez exécuter la suite de tests en utilisant `Base.runtests()`.

```@docs
Base.runtests
```

## Basic Unit Tests

Le module `Test` fournit une fonctionnalité simple de *tests unitaires*. Les tests unitaires sont un moyen de vérifier si votre code est correct en vérifiant que les résultats correspondent à vos attentes. Cela peut être utile pour s'assurer que votre code fonctionne toujours après avoir apporté des modifications, et peut être utilisé lors du développement comme un moyen de spécifier les comportements que votre code devrait avoir une fois terminé. Vous voudrez peut-être également consulter la documentation pour [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package).

Des tests unitaires simples peuvent être effectués avec les macros `@test` et `@test_throws` :

```@docs
Test.@test
Test.@test_throws
```

Par exemple, supposons que nous voulons vérifier que notre nouvelle fonction `foo(x)` fonctionne comme prévu :

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

Si la condition est vraie, un `Pass` est retourné :

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

Si la condition est fausse, alors un `Échec` est renvoyé et une exception est levée :

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

Si la condition ne pouvait pas être évaluée en raison d'une exception levée, ce qui se produit dans ce cas parce que `length` n'est pas défini pour les symboles, un objet `Error` est renvoyé et une exception est levée :

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

Si nous nous attendons à ce qu'évaluer une expression *doit* lancer une exception, alors nous pouvons utiliser `@test_throws` pour vérifier que cela se produit :

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

Typiquement, un grand nombre de tests sont utilisés pour s'assurer que les fonctions fonctionnent correctement sur une gamme d'entrées. Dans le cas où un test échoue, le comportement par défaut est de lancer une exception immédiatement. Cependant, il est généralement préférable d'exécuter le reste des tests d'abord pour avoir une meilleure idée du nombre d'erreurs dans le code testé.

!!! note
    Le `@testset` créera un scope local à lui-même lors de l'exécution des tests qu'il contient.


Le macro `@testset` peut être utilisé pour regrouper des tests en *ensembles*. Tous les tests d'un ensemble de tests seront exécutés, et à la fin de l'ensemble de tests, un résumé sera imprimé. Si l'un des tests a échoué, ou n'a pas pu être évalué en raison d'une erreur, l'ensemble de tests lancera alors une `TestSetException`.

```@docs
Test.@testset
Test.TestSetException
```

Nous pouvons mettre nos tests pour la fonction `foo(x)` dans un ensemble de tests :

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

Les ensembles de tests peuvent également être imbriqués :

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

Ainsi que des fonctions d'appel :

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

Cela peut être utilisé pour permettre la factorisation des ensembles de tests, facilitant ainsi l'exécution d'ensembles de tests individuels en exécutant plutôt les fonctions associées. Notez que dans le cas des fonctions, l'ensemble de tests portera le nom de la fonction appelée. Dans le cas où un ensemble de tests imbriqué n'a pas d'échecs, comme c'est le cas ici, il sera masqué dans le résumé, à moins que l'option `verbose=true` ne soit passée :

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

Si nous avons un échec de test, seuls les détails des ensembles de tests échoués seront affichés :

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

On peut utiliser la macro [`@test_logs`](@ref) pour tester les déclarations de journal, ou utiliser un [`TestLogger`](@ref).

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

Comme les calculs sur des valeurs à virgule flottante peuvent être imprécis, vous pouvez effectuer des vérifications d'égalité approximative en utilisant soit `@test a ≈ b` (où `≈`, tapé via la complétion par tabulation de `\approx`, est la fonction [`isapprox`](@ref)) ou utiliser `4d61726b646f776e2e436f64652822222c20226973617070726f782229_40726566` directement.

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

Vous pouvez spécifier des tolérances relatives et absolues en définissant les arguments de mot-clé `rtol` et `atol` de `isapprox`, respectivement, après la comparaison `≈` :

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

Notez que ce n'est pas une fonctionnalité spécifique de `≈`, mais plutôt une fonctionnalité générale de la macro `@test` : `@test a <op> b key=val` est transformé par la macro en `@test op(a, b, key=val)`. Cela dit, c'est particulièrement utile pour les tests `≈`.

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

Si un test échoue de manière constante, il peut être modifié pour utiliser le macro `@test_broken`. Cela désignera le test comme `Broken` si le test continue d'échouer et alertera l'utilisateur via une `Error` si le test réussit.

```@docs
Test.@test_broken
```

`@test_skip` est également disponible pour ignorer un test sans évaluation, mais en comptant le test ignoré dans le rapport du jeu de tests. Le test ne s'exécutera pas mais donnera un `Résultat` `Cassé`.

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

Les packages peuvent créer leurs propres sous-types `AbstractTestSet` en implémentant les méthodes `record` et `finish`. Le sous-type doit avoir un constructeur à un argument prenant une chaîne de description, avec toutes les options passées en tant qu'arguments nommés.

```@docs
Test.record
Test.finish
```

`Test` prend la responsabilité de maintenir une pile de jeux de tests imbriqués au fur et à mesure de leur exécution, mais toute accumulation de résultats est de la responsabilité du sous-type `AbstractTestSet`. Vous pouvez accéder à cette pile avec les méthodes `get_testset` et `get_testset_depth`. Notez que ces fonctions ne sont pas exportées.

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test` s'assure également que les invocations imbriquées de `@testset` utilisent le même sous-type `AbstractTestSet` que leur parent, sauf si cela est défini explicitement. Il ne propage aucune propriété du testset. Le comportement d'héritage des options peut être implémenté par des packages en utilisant l'infrastructure de pile que `Test` fournit.

Définir un sous-type de base `AbstractTestSet` pourrait ressembler à :

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

Et en utilisant cet ensemble de test, cela ressemble à :

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

Pour utiliser un ensemble de tests personnalisé et avoir les résultats enregistrés imprimés comme partie de tout ensemble de tests par défaut extérieur, définissez également `Test.get_test_counts`. Cela pourrait ressembler à ceci :

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

En utilisant les outils disponibles dans les sections précédentes, voici un flux de travail potentiel pour créer un package et y ajouter des tests.

### Generating an Example Package

Pour ce flux de travail, nous allons créer un package appelé `Example` :

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

La condition numéro un pour tester un package est d'avoir une fonctionnalité à tester. Pour cela, nous allons ajouter quelques fonctions simples à `Example` que nous pouvons tester. Ajoutez ce qui suit à `src/Example.jl` :

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

Depuis la racine du package `Example`, naviguez vers le répertoire `test`, activez un nouvel environnement là-bas et ajoutez le package `Test` à l'environnement :

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

Maintenant, nous sommes prêts à ajouter des tests à `Example`. Il est d'usage de créer un fichier dans le répertoire `test` appelé `runtests.jl` qui contient les ensembles de tests que nous voulons exécuter. Allez-y et créez ce fichier dans le répertoire `test` et ajoutez-y le code suivant :

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

Nous devrons créer ces deux fichiers inclus, `math_tests.jl` et `greeting_tests.jl`, et y ajouter quelques tests.

> **Remarque :** Remarquez comment nous n'avons pas eu besoin de spécifier d'ajouter `Example` dans le fichier `Project.toml` de l'environnement `test`. C'est un avantage du système de test de Julia que vous pourriez [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/).


#### Writing Tests for `math_tests.jl`

En utilisant nos connaissances de `Test.jl`, voici quelques tests d'exemple que nous pourrions ajouter à `math_tests.jl` :

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

En utilisant nos connaissances de `Test.jl`, voici quelques tests d'exemple que nous pourrions ajouter à `greeting_tests.jl` :

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

Maintenant que nous avons ajouté nos tests et notre script `runtests.jl` dans `test`, nous pouvons tester notre package `Example` en revenant à la racine de l'environnement du package `Example` et en réactivant l'environnement `Example` :

```julia
shell> cd ..
pkg> activate .
```

À partir de là, nous pouvons enfin exécuter notre suite de tests comme suit :

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

Et si tout s'est bien passé, vous devriez voir une sortie similaire à celle ci-dessus. En utilisant `Test.jl`, des tests plus compliqués peuvent être ajoutés pour les packages, mais cela devrait idéalement orienter les développeurs sur la façon de commencer à tester leurs propres packages créés.

```@meta
DocTestSetup = nothing
```

### Code Coverage

Le suivi de la couverture de code pendant les tests peut être activé en utilisant le drapeau `pkg> test --coverage` (ou à un niveau inférieur en utilisant l'argument julia [`--code-coverage`](@ref command-line-interface)). Cela est activé par défaut dans l'action GitHub [julia-runtest](https://github.com/julia-actions/julia-runtest).

To evaluate coverage either manually inspect the `.cov` files that are generated beside the source files locally, or in CI use the [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub action.

!!! compat "Julia 1.11"
    Depuis Julia 1.11, la couverture n'est pas collectée pendant la phase de précompilation des paquets.


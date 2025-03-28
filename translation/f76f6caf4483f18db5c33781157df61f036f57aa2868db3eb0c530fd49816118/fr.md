```
@testset [CustomTestSet] [options...] ["description"] begin test_ex end
@testset [CustomTestSet] [options...] ["description $v"] for v in itr test_ex end
@testset [CustomTestSet] [options...] ["description $v, $w"] for v in itrv, w in itrw test_ex end
@testset [CustomTestSet] [options...] ["description"] test_func()
@testset let v = v, w = w; test_ex; end
```

# Avec begin/end ou appel de fonction

Lorsque @testset est utilisé, avec begin/end ou un seul appel de fonction, la macro commence un nouveau test set dans lequel évaluer l'expression donnée.

Si aucun type de testset personnalisé n'est donné, il crée par défaut un `DefaultTestSet`. `DefaultTestSet` enregistre tous les résultats et, s'il y a des `Fail`s ou des `Error`s, lance une exception à la fin du test set de niveau supérieur (non imbriqué), accompagnée d'un résumé des résultats des tests.

Tout type de testset personnalisé (sous-type de `AbstractTestSet`) peut être donné et sera également utilisé pour toute invocation imbriquée de `@testset`. Les options données ne s'appliquent qu'au test set où elles sont fournies. Le type de test set par défaut accepte trois options booléennes :

  * `verbose` : si `true`, le résumé des résultats des testsets imbriqués est affiché même lorsqu'ils passent tous (la valeur par défaut est `false`).
  * `showtiming` : si `true`, la durée de chaque testset affiché est montrée (la valeur par défaut est `true`).
  * `failfast` : si `true`, tout échec de test ou erreur fera que le testset et tous les testsets enfants retourneront immédiatement (la valeur par défaut est `false`). Cela peut également être défini globalement via la variable d'environnement `JULIA_TEST_FAILFAST`.

!!! compat "Julia 1.8"
    `@testset test_func()` nécessite au moins Julia 1.8.


!!! compat "Julia 1.9"
    `failfast` nécessite au moins Julia 1.9.


La chaîne de description accepte l'interpolation des indices de boucle. Si aucune description n'est fournie, une est construite en fonction des variables. Si un appel de fonction est fourni, son nom sera utilisé. Les chaînes de description explicites remplacent ce comportement.

Par défaut, la macro `@testset` renverra l'objet testset lui-même, bien que ce comportement puisse être personnalisé dans d'autres types de testset. Si une boucle `for` est utilisée, alors la macro collecte et renvoie une liste des valeurs de retour de la méthode `finish`, qui par défaut renverra une liste des objets testset utilisés à chaque itération.

Avant l'exécution du corps d'un `@testset`, il y a un appel implicite à `Random.seed!(seed)` où `seed` est la graine actuelle du RNG global. De plus, après l'exécution du corps, l'état du RNG global est restauré à ce qu'il était avant le `@testset`. Cela vise à faciliter la reproductibilité en cas d'échec et à permettre des réarrangements transparents des `@testset` indépendamment de leur effet secondaire sur l'état du RNG global.

## Exemples

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

Lorsque `@testset for` est utilisé, la macro commence un nouveau test pour chaque itération de la boucle fournie. La sémantique de chaque test set est autrement identique à celle du cas `begin/end` (comme si utilisé pour chaque itération de boucle).

# `@testset let`

Lorsque `@testset let` est utilisé, la macro commence un test set *transparent* avec l'objet donné ajouté comme objet de contexte à tout test échouant contenu dans celui-ci. Cela est utile lors de l'exécution d'un ensemble de tests liés sur un objet plus grand et il est souhaitable d'imprimer cet objet plus grand lorsque l'un des tests individuels échoue. Les test sets transparents n'introduisent pas de niveaux supplémentaires d'imbrication dans la hiérarchie des test sets et sont transmis directement au test set parent (avec l'objet de contexte ajouté à tout test échouant).

!!! compat "Julia 1.9"
    `@testset let` nécessite au moins Julia 1.9.


!!! compat "Julia 1.10"
    Plusieurs affectations `let` sont prises en charge depuis Julia 1.10.


## Exemples

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
Test Failed at none:3
  Expression: !(iszero(real(logi)))
     Context: logi = 0.0 + 1.5707963267948966im

ERROR: Il y a eu une erreur pendant le test

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
Test Failed at none:3
  Expression: op(real(logi))
     Context: logi = 0.0 + 1.5707963267948966im
              op = !iszero

ERROR: Il y a eu une erreur pendant le test
```

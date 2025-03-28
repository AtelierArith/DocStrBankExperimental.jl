```
Base.@assume_effects réglage... [ex]
```

Surchargez la modélisation des effets du compilateur. Cette macro peut être utilisée dans plusieurs contextes :

1. Immédiatement avant une définition de méthode, pour remplacer la modélisation des effets de la méthode appliquée.
2. Dans le corps d'une fonction sans arguments, pour remplacer la modélisation des effets de la méthode englobante.
3. Appliquée à un bloc de code, pour remplacer la modélisation locale des effets du bloc de code appliqué.

# Exemples

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # utilisation 1 :
           # ce :terminates_locally permet à `fact` d'être constant plié
           res = 1
           0 ≤ x < 20 || error("mauvais fact")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generic function with 1 method)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # utilisation 2 :
               # ce :terminates_locally permet à cette fonction anonyme d'être constant pliée
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("mauvais fact")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("mauvais fact")
               # utilisation 3 :
               # avec cette annotation :terminates_locally, le compilateur évite de marquer
               # l'effet `:terminates` dans ce bloc `while`, permettant à la fonction
               # anonyme parente d'être constant pliée
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    L'utilisation de `Base.@assume_effects` nécessite la version Julia 1.8.


!!! compat "Julia 1.10"
    L'utilisation dans le corps d'une fonction nécessite au moins Julia 1.10.


!!! compat "Julia 1.11"
    L'annotation de bloc de code nécessite au moins Julia 1.11.


!!! warning
    Une utilisation incorrecte de cette macro entraîne un comportement indéfini (y compris des plantages, des réponses incorrectes ou d'autres bogues difficiles à suivre). Utilisez avec précaution et uniquement en dernier recours si absolument nécessaire. Même dans ce cas, vous DEVEZ prendre toutes les mesures possibles pour minimiser la force de l'assertion d'effet (par exemple, ne pas utiliser `:total` si `:nothrow` aurait été suffisant).


En général, chaque valeur de `réglage` fait une assertion sur le comportement de la fonction, sans exiger que le compilateur prouve que ce comportement est effectivement vrai. Ces assertions sont faites pour tous les âges du monde. Il est donc conseillé de limiter l'utilisation de fonctions génériques qui pourraient être étendues ultérieurement pour invalider l'hypothèse (ce qui entraînerait un comportement indéfini).

Les `réglages` suivants sont pris en charge.

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# Aide étendue

---

## `:consistent`

Le réglage `:consistent` affirme que pour des entrées égales (`===`) :

  * La manière de terminaison (valeur de retour, exception, non-termination) sera toujours la même.
  * Si la méthode retourne, les résultats seront toujours égaux.

!!! note
    Cela implique en particulier que la méthode ne doit pas retourner un objet mutable nouvellement alloué. Plusieurs allocations d'objets mutables (même avec un contenu identique) ne sont pas égales.


!!! note
    L'assertion `:consistent` est faite par âge du monde. Plus formellement, écrivez $fᵢ$ pour l'évaluation de $f$ dans l'âge du monde $i$, alors ce réglage exige :

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    Cependant, pour deux âges du monde $i$, $j$ tels que $i ≠ j$, nous pouvons avoir $fᵢ(x) ≢ fⱼ(y)$.

    Une autre implication est que les fonctions `:consistent` ne peuvent pas rendre leur valeur de retour dépendante de l'état du tas ou de tout autre état global qui n'est pas constant pour un âge du monde donné.


!!! note
    Les fonctions `:consistent` incluent toutes les réécritures légales effectuées par l'optimiseur. Par exemple, les opérations fastmath en virgule flottante ne sont pas considérées comme `:consistent`, car l'optimiseur peut les réécrire, ce qui entraîne une sortie qui n'est pas `:consistent`, même pour le même âge du monde (par exemple, parce qu'une a été exécutée dans l'interpréteur, tandis que l'autre a été optimisée).


!!! note
    Si les fonctions `:consistent` se terminent en lançant une exception, cette exception elle-même n'est pas requise pour répondre à l'exigence d'égalité spécifiée ci-dessus.


---

## `:effect_free`

Le réglage `:effect_free` affirme que la méthode est exempte d'effets secondaires sémantiquement visibles externes. La liste suivante est une liste incomplète d'effets secondaires sémantiquement visibles externes :

  * Changer la valeur d'une variable globale.
  * Muter le tas (par exemple, un tableau ou une valeur mutable), sauf comme noté ci-dessous.
  * Changer la table des méthodes (par exemple, par des appels à eval).
  * I/O de fichiers/réseau/etc.
  * Changement de tâche.

Cependant, les éléments suivants ne sont explicitement pas visibles sémantiquement, même s'ils peuvent être observables :

  * Allocations de mémoire (à la fois mutables et immuables).
  * Temps écoulé.
  * Collecte des ordures.
  * Mutations du tas d'objets dont la durée de vie ne dépasse pas la méthode (c'est-à-dire qui ont été alloués dans la méthode et ne s'échappent pas).
  * La valeur retournée (qui est visible de l'extérieur, mais pas un effet secondaire).

La règle générale ici est qu'un effet secondaire visible de l'extérieur est tout ce qui affecterait l'exécution du reste du programme si la fonction n'était pas exécutée.

!!! note
    L'assertion `:effect_free` est faite à la fois pour la méthode elle-même et tout code exécuté par la méthode. Gardez à l'esprit que l'assertion doit être valide pour tous les âges du monde et limitez l'utilisation de cette assertion en conséquence.


---

## `:nothrow`

Le réglage `:nothrow` affirme que cette méthode ne lance pas d'exception (c'est-à-dire qu'elle retournera toujours une valeur ou ne retournera jamais).

!!! note
    Il est permis aux méthodes annotées `:nothrow` d'utiliser la gestion des exceptions en interne tant que l'exception n'est pas relancée en dehors de la méthode elle-même.


!!! note
    Si l'exécution d'une méthode peut lever des `MethodError` et des exceptions similaires, alors la méthode n'est pas considérée comme `:nothrow`. Cependant, notez que les erreurs dépendantes de l'environnement comme `StackOverflowError` ou `InterruptException` ne sont pas modélisées par cet effet et donc une méthode qui peut entraîner un `StackOverflowError` n'a pas nécessairement besoin d'être `!:nothrow` (bien qu'elle devrait généralement être `!:terminates` aussi).


---

## `:terminates_globally`

Le réglage `:terminates_globally` affirme que cette méthode se terminera éventuellement (soit normalement, soit anormalement), c'est-à-dire qu'elle ne boucle pas indéfiniment.

!!! note
    Cette assertion `:terminates_globally` couvre toutes les autres méthodes appelées par la méthode annotée.


!!! note
    Le compilateur considérera cela comme une forte indication que la méthode se terminera relativement *rapidement* et peut (si autrement légal) appeler cette méthode à la compilation. C'est-à-dire qu'il est une mauvaise idée d'annoter ce réglage sur une méthode qui *techniquement*, mais pas *pratiquement*, se termine.


---

## `:terminates_locally`

Le réglage `:terminates_locally` est comme `:terminates_globally`, sauf qu'il ne s'applique qu'au flux de contrôle syntaxique *dans* la méthode annotée. C'est donc une assertion beaucoup plus faible (et donc plus sûre) qui permet la possibilité de non-termination si la méthode appelle une autre méthode qui ne se termine pas.

!!! note
    `:terminates_globally` implique `:terminates_locally`.


---

## `:notaskstate`

Le réglage `:notaskstate` affirme que la méthode n'utilise ni ne modifie l'état de tâche local (stockage local de tâche, état RNG, etc.) et peut donc être déplacée en toute sécurité entre les tâches sans résultats observables.

!!! note
    L'implémentation de la gestion des exceptions utilise un état stocké dans l'objet tâche. Cependant, cet état n'est actuellement pas considéré comme étant dans le champ d'application de `:notaskstate` et est suivi séparément à l'aide de l'effet `:nothrow`.


!!! note
    L'assertion `:notaskstate` concerne l'état de la *tâche actuellement en cours d'exécution*. Si une référence à un objet `Task` est obtenue par d'autres moyens qui ne tiennent pas compte de la tâche qui est *actuellement* en cours d'exécution, l'effet `:notaskstate` n'a pas besoin d'être marqué. Cela est vrai, même si cet objet tâche se trouve être `===` à la tâche actuellement en cours d'exécution.


!!! note
    L'accès à l'état de la tâche entraîne généralement également le marquage d'autres effets, tels que `:effect_free` (si l'état de la tâche est modifié) ou `:consistent` (si l'état de la tâche est utilisé dans le calcul du résultat). En particulier, le code qui n'est pas `:notaskstate`, mais qui est `:effect_free` et `:consistent` peut toujours être éliminé comme code mort et donc promu à `:total`.


---

## `:inaccessiblememonly`

Le réglage `:inaccessiblememonly` affirme que la méthode n'accède ni ne modifie la mémoire mutable accessible de l'extérieur. Cela signifie que la méthode peut accéder ou modifier la mémoire mutable pour des objets nouvellement alloués qui ne sont pas accessibles par d'autres méthodes ou exécutions de niveau supérieur avant le retour de la méthode, mais elle ne peut pas accéder ou modifier un état global mutable ou une mémoire mutable pointée par ses arguments.

!!! note
    Ci-dessous se trouve une liste incomplète d'exemples qui invalident cette hypothèse :

      * une référence globale ou un appel `getglobal` pour accéder à une variable globale mutable
      * une affectation globale ou un appel `setglobal!` pour effectuer une affectation à une variable globale non constante
      * un appel `setfield!` qui change un champ d'une variable mutable globale


!!! note
    Cette assertion `:inaccessiblememonly` couvre toutes les autres méthodes appelées par la méthode annotée.


---

## `:noub`

Le réglage `:noub` affirme que la méthode n'exécutera aucun comportement indéfini (pour toute entrée). Notez que le comportement indéfini peut techniquement amener la méthode à violer d'autres assertions d'effet (telles que `:consistent` ou `:effect_free`), mais nous ne modélisons pas cela, et elles supposent l'absence de comportement indéfini.

---

## `:nortcall`

Le réglage `:nortcall` affirme que la méthode n'appelle pas `Core.Compiler.return_type`, et que toutes les autres méthodes que cette méthode pourrait appeler n'appellent également pas `Core.Compiler.return_type`.

!!! note
    Pour être précis, cette assertion peut être utilisée lorsqu'un appel à `Core.Compiler.return_type` n'est pas effectué à l'exécution ; c'est-à-dire lorsque le résultat de `Core.Compiler.return_type` est connu exactement à la compilation et que l'appel est éliminé par l'optimiseur. Cependant, étant donné que la question de savoir si le résultat de `Core.Compiler.return_type` est plié à la compilation dépend fortement de l'implémentation du compilateur, il est généralement risqué d'affirmer cela si la méthode en question utilise `Core.Compiler.return_type` sous une forme quelconque.


---

## `:foldable`

Ce réglage est un raccourci pratique pour l'ensemble des effets que le compilateur exige pour garantir le pliage constant d'un appel à la compilation. Il est actuellement équivalent aux `réglages` suivants :

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    Cette liste, en particulier, n'inclut pas `:nothrow`. Le compilateur tentera toujours la propagation constante et notera toute erreur lancée à la compilation. Notez cependant qu'en raison des exigences de `:consistent`, tout appel annoté de cette manière doit lancer de manière cohérente pour les mêmes valeurs d'argument.


!!! note
    Une annotation explicite `@inbounds` à l'intérieur de la fonction désactivera également le pliage constant et ne sera pas remplacée par `:foldable`.


---

## `:removable`

Ce réglage est un raccourci pratique pour l'ensemble des effets que le compilateur exige pour garantir la suppression d'un appel dont le résultat est inutilisé à la compilation. Il est actuellement équivalent aux `réglages` suivants :

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

Ce `réglage` est le maximum possible d'effets. Il implique actuellement les autres `réglages` suivants :

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total` est une assertion très forte et gagnera probablement des sémantiques supplémentaires dans les futures versions de Julia (par exemple, si des effets supplémentaires sont ajoutés et inclus dans la définition de `:total`). En conséquence, il doit être utilisé avec précaution. Chaque fois que cela est possible, il est préférable d'utiliser l'ensemble minimum possible d'assertions d'effet spécifiques requises pour une application particulière. Dans les cas où un grand nombre de remplacements d'effet s'appliquent à un ensemble de fonctions, une macro personnalisée est recommandée plutôt que l'utilisation de `:total`.


---

## Effets niés

Les noms d'effet peuvent être préfixés par `!` pour indiquer que l'effet doit être supprimé d'un effet méta précédent. Par exemple, `:total !:nothrow` indique que bien que l'appel soit généralement total, il peut cependant lancer.

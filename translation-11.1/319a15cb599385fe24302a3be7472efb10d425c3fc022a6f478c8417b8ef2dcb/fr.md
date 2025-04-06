# Working with LLVM

Ce n'est pas un remplacement pour la documentation LLVM, mais une collection de conseils pour travailler sur LLVM pour Julia.

## Overview of Julia to LLVM Interface

Julia lie par défaut contre LLVM de manière dynamique. Construisez avec `USE_LLVM_SHLIB=0` pour lier statiquement.

Le code pour abaisser l'AST de Julia vers l'IR LLVM ou l'interpréter directement se trouve dans le répertoire `src/`.

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

Certains des fichiers `.cpp` forment un groupe qui se compile en un seul objet.

La différence entre un intrinsèque et un intégré est qu'un intégré est une fonction de première classe qui peut être utilisée comme n'importe quelle autre fonction Julia. Un intrinsèque ne peut opérer que sur des données non encapsulées, et par conséquent, ses arguments doivent être typés statiquement.

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia currently uses LLVM's [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata). To find the comments that document the inclusion relationships, look for `static MDNode*` in `src/codegen.cpp`.

L'option `-O` active [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass) de LLVM.

## Building Julia with a different version of LLVM

La version par défaut de LLVM est spécifiée dans `deps/llvm.version`. Vous pouvez la remplacer en créant un fichier appelé `Make.user` dans le répertoire de niveau supérieur et en y ajoutant une ligne comme :

```
LLVM_VER = 13.0.0
```

En plus des numéros de version d'LLVM, vous pouvez également utiliser `DEPS_GIT = llvm` en combinaison avec `USE_BINARYBUILDER_LLVM = 0` pour construire contre la dernière version de développement d'LLVM.

Vous pouvez également spécifier de construire une version de débogage d'LLVM, en définissant soit `LLVM_DEBUG = 1` soit `LLVM_DEBUG = Release` dans votre fichier `Make.user`. Le premier sera une construction entièrement non optimisée d'LLVM et le second produira une construction optimisée d'LLVM. Selon vos besoins, ce dernier suffira et sera beaucoup plus rapide. Si vous utilisez `LLVM_DEBUG = Release`, vous voudrez également définir `LLVM_ASSERTIONS = 1` pour activer les diagnostics pour différents passes. Seul `LLVM_DEBUG = 1` implique cette option par défaut.

## Passing options to LLVM

Vous pouvez passer des options à LLVM via la variable d'environnement [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS). Voici des exemples de paramètres utilisant la syntaxe `bash` :

  * `export JULIA_LLVM_ARGS=-print-after-all` génère IR après chaque passage.
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize` génère des diagnostics `DEBUG(...)` LLVM pour le vectoriseur de boucle. Si vous recevez des avertissements concernant "Argument de ligne de commande inconnu", reconstruisez LLVM avec `LLVM_ASSERTIONS = 1`.
  * `export JULIA_LLVM_ARGS=-help` affiche une liste des options disponibles. `export JULIA_LLVM_ARGS=-help-hidden` affiche encore plus d'options.
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"` est un exemple de la façon d'utiliser plusieurs options.

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`: imprime l'IR après toute exécution de `PASS`, utile pour vérifier les modifications apportées par un passage.
  * `-print-before=PASS`: imprime l'IR avant toute exécution de `PASS`, utile pour vérifier l'entrée d'un passage.
  * `-print-changed`: imprime l'IR chaque fois qu'un passage modifie l'IR, utile pour identifier quels passages causent des problèmes.
  * `-print-(before|after)=MARQUE-PASS`: le pipeline Julia est livré avec un certain nombre de passes de marque dans le pipeline, qui peuvent être utilisées pour identifier où des problèmes ou des optimisations se produisent. Une passe de marque est définie comme une passe qui apparaît une fois dans le pipeline et ne réalise aucune transformation sur l'IR, et n'est utile que pour cibler print-before/print-after. Actuellement, les passes de marque suivantes existent dans le pipeline :

      * AvantOptimisation
      * AvantSimplificationPrécoce
      * AprèsSimplificationPrécoce
      * AvantOptimisationPrécoce
      * AprèsOptimisationPrécoce
      * AvantOptimisationBoucle
      * AvantLICM
      * AprèsLICM
      * AvantLaSimplificationDeBoucle
      * AprèsSimplificationDeBoucle
      * AprèsOptimisationDeBoucle
      * AvantOptimisationScalaire
      * AprèsOptimisationScalaire
      * AvantVectorisation
      * AprèsVectorisation
      * AvantRéductionIntrinsèque
      * AprèsAbaissementIntrinsèque
      * AvantNettoyage
      * AprèsNettoyage
      * AprèsOptimisation
  * `-time-passes`: imprime le temps passé à chaque passe, utile pour identifier quelles passes prennent beaucoup de temps.
  * `-print-module-scope`: utilisé en conjonction avec `-print-(before|after)`, obtient l'ensemble du module plutôt que l'unité IR reçue par le passage.
  * `-debug`: imprime beaucoup d'informations de débogage dans tout LLVM
  * `-debug-only=NAME`, imprime des déclarations de débogage à partir de fichiers avec `DEBUG_TYPE` défini sur `NAME`, utile pour obtenir un contexte supplémentaire sur un problème.

## Debugging LLVM transformations in isolation

Il peut parfois être utile de déboguer les transformations d'LLVM de manière isolée du reste du système Julia, par exemple parce que reproduire le problème à l'intérieur de `julia` prendrait trop de temps, ou parce qu'on souhaite tirer parti des outils d'LLVM (par exemple, bugpoint).

Pour commencer, vous pouvez installer les outils de développement pour travailler avec LLVM via :

```
make -C deps install-llvm-tools
```

Pour obtenir un IR non optimisé pour l'ensemble de l'image système, passez l'option `--output-unopt-bc unopt.bc` au processus de construction de l'image système, ce qui générera l'IR non optimisé dans un fichier `unopt.bc`. Ce fichier peut ensuite être passé aux outils LLVM comme d'habitude. `libjulia` peut fonctionner comme un plugin de passage LLVM et peut être chargé dans les outils LLVM, pour rendre les passages spécifiques à Julia disponibles dans cet environnement. De plus, il expose le méta-passage `-julia`, qui exécute l'ensemble du pipeline de passages Julia sur l'IR. Par exemple, pour générer une image système avec l'ancien gestionnaire de passages, on pourrait faire :

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Pour générer une image système avec le nouveau gestionnaire de mots de passe, on pourrait faire :

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Cette image système peut ensuite être chargée par `julia` comme d'habitude.

Il est également possible d'extraire un module LLVM IR pour une seule fonction Julia, en utilisant :

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

Ces fichiers peuvent être traités de la même manière que l'IR sysimg non optimisé montré ci-dessus.

## Running the LLVM test suite

Pour exécuter les tests llvm localement, vous devez d'abord installer les outils, construire julia, puis vous pouvez exécuter les tests :

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

Si vous souhaitez exécuter les fichiers de test individuels directement, via les commandes en haut de chaque fichier de test, la première étape ici aura installé les outils dans `./usr/tools/opt`. Ensuite, vous voudrez remplacer manuellement `%s` par le nom du fichier de test.

## Improving LLVM optimizations for Julia

Améliorer la génération de code LLVM implique généralement soit de modifier la réduction de Julia pour être plus conviviale avec les passes de LLVM, soit d'améliorer une passe.

Si vous prévoyez d'améliorer un pass, assurez-vous de lire le [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html). La meilleure stratégie est de créer un exemple de code sous une forme où vous pouvez utiliser l'outil `opt` d'LLVM pour l'étudier ainsi que le pass d'intérêt en isolation.

1. Create an example Julia code of interest.
2. Utilisez `JULIA_LLVM_ARGS=-print-after-all` pour afficher l'IR.
3. Repérez l'IR au point juste avant que le passage d'intérêt ne s'exécute.
4. Supprimez les métadonnées de débogage et corrigez manuellement les métadonnées TBAA.

La dernière étape est laborieuse. Des suggestions pour une meilleure méthode seraient appréciées.

## The jlcall calling convention

Julia a une convention d'appel générique pour le code non optimisé, qui ressemble quelque peu à ceci :

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

où le premier argument est l'objet de fonction encapsulé, le deuxième argument est un tableau d'arguments sur la pile et le troisième est le nombre d'arguments. Maintenant, nous pourrions effectuer une réduction directe et émettre un alloca pour le tableau d'arguments. Cependant, cela trahirait la nature SSA des utilisations au site d'appel, rendant les optimisations (y compris le placement des racines GC) considérablement plus difficiles. Au lieu de cela, nous l'émettons comme suit :

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

Cela nous permet de conserver le caractère SSA des utilisations tout au long de l'optimiseur. Le placement des racines GC réduira plus tard cet appel à l'ABI C d'origine.

## GC root placement

Le placement des racines GC est effectué par un passage LLVM tard dans le pipeline de passages. Effectuer le placement des racines GC aussi tard permet à LLVM de réaliser des optimisations plus agressives autour du code qui nécessite des racines GC, tout en nous permettant de réduire le nombre de racines GC requises et d'opérations de stockage de racines GC (puisqu'LLVM ne comprend pas notre GC, il ne saurait autrement ce qu'il est et n'est pas autorisé à faire avec les valeurs stockées dans le cadre GC, donc il agira de manière conservatrice et fera très peu). Par exemple, considérons un chemin d'erreur.

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

Lors de l'évaluation constante, LLVM peut découvrir que la condition est toujours fausse et peut supprimer le bloc de base. Cependant, si l'abaissement des racines GC est effectué trop tôt, les emplacements de racines GC utilisés dans le bloc supprimé, ainsi que toutes les valeurs maintenues en vie dans ces emplacements uniquement parce qu'elles étaient utilisées dans le chemin d'erreur, seraient maintenues en vie par LLVM. En effectuant l'abaissement des racines GC tardivement, nous donnons à LLVM la licence d'effectuer toutes ses optimisations habituelles (évaluation constante, élimination de code mort, etc.), sans avoir à trop se soucier des valeurs qui peuvent ou non être suivies par le GC.

Cependant, afin de pouvoir effectuer un placement tardif des racines GC, nous devons être en mesure d'identifier a) quels pointeurs sont suivis par le GC et b) toutes les utilisations de ces pointeurs. L'objectif du passage de placement GC est donc simple :

Minimiser le nombre de racines GC nécessaires/stocks pour elles sous la contrainte qu'à chaque point de sauvegarde, tout pointeur suivi par le GC (c'est-à-dire pour lequel il existe un chemin après ce point qui contient une utilisation de ce pointeur) se trouve dans un emplacement GC.

### Representation

La principale difficulté est donc de choisir une représentation IR qui nous permette d'identifier les pointeurs suivis par le GC et leurs utilisations, même après que le programme ait été passé par l'optimiseur. Notre conception utilise trois fonctionnalités LLVM pour y parvenir :

  * Espaces d'adresses personnalisés
  * Paquets d'opérandes
  * Pointeurs non intégraux

Les espaces d'adresses personnalisés nous permettent de marquer chaque point avec un entier qui doit être préservé à travers les optimisations. Le compilateur ne peut pas insérer de conversions entre des espaces d'adresses qui n'existaient pas dans le programme original et il ne doit jamais changer l'espace d'adresses d'un pointeur lors d'une opération de chargement/stocker/etc. Cela nous permet d'annoter quels pointeurs sont suivis par le GC de manière résistante à l'optimiseur. Notez que les métadonnées ne pourraient pas atteindre le même objectif. Les métadonnées sont censées être toujours jetables sans altérer la sémantique du programme. Cependant, ne pas identifier un pointeur suivi par le GC modifie le comportement du programme résultant de manière dramatique - il va probablement planter ou retourner des résultats incorrects. Nous utilisons actuellement trois espaces d'adresses différents (leurs numéros sont définis dans `src/codegen_shared.cpp`):

  * Pointeurs suivis par le GC (actuellement 10) : Ce sont des pointeurs vers des valeurs encapsulées qui peuvent être placées dans un cadre GC. Cela équivaut de manière lâche à un pointeur `jl_value_t*` du côté C. N.B. Il est illégal d'avoir un pointeur dans cet espace d'adresses qui ne peut pas être stocké dans un emplacement GC.
  * Pointeurs dérivés (actuellement 11) : Ce sont des pointeurs qui sont dérivés d'un pointeur suivi par le GC. Les utilisations de ces pointeurs génèrent des utilisations du pointeur original. Cependant, ils n'ont pas besoin d'être eux-mêmes connus du GC. Le passage de placement des racines du GC DOIT toujours trouver le pointeur suivi par le GC à partir duquel ce pointeur est dérivé et l'utiliser comme pointeur racine.
  * Pointeurs enracinés par le callee (actuellement 12) : Il s'agit d'un espace d'adresses utilitaire pour exprimer la notion d'une valeur enracinée par le callee. Toutes les valeurs de cet espace d'adresses DOIVENT être stockables dans une racine GC (bien qu'il soit possible de relâcher cette condition à l'avenir), mais contrairement aux autres pointeurs, elles ne doivent pas être enracinées si elles sont passées à un appel (elles doivent néanmoins être enracinées si elles sont actives entre un autre point de sécurité entre la définition et l'appel).
  * Pointeurs chargés à partir d'un objet suivi (actuellement 13) : Cela est utilisé par les tableaux, qui contiennent eux-mêmes un pointeur vers les données gérées. Cette zone de données appartient au tableau, mais n'est pas un objet suivi par le GC en soi. Le compilateur garantit que tant que ce pointeur est actif, l'objet à partir duquel ce pointeur a été chargé restera actif.

### Invariants

Le passage de placement des racines GC utilise plusieurs invariants, qui doivent être observés par le frontend et sont préservés par l'optimiseur.

Tout d'abord, seuls les types de conversion d'espace d'adresses suivants sont autorisés :

  * 0->{Suivi,Dérivé,RacineCallee}: Il est permis de réduire un pointeur non suivi à n'importe lequel des autres. Cependant, notez que l'optimiseur a une large marge de manœuvre pour ne pas ancrer une telle valeur. Il n'est jamais sûr d'avoir une valeur dans l'espace d'adresses 0 dans une partie du programme si elle est (ou dérivée d') une valeur qui nécessite une racine GC.
  * Suivi->Dérivé : C'est le chemin de désintégration standard pour les valeurs intérieures. Le passage de placement recherchera ceux-ci pour identifier le pointeur de base pour toute utilisation.
  * Tracked->CalleeRooted : L'espace d'adresse CalleeRooted sert simplement d'indice qu'une racine GC n'est pas requise. Cependant, notez que la dégradation Derived->CalleeRooted est interdite, car les pointeurs devraient généralement être stockables dans un emplacement GC, même dans cet espace d'adresse.

Maintenant, considérons ce qui constitue une utilisation :

  * Charges dont les valeurs chargées se trouvent dans l'un des espaces d'adresses
  * Stocke d'une valeur dans l'un des espaces d'adresses à un emplacement
  * Stocke à un pointeur dans l'un des espaces d'adresses
  * Appels pour lesquels une valeur dans l'un des espaces d'adresses est un opérande
  * Appels dans l'ABI jlcall, pour lesquels le tableau d'arguments contient une valeur
  * Please provide the Markdown content or text you would like me to translate into French.

Nous autorisons explicitement les chargements/stocks et les appels simples dans les espaces d'adresses Tracked/Derived. Les éléments des tableaux d'arguments jlcall doivent toujours être dans l'espace d'adresses Tracked (il est requis par l'ABI qu'ils soient des pointeurs `jl_value_t*` valides). Il en va de même pour les instructions de retour (bien que les arguments de retour de structure puissent avoir n'importe lequel des espaces d'adresses). La seule utilisation autorisée d'un pointeur CalleeRooted dans un espace d'adresses est de le passer à un appel (qui doit avoir un opérande de type approprié).

De plus, nous interdisons `getelementptr` dans l'espace d'adresses Tracked. Cela est dû au fait que, sauf si l'opération est un noop, le pointeur résultant ne pourra pas être stocké valablement dans un emplacement GC et ne pourra donc pas être dans cet espace d'adresses. Si un tel pointeur est requis, il doit d'abord être réduit à l'espace d'adresses Derived.

Enfin, nous interdisons les instructions `inttoptr`/`ptrtoint` dans ces espaces d'adresses. Avoir ces instructions signifierait que certaines valeurs `i64` sont réellement suivies par le GC. Cela pose problème, car cela enfreint l'exigence déclarée selon laquelle nous devons être en mesure d'identifier les pointeurs pertinents pour le GC. Cette invariant est réalisée en utilisant la fonctionnalité "pointeurs non intégraux" de LLVM, qui est nouvelle dans LLVM 5.0. Elle interdit à l'optimiseur de faire des optimisations qui introduiraient ces opérations. Notez que nous pouvons toujours insérer des constantes statiques au moment du JIT en utilisant `inttoptr` dans l'espace d'adresses 0, puis en se dégradant vers l'espace d'adresses approprié par la suite.

### Supporting [`ccall`](@ref)

Un aspect important manquant dans la discussion jusqu'à présent est la gestion de [`ccall`](@ref). `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566` a la caractéristique particulière que l'emplacement et la portée d'une utilisation ne coïncident pas. Comme exemple, considérons :

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

Dans la réduction, le compilateur insérera une conversion du tableau au pointeur qui supprime la référence à la valeur du tableau. Cependant, nous devons bien sûr nous assurer que le tableau reste vivant pendant que nous exécutons le [`ccall`](@ref). Pour comprendre comment cela est fait, examinons une réduction hypothétique approximative possible du code ci-dessus :

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

Le dernier `:(A)`, est une liste d'arguments supplémentaires insérée lors de la réduction qui informe le générateur de code des valeurs de niveau Julia qui doivent rester vivantes pendant la durée de ce [`ccall`](@ref). Nous prenons ensuite cette information et la représentons dans un "paquet d'opérandes" au niveau IR. Un paquet d'opérandes est essentiellement une utilisation fictive qui est attachée au site d'appel. Au niveau IR, cela ressemble à ceci :

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

Le passage de placement des racines GC traitera le paquet d'opérandes `jl_roots` comme s'il s'agissait d'un opérande ordinaire. Cependant, en tant qu'étape finale, après l'insertion des racines GC, il supprimera le paquet d'opérandes pour éviter de confondre la sélection des instructions.

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref) est spécial car il nécessite que l'utilisateur prenne le contrôle explicite du raclage de la mémoire. Selon nos invariants ci-dessus, cette fonction est illégale, car elle effectue un cast d'espace d'adresses de 10 à 0. Cependant, elle peut être utile dans certaines situations, donc nous fournissons une fonction intrinsèque spéciale :

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

qui est abaissé à l'espace d'adresse correspondant après l'abaissement de la racine GC. Notez cependant qu'en utilisant cet intrinsèque, l'appelant assume l'entière responsabilité de s'assurer que la valeur en question est enracinée. De plus, cet intrinsèque n'est pas considéré comme une utilisation, donc le passage de placement de racine GC ne fournira pas de racine GC pour la fonction. En conséquence, l'enracinement externe doit être organisé tant que la valeur est encore suivie par le système. C'est-à-dire qu'il n'est pas valide d'essayer d'utiliser le résultat de cette opération pour établir une racine globale - l'optimiseur peut déjà avoir supprimé la valeur.

### Keeping values alive in the absence of uses

Dans certains cas, il est nécessaire de garder un objet en vie, même s'il n'y a pas d'utilisation visible par le compilateur de cet objet. Cela peut être le cas pour du code de bas niveau qui opère directement sur la représentation mémoire d'un objet ou du code qui doit interagir avec du code C. Pour permettre cela, nous fournissons les intrinsics suivants au niveau LLVM :

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

(L'`llvm.` dans le nom est requis afin de pouvoir utiliser le type `token`). La sémantique de ces intrinsics est la suivante : À tout point de sauvegarde qui est dominé par un appel à `gc_preserve_begin`, mais qui n'est pas dominé par un appel correspondant à `gc_preserve_end` (c'est-à-dire un appel dont l'argument est le token retourné par un appel à `gc_preserve_begin`), les valeurs passées en arguments à ce `gc_preserve_begin` seront maintenues vivantes. Notez que le `gc_preserve_begin` compte toujours comme une utilisation régulière de ces valeurs, donc la sémantique de durée de vie standard garantira que les valeurs seront maintenues vivantes avant d'entrer dans la région de préservation.

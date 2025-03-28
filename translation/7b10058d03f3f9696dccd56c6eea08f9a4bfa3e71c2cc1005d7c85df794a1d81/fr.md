# Static analyzer annotations for GC correctness in C code

## Running the analysis

Le plugin d'analyse qui pilote l'analyse est livré avec julia. Son code source peut être trouvé dans `src/clangsa`. Pour l'exécuter, il est nécessaire de construire la dépendance clang. Définissez la variable `BUILD_LLVM_CLANG` dans votre Make.user afin de construire une version appropriée de clang. Vous pouvez également vouloir utiliser les binaires préconstruits en utilisant les options `USE_BINARYBUILDER_LLVM`.

Alternativement (ou si cela ne suffit pas), essayez

```sh
make -C src install-analysis-deps
```

depuis le répertoire de niveau supérieur de Julia.

Ensuite, exécuter l'analyse sur l'arbre source est aussi simple que d'exécuter `make -C src analyzegc`.

## General Overview

Puisque le GC de Julia est précis, il doit maintenir des informations de racine correctes pour toute valeur qui peut être référencée à tout moment où le GC peut se produire. Ces endroits sont connus sous le nom de `safepoints` et dans le contexte local de la fonction, nous étendons cette désignation à tout appel de fonction qui peut finalement se retrouver à un safepoint de manière récursive.

Dans le code généré, cela est pris en charge automatiquement par le passage de placement des racines GC (voir le chapitre sur les racines GC dans la documentation de développement de code LLVM). Cependant, dans le code C, nous devons informer le runtime de toutes les racines GC manuellement. Cela se fait en utilisant les macros suivantes :

```
// The value assigned to any slot passed as an argument to these
// is rooted for the duration of this GC frame.
JL_GC_PUSH{1,...,6}(args...)
// The values assigned into the size `n` array `rts` are rooted
// for the duration of this GC frame.
JL_GC_PUSHARGS(rts, n)
// Pop a GC frame
JL_GC_POP
```

Si ces macros ne sont pas utilisées là où elles doivent l'être, ou si elles sont utilisées incorrectement, le résultat est une corruption de mémoire silencieuse. Il est donc très important qu'elles soient placées correctement dans tout le code applicable.

En tant que tel, nous utilisons l'analyse statique (et en particulier l'analyseur statique clang) pour aider à garantir que ces macros sont utilisées correctement. Le reste de ce document donne un aperçu de cette analyse statique et décrit le support nécessaire dans la base de code julia pour faire fonctionner les choses.

## GC Invariants

Il y a deux invariants simples de correction :

  * Tous les appels `GC_PUSH` doivent être suivis d'un `GC_POP` approprié (en pratique, nous faisons respecter cela au niveau de la fonction).
  * Si une valeur n'était auparavant pas ancrée à un point de sauvegarde, elle peut ne plus être référencée par la suite.

Bien sûr, le diable est dans les détails ici. En particulier, pour satisfaire la deuxième des conditions ci-dessus, nous devons savoir :

  * Quelles appels sont des points de sécurité et lesquels ne le sont pas
  * Quelles valeurs sont enracinées à un point de sécurité donné et lesquelles ne le sont pas
  * Quand une valeur est-elle référencée

Pour le deuxième point en particulier, nous devons savoir quelles emplacements mémoire seront considérés comme enracinés à l'exécution (c'est-à-dire que les valeurs assignées à ces emplacements sont enracinées). Cela inclut les emplacements explicitement désignés comme tels en les passant à l'un des macros `GC_PUSH`, les emplacements et valeurs enracinés globalement, ainsi que tout emplacement accessible de manière récursive à partir de l'un de ces emplacements.

## Static Analysis Algorithm

L'idée elle-même est très simple, bien que l'implémentation soit beaucoup plus compliquée (principalement en raison d'un grand nombre de cas particuliers et des subtilités de C et C++). En essence, nous suivons tous les emplacements qui sont enracinés, toutes les valeurs qui peuvent être enracinées et toute expression (assignations, allocations, etc.) qui affecte l'enracinement de toute valeur enracinable. Ensuite, à tout point de sauvegarde, nous effectuons un "GC symbolique" et empoisonnons toutes les valeurs qui ne sont pas enracinées à cet emplacement. Si ces valeurs sont ensuite référencées, nous émettons une erreur.

L'analyseur statique clang fonctionne en construisant un graphe d'états et en explorant ce graphe à la recherche de sources d'erreurs. Plusieurs nœuds de ce graphe sont générés par l'analyseur lui-même (par exemple pour le flux de contrôle), mais les définitions ci-dessus augmentent ce graphe avec notre propre état.

L'analyseur statique est interprocédural et peut analyser le flux de contrôle à travers les frontières des fonctions. Cependant, l'analyseur statique n'est pas entièrement récursif et prend des décisions heuristiques sur les appels à explorer (de plus, certains appels sont inter-unités de traduction et invisibles pour l'analyseur). Dans notre cas, notre définition de la correction nécessite des informations totales. En tant que tel, nous devons annoter les prototypes de tous les appels de fonction avec les informations requises par l'analyse, même si ces informations seraient autrement disponibles par l'analyse statique interprocédurale.

Heureusement, nous pouvons toujours utiliser cette analyse interprocédurale pour nous assurer que les annotations que nous plaçons sur une fonction donnée sont en effet correctes compte tenu de l'implémentation de ladite fonction.

## The analyzer annotations

Ces annotations se trouvent dans src/support/analyzer_annotations.h. Elles ne sont actives que lorsque l'analyseur est utilisé et s'étendent soit à rien (pour les annotations de prototype), soit à des no-ops (pour les annotations de type fonction).

### `JL_NOTSAFEPOINT`

Ceci est peut-être l'annotation la plus courante, et elle doit être placée sur toute fonction qui est connue pour ne pas pouvoir mener à un point de sécurité GC. En général, il est seulement sûr pour une telle fonction d'effectuer des opérations arithmétiques, des accès mémoire et des appels à des fonctions soit annotées `JL_NOTSAFEPOINT`, soit autrement connues pour ne pas être des points de sécurité (par exemple, des fonctions de la bibliothèque standard C, qui sont codées en dur comme telles dans l'analyseur).

Il est valide de conserver des valeurs non enracinées lors des appels à toute fonction annotée avec cet attribut :

Exemple d'utilisation :

```c
void jl_get_one() JL_NOTSAFEPOINT {
  return 1;
}

jl_value_t *example() {
  jl_value_t *val = jl_alloc_whatever();
  // This is valid, even though `val` is unrooted, because
  // jl_get_one is not a safepoint
  jl_get_one();
  return val;
}
```

### `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`

Lorsque `JL_MAYBE_UNROOTED` est annoté comme un argument d'une fonction, cela indique que cet argument peut être passé, même s'il n'est pas enraciné. Dans le cours normal des événements, l'ABI de Julia garantit que les appelants enracinent les valeurs avant de les passer aux appelés. Cependant, certaines fonctions ne suivent pas cette ABI et permettent que des valeurs leur soient passées même si elles ne sont pas enracinées. Notez cependant que cela n'implique pas automatiquement que cet argument sera préservé. L'annotation `ROOTS_TEMPORARILY` fournit la garantie plus forte que, non seulement la valeur peut être non enracinée lorsqu'elle est passée, mais qu'elle sera également préservée à travers tous les points de sauvegarde internes par l'appelé.

Notez que `JL_NOTSAFEPOINT` implique essentiellement `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`, car la racine d'un argument est sans importance si la fonction ne contient pas de points de sauvegarde.

Un point supplémentaire à noter est que ces annotations s'appliquent à la fois du côté de l'appelant et du côté du appelé. Du côté de l'appelant, elles lèvent les restrictions de racine qui sont normalement requises pour les fonctions ABI de julia. Du côté du appelé, elles ont l'effet inverse d'empêcher ces arguments d'être considérés comme implicitement enracinés.

Si l'une de ces annotations est appliquée à la fonction dans son ensemble, elle s'applique à tous les arguments de la fonction. Cela ne devrait généralement être nécessaire que pour les fonctions varargs.

Exemple d'utilisation :

```c
JL_DLLEXPORT void JL_NORETURN jl_throw(jl_value_t *e JL_MAYBE_UNROOTED);
jl_value_t *jl_alloc_error();

void example() {
  // The return value of the allocation is unrooted. This would normally
  // be an error, but is allowed because of the above annotation.
  jl_throw(jl_alloc_error());
}
```

### `JL_PROPAGATES_ROOT`

Cette annotation se trouve couramment sur les fonctions d'accès qui retournent un objet rootable stocké dans un autre. Lorsqu'elle est annotée sur un argument de fonction, elle indique à l'analyseur que la racine pour cet argument s'applique également à la valeur retournée par la fonction.

Exemple d'utilisation :

```c
jl_value_t *jl_svecref(jl_svec_t *t JL_PROPAGATES_ROOT, size_t i) JL_NOTSAFEPOINT;

size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_svecref(svec, 1)
  // This is valid, because, as annotated by the PROPAGATES_ROOT annotation,
  // jl_svecref propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_ROOTING_ARGUMENT`/`JL_ROOTED_ARGUMENT`

Ceci est essentiellement le pendant de l'assignation à `JL_PROPAGATES_ROOT`. Lorsqu'une valeur est assignée à un champ d'une autre valeur qui est déjà enracinée, la valeur assignée héritera de la racine de la valeur dans laquelle elle est assignée.

Exemple d'utilisation :

```c
void jl_svecset(void *t JL_ROOTING_ARGUMENT, size_t i, void *x JL_ROOTED_ARGUMENT) JL_NOTSAFEPOINT


size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_box_long(10000);
  jl_svecset(svec, val);
  // This is valid, because the annotations imply that the
  // jl_svecset propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_GC_DISABLED`

Cette annotation implique que cette fonction n'est appelée qu'avec le runtime GC désactivé. Les fonctions de ce type sont le plus souvent rencontrées lors du démarrage et dans le code GC lui-même. Notez que cette annotation est vérifiée par rapport aux appels d'activation/désactivation du runtime, donc clang saura si vous mentez. Ce n'est pas une bonne façon de désactiver le traitement d'une fonction donnée si le GC n'est pas réellement désactivé (utilisez `ifdef __clang_analyzer__` pour cela si vous devez).

Exemple d'utilisation :

```c
void jl_do_magic() JL_GC_DISABLED {
  // Wildly allocate here with no regard for roots
}

void example() {
  int en = jl_gc_enable(0);
  jl_do_magic();
  jl_gc_enable(en);
}
```

### `JL_REQUIRE_ROOTED_SLOT`

Cette annotation exige que l'appelant passe un slot qui est enraciné (c'est-à-dire que les valeurs assignées à ce slot seront enracinées).

Exemple d'utilisation :

```c
void jl_do_processing(jl_value_t **slot JL_REQUIRE_ROOTED_SLOT) {
  *slot = jl_box_long(1);
  // Ok, only, because the slot was annotated as rooting
  jl_gc_safepoint();
}

void example() {
  jl_value_t *slot = NULL;
  JL_GC_PUSH1(&slot);
  jl_do_processing(&slot);
  JL_GC_POP();
}
```

### `JL_GLOBALLY_ROOTED`

Cette annotation implique qu'une valeur donnée est toujours enracinée globalement. Elle peut être appliquée aux déclarations de variables globales, auquel cas elle s'appliquera à la valeur de ces variables (ou aux valeurs si la déclaration concerne un tableau), ou aux fonctions, auquel cas elle s'appliquera à la valeur de retour de ces fonctions (par exemple, pour des fonctions qui retournent toujours une valeur privée, enracinée globalement).

Exemple d'utilisation :

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

Cette annotation est essentiellement équivalente à `JL_GLOBALLY_ROOTED`, sauf qu'elle ne doit être utilisée que si ces valeurs sont globalement ancrées en raison d'être un type feuille. L'ancrage des types feuilles est un peu compliqué. Ils sont généralement ancrés par le champ `cache` du `TypeName` correspondant, qui lui-même est ancré par le module contenant (donc ils sont ancrés tant que le module contenant est valide) et nous pouvons généralement supposer que les types feuilles sont ancrés là où ils sont utilisés, mais nous pourrions affiner cette propriété à l'avenir, donc l'annotation séparée aide à clarifier la raison pour laquelle ils sont globalement ancrés.

L'analyseur détecte également automatiquement les vérifications de la nature de feuille et ne se plaindra pas de l'absence de racines GC sur ces chemins.

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

Ceci est une annotation de type fonction. Toute valeur passée à cette annotation sera considérée comme enracinée pour la portée de la fonction actuelle. Elle est conçue comme une échappatoire pour l'insuffisance de l'analyseur ou des situations compliquées. Cependant, elle doit être utilisée avec parcimonie, au profit de l'amélioration de l'analyseur lui-même.

```
void example() {
  jl_value_t *val = jl_alloc_something();
  if (some_condition) {
    // We happen to know for complicated external reasons
    // that val is rooted under these conditions
    JL_GC_PROMISE_ROOTED(val);
  }
}
```

## Completeness of analysis

L'analyseur ne considère que les informations locales. En particulier, par exemple dans le cas `PROPAGATES_ROOT` ci-dessus, il suppose que cette mémoire n'est modifiée que de manière visible, et non dans des fonctions appelées (à moins qu'il ne décide de les prendre en compte dans son analyse) et non dans des threads s'exécutant simultanément. En tant que tel, il peut manquer quelques cas problématiques, bien qu'en pratique, une telle modification concurrente soit assez rare. Améliorer l'analyseur pour gérer davantage de tels cas pourrait être un sujet intéressant pour de futurs travaux.

# Embedding Julia

Comme nous l'avons vu dans [Calling C and Fortran Code](@ref), Julia a un moyen simple et efficace d'appeler des fonctions écrites en C. Mais il existe des situations où l'inverse est nécessaire : appeler des fonctions Julia depuis du code C. Cela peut être utilisé pour intégrer du code Julia dans un projet C/C++ plus vaste, sans avoir besoin de tout réécrire en C/C++. Julia dispose d'une API C pour rendre cela possible. Comme presque tous les langages de programmation ont un moyen d'appeler des fonctions C, l'API C de Julia peut également être utilisée pour construire d'autres ponts linguistiques (par exemple, appeler Julia depuis Python, Rust ou C#). Bien que Rust et C++ puissent utiliser directement l'API d'intégration C, les deux disposent de packages facilitant cela, pour C++ [Jluna](https://github.com/Clemapfel/jluna) est utile.

## High-Level Embedding

**Remarque** : Cette section couvre l'intégration de code Julia dans C sur des systèmes d'exploitation de type Unix. Pour le faire sur Windows, veuillez consulter la section suivante, [High-Level Embedding on Windows with Visual Studio](@ref).

Nous commençons par un programme C simple qui initialise Julia et appelle du code Julia :

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Pour construire ce programme, vous devez ajouter le chemin vers l'en-tête Julia au chemin d'inclusion et lier contre `libjulia`. Par exemple, lorsque Julia est installé dans `$JULIA_DIR`, on peut compiler le programme de test ci-dessus `test.c` avec `gcc` en utilisant :

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

Alternativement, regardez le programme `embedding.c` dans l'arborescence source de Julia dans le dossier `test/embedding/`. Le fichier `cli/loader_exe.c` est un autre exemple simple de la façon de définir les options `jl_options` lors de la liaison avec `libjulia`.

La première chose à faire avant d'appeler toute autre fonction C de Julia est d'initialiser Julia. Cela se fait en appelant `jl_init`, qui essaie de déterminer automatiquement l'emplacement d'installation de Julia. Si vous devez spécifier un emplacement personnalisé ou indiquer quelle image système charger, utilisez `jl_init_with_image` à la place.

La deuxième instruction dans le programme de test évalue une instruction Julia en utilisant un appel à `jl_eval_string`.

Avant la terminaison du programme, il est fortement recommandé d'appeler `jl_atexit_hook`. Le programme d'exemple ci-dessus l'appelle juste avant de retourner de `main`.

!!! note
    Actuellement, le lien dynamique avec la bibliothèque partagée `libjulia` nécessite de passer l'option `RTLD_GLOBAL`. En Python, cela ressemble à :

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    Si le programme Julia doit accéder à des symboles de l'exécutable principal, il peut être nécessaire d'ajouter le drapeau de l'éditeur de liens `-Wl,--export-dynamic` au moment de la compilation sur Linux, en plus de ceux générés par `julia-config.jl` décrits ci-dessous. Cela n'est pas nécessaire lors de la compilation d'une bibliothèque partagée.


### Using julia-config to automatically determine build parameters

Le script `julia-config.jl` a été créé pour aider à déterminer quels paramètres de construction sont requis par un programme qui utilise Julia embarqué. Ce script utilise les paramètres de construction et la configuration système de la distribution Julia particulière par laquelle il est invoqué pour exporter les drapeaux de compilation nécessaires à un programme d'intégration pour interagir avec cette distribution. Ce script se trouve dans le répertoire de données partagées de Julia.

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

Une utilisation simple de ce script se fait depuis la ligne de commande. En supposant que `julia-config.jl` se trouve dans `/usr/local/julia/share/julia`, il peut être invoqué directement depuis la ligne de commande et accepte n'importe quelle combinaison de trois options :

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

Si l'exemple de code ci-dessus est enregistré dans le fichier `embed_example.c`, alors la commande suivante le compilera en un programme exécutable sur Linux et Windows (environnement MSYS2). Sur macOS, remplacez `gcc` par `clang`.

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

En général, les projets d'intégration seront plus compliqués que l'exemple ci-dessus, et ce qui suit permet également un support général des makefiles – en supposant GNU make en raison de l'utilisation des expansions de macro **shell**. De plus, bien que `julia-config.jl` se trouve généralement dans le répertoire `/usr/local`, s'il n'y est pas, alors Julia elle-même peut être utilisée pour trouver `julia-config.jl`, et le makefile peut tirer parti de cela. L'exemple ci-dessus est étendu pour utiliser un makefile :

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

Maintenant, la commande de construction est simplement `make`.

## High-Level Embedding on Windows with Visual Studio

Si la variable d'environnement `JULIA_DIR` n'a pas été configurée, ajoutez-la en utilisant le panneau Système avant de démarrer Visual Studio. Le dossier `bin` sous JULIA_DIR doit être dans le PATH système.

Nous commençons par ouvrir Visual Studio et créer un nouveau projet d'application Console. Ouvrez le fichier d'en-tête 'stdafx.h' et ajoutez les lignes suivantes à la fin :

```c
#include <julia.h>
```

Ensuite, remplacez la fonction main() dans le projet par ce code :

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

L'étape suivante consiste à configurer le projet pour trouver les fichiers d'inclusion Julia et les bibliothèques. Il est important de savoir si l'installation de Julia est en 32 ou 64 bits. Supprimez toute configuration de plateforme qui ne correspond pas à l'installation de Julia avant de continuer.

En utilisant la boîte de dialogue des propriétés du projet, allez dans `C/C++` | `Général` et ajoutez `$(JULIA_DIR)\include\julia\` à la propriété Répertoires d'inclusion supplémentaires. Ensuite, allez dans la section `Linker` | `Général` et ajoutez `$(JULIA_DIR)\lib` à la propriété Répertoires de bibliothèques supplémentaires. Enfin, sous `Linker` | `Input`, ajoutez `libjulia.dll.a;libopenlibm.dll.a;` à la liste des bibliothèques.

À ce stade, le projet devrait se construire et s'exécuter.

## Converting Types

Les applications réelles devront non seulement exécuter des expressions, mais aussi renvoyer leurs valeurs au programme hôte. `jl_eval_string` renvoie un `jl_value_t*`, qui est un pointeur vers un objet Julia alloué sur le tas. Stocker des types de données simples comme [`Float64`](@ref) de cette manière s'appelle `boxing`, et extraire les données primitives stockées s'appelle `unboxing`. Notre programme d'exemple amélioré qui calcule la racine carrée de 2 en Julia et lit le résultat en C contient maintenant ce code :

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

Pour vérifier si `ret` est d'un type Julia spécifique, nous pouvons utiliser les fonctions `jl_isa`, `jl_typeis` ou `jl_is_...`. En tapant `typeof(sqrt(2.0))` dans le shell Julia, nous pouvons voir que le type de retour est [`Float64`](@ref) (`double` en C). Pour convertir la valeur Julia encapsulée en un double C, la fonction `jl_unbox_float64` est utilisée dans l'extrait de code ci-dessus.

Les fonctions `jl_box_...` correspondantes sont utilisées pour convertir dans l'autre sens :

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

Comme nous le verrons ensuite, le boxing est nécessaire pour appeler des fonctions Julia avec des arguments spécifiques.

## Calling Julia Functions

Bien que `jl_eval_string` permette à C d'obtenir le résultat d'une expression Julia, il ne permet pas de passer des arguments calculés en C à Julia. Pour cela, vous devrez invoquer directement des fonctions Julia, en utilisant `jl_call` :

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

Dans la première étape, un handle à la fonction Julia `sqrt` est récupéré en appelant `jl_get_function`. Le premier argument passé à `jl_get_function` est un pointeur vers le module `Base` dans lequel `sqrt` est défini. Ensuite, la valeur double est encapsulée en utilisant `jl_box_float64`. Enfin, dans la dernière étape, la fonction est appelée en utilisant `jl_call1`. Les fonctions `jl_call0`, `jl_call2` et `jl_call3` existent également, pour gérer de manière pratique différents nombres d'arguments. Pour passer plus d'arguments, utilisez `jl_call` :

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

Son deuxième argument `args` est un tableau d'arguments `jl_value_t*` et `nargs` est le nombre d'arguments.

Il existe également une alternative, peut-être plus simple, pour appeler des fonctions Julia, et c'est via [`@cfunction`](@ref). L'utilisation de `@cfunction` vous permet d'effectuer les conversions de type du côté de Julia, ce qui est généralement plus facile que de le faire du côté de C. L'exemple `sqrt` ci-dessus serait écrit avec `@cfunction` comme suit :

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

où nous définissons d'abord une fonction appelable en C dans Julia, extrayons le pointeur de fonction à partir de celle-ci, et enfin l'appelons. En plus de simplifier les conversions de types en les effectuant dans le langage de haut niveau, appeler des fonctions Julia via des pointeurs `@cfunction` élimine le surcoût de dispatch dynamique requis par `jl_call` (pour lequel tous les arguments sont "emballés"), et devrait avoir des performances équivalentes à celles des pointeurs de fonction C natifs.

## Memory Management

Comme nous l'avons vu, les objets Julia sont représentés en C comme des pointeurs de type `jl_value_t*`. Cela soulève la question de qui est responsable de la libération de ces objets.

Typiquement, les objets Julia sont libérés par le ramasse-miettes (GC), mais le GC ne sait pas automatiquement que nous détenons une référence à une valeur Julia depuis C. Cela signifie que le GC peut libérer des objets sous vous, rendant les pointeurs invalides.

Le GC ne s'exécutera que lorsque de nouveaux objets Julia sont en cours d'allocation. Des appels comme `jl_box_float64` effectuent une allocation, mais l'allocation peut également se produire à tout moment lors de l'exécution du code Julia.

Lors de l'écriture de code qui intègre Julia, il est généralement sûr d'utiliser des valeurs `jl_value_t*` entre les appels `jl_...` (car le GC ne sera déclenché que par ces appels). Mais pour s'assurer que les valeurs peuvent survivre aux appels `jl_...`, nous devons indiquer à Julia que nous maintenons toujours une référence aux valeurs Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf), un processus appelé "GC rooting". Rooter une valeur garantira que le ramasse-miettes n'identifie pas accidentellement cette valeur comme inutilisée et ne libère pas la mémoire qui soutient cette valeur. Cela peut être fait en utilisant les macros `JL_GC_PUSH` :

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

L'appel `JL_GC_POP` libère les références établies par le précédent `JL_GC_PUSH`. Notez que `JL_GC_PUSH` stocke des références sur la pile C, il doit donc être exactement associé à un `JL_GC_POP` avant que la portée ne soit quittée. C'est-à-dire, avant que la fonction ne retourne, ou que le flux de contrôle quitte autrement le bloc dans lequel le `JL_GC_PUSH` a été invoqué.

Plusieurs valeurs Julia peuvent être ajoutées en une seule fois en utilisant les macros `JL_GC_PUSH2` à `JL_GC_PUSH6` :

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

Pour pousser un tableau de valeurs Julia, on peut utiliser la macro `JL_GC_PUSHARGS`, qui peut être utilisée comme suit :

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

Chaque portée doit avoir un seul appel à `JL_GC_PUSH*`, et doit être associé à un seul appel `JL_GC_POP`. Si toutes les variables nécessaires que vous souhaitez ancrer ne peuvent pas être poussées par un seul appel à `JL_GC_PUSH*`, ou s'il y a plus de 6 variables à pousser et que l'utilisation d'un tableau d'arguments n'est pas une option, alors on peut utiliser des blocs internes :

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

Notez qu'il n'est pas nécessaire d'avoir des valeurs `jl_value_t*` valides avant d'appeler `JL_GC_PUSH*`. Il est acceptable d'en avoir un certain nombre initialisés à `NULL`, de les passer à `JL_GC_PUSH*` puis de créer les valeurs Julia réelles. Par exemple :

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

Si vous devez conserver le pointeur vers une variable entre des fonctions (ou des portées de blocs), il n'est pas possible d'utiliser `JL_GC_PUSH*`. Dans ce cas, il est nécessaire de créer et de conserver une référence à la variable dans le scope global de Julia. Une façon simple d'y parvenir est d'utiliser un `IdDict` global qui contiendra les références, évitant ainsi la désallocation par le GC. Cependant, cette méthode ne fonctionnera correctement qu'avec des types mutables.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

Si la variable est immuable, elle doit être enveloppée dans un conteneur mutable équivalent ou, de préférence, dans un `RefValue{Any}` avant d'être ajoutée à `IdDict`. Dans cette approche, le conteneur doit être créé ou rempli via du code C en utilisant, par exemple, la fonction `jl_new_struct`. Si le conteneur est créé par `jl_call*`, vous devrez recharger le pointeur à utiliser dans le code C.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

Le GC peut être autorisé à désallouer une variable en supprimant la référence à celle-ci de `refs` en utilisant la fonction `delete!`, à condition qu'aucune autre référence à la variable ne soit conservée ailleurs :

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

En tant qu'alternative pour des cas très simples, il est possible de créer simplement un conteneur global de type `Vector{Any}` et de récupérer les éléments de celui-ci lorsque nécessaire, ou même de créer une variable globale par pointeur en utilisant

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

Le ramasse-miettes fonctionne également sous l'hypothèse qu'il est conscient de chaque objet de génération supérieure pointant vers un objet de génération inférieure. Chaque fois qu'un pointeur est mis à jour, rompant cette hypothèse, il doit être signalé au collecteur avec la fonction `jl_gc_wb` (barrière d'écriture) comme suit :

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

Il est en général impossible de prédire quelles valeurs seront anciennes à l'exécution, donc la barrière d'écriture doit être insérée après tous les stockages explicites. Une exception notable est si l'objet `parent` vient d'être alloué et qu'aucune collecte de déchets n'a eu lieu depuis. Notez que la plupart des fonctions `jl_...` peuvent parfois invoquer la collecte de déchets.

La barrière d'écriture est également nécessaire pour les tableaux de pointeurs lors de la mise à jour de leurs données directement. Appeler `jl_array_ptr_set` est généralement beaucoup préférable. Mais des mises à jour directes peuvent être effectuées. Par exemple :

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

Il existe certaines fonctions pour contrôler le GC. Dans des cas d'utilisation normaux, celles-ci ne devraient pas être nécessaires.

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

Julia et C peuvent partager des données de tableau sans les copier. L'exemple suivant montrera comment cela fonctionne.

Les tableaux Julia sont représentés en C par le type de données `jl_array_t*`. Fondamentalement, `jl_array_t` est une structure qui contient :

  * Informations sur le type de données
  * Un pointeur vers le bloc de données
  * Informations sur les tailles du tableau

Pour garder les choses simples, nous commençons par un tableau 1D. La création d'un tableau contenant des éléments Float64 de longueur 10 peut se faire comme ceci :

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

Alternativement, si vous avez déjà alloué le tableau, vous pouvez générer un mince wrapper autour de ses données :

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

Le dernier argument est un booléen indiquant si Julia doit prendre possession des données. Si cet argument est non nul, le GC appellera `free` sur le pointeur de données lorsque le tableau ne sera plus référencé.

Pour accéder aux données de `x`, nous pouvons utiliser `jl_array_data` :

```c
double *xData = jl_array_data(x, double);
```

Maintenant, nous pouvons remplir le tableau :

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

Maintenant, appelons une fonction Julia qui effectue une opération en place sur `x` :

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

En imprimant le tableau, on peut vérifier que les éléments de `x` sont maintenant inversés.

### Accessing Returned Arrays

Si une fonction Julia renvoie un tableau, la valeur de retour de `jl_eval_string` et `jl_call` peut être convertie en un `jl_array_t*` :

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

Maintenant, le contenu de `y` peut être accédé comme auparavant en utilisant `jl_array_data`. Comme toujours, assurez-vous de garder une référence au tableau tant qu'il est utilisé.

### Multidimensional Arrays

Les tableaux multidimensionnels de Julia sont stockés en mémoire dans l'ordre de colonne. Voici un code qui crée un tableau 2D et accède à ses propriétés :

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

Remarquez que, bien que les tableaux Julia utilisent un indexage basé sur 1, l'API C utilise un indexage basé sur 0 (par exemple, lors de l'appel de `jl_array_dim`) afin de se lire comme du code C idiomatique.

## Exceptions

Le code Julia peut lancer des exceptions. Par exemple, considérez :

```c
jl_eval_string("this_function_does_not_exist()");
```

Cet appel semblera ne rien faire. Cependant, il est possible de vérifier si une exception a été levée :

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

Si vous utilisez l'API C de Julia depuis un langage qui prend en charge les exceptions (par exemple, Python, C#, C++), il est logique d'encapsuler chaque appel à `libjulia` dans une fonction qui vérifie si une exception a été levée, puis relance l'exception dans le langage hôte.

### Throwing Julia Exceptions

Lors de l'écriture de fonctions appelables en Julia, il peut être nécessaire de valider les arguments et de lancer des exceptions pour indiquer des erreurs. Un contrôle de type typique ressemble à :

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

Les exceptions générales peuvent être levées en utilisant les fonctions :

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error` prend une chaîne C, et `jl_errorf` est appelé comme `printf` :

```c
jl_errorf("argument x = %d is too large", x);
```

où dans cet exemple `x` est supposé être un entier.

### Thread-safety

En général, l'API C de Julia n'est pas entièrement sécurisée pour les threads. Lors de l'intégration de Julia dans une application multi-threadée, il est nécessaire de veiller à ne pas enfreindre les restrictions suivantes :

  * `jl_init()` ne peut être appelé qu'une seule fois dans la durée de vie de l'application. Il en va de même pour `jl_atexit_hook()`, qui ne peut être appelé qu'après `jl_init()`.
  * Les fonctions API `jl_...()` ne peuvent être appelées que depuis le thread dans lequel `jl_init()` a été appelé, *ou depuis des threads démarrés par le runtime Julia*. Appeler des fonctions API Julia depuis des threads démarrés par l'utilisateur n'est pas pris en charge et peut entraîner un comportement indéfini et des plantages.

La deuxième condition ci-dessus implique que vous ne pouvez pas appeler en toute sécurité les fonctions `jl_...()` à partir de threads qui n'ont pas été démarrés par Julia (le thread appelant `jl_init()` étant l'exception). Par exemple, ce qui suit n'est pas pris en charge et provoquera très probablement un segfault :

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

Au lieu de cela, effectuer tous les appels Julia à partir du même thread créé par l'utilisateur fonctionnera :

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

Un exemple d'appel de l'API C de Julia depuis un thread démarré par Julia lui-même :

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

Si nous exécutons ce code avec 2 threads Julia, nous obtenons la sortie suivante (remarque : la sortie variera selon l'exécution et le système) :

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

Comme on peut le voir, le thread Julia 1 correspond à l'ID pthread 3bfd9c00, et le thread Julia 2 correspond à l'ID 23938640, montrant qu'en effet plusieurs threads sont utilisés au niveau C, et que nous pouvons appeler en toute sécurité les routines de l'API C de Julia depuis ces threads.

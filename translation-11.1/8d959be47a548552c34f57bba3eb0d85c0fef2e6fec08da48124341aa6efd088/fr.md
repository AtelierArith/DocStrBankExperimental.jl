# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

Dans `gdb`, tout objet `jl_value_t*` `obj` peut être affiché en utilisant

```
(gdb) call jl_(obj)
```

L'objet sera affiché dans la session `julia`, et non dans la session gdb. C'est un moyen utile de découvrir les types et les valeurs des objets manipulés par le code C de Julia.

De même, si vous déboguez certaines des internals de Julia (par exemple, `compiler.jl`), vous pouvez imprimer `obj` en utilisant

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

C'est une bonne façon de contourner les problèmes qui surviennent en raison de l'ordre dans lequel les flux de sortie de Julia sont initialisés.

L'interpréteur flisp de Julia utilise des objets `value_t` ; ceux-ci peuvent être affichés avec `call fl_print(fl_ctx, ios_stdout, obj)`.

## Useful Julia variables for Inspecting

Bien que les adresses de nombreuses variables, comme les singletons, puissent être utiles à imprimer pour de nombreux échecs, il existe un certain nombre de variables supplémentaires (voir `julia.h` pour une liste complète) qui sont encore plus utiles.

  * (lors de `jl_apply_generic`) `mfunc` et `jl_uncompress_ast(mfunc->def, mfunc->code)` :: pour comprendre un peu la pile d'appels
  * `jl_lineno` et `jl_filename` :: pour déterminer à partir de quelle ligne dans un test commencer à déboguer (ou pour savoir jusqu'où un fichier a été analysé)
  * `$1` :: pas vraiment une variable, mais toujours un raccourci utile pour se référer au résultat de la dernière commande gdb (comme `print`)
  * `jl_options` :: parfois utile, car il répertorie toutes les options de ligne de commande qui ont été correctement analysées.
  * `jl_uv_stderr` :: parce que qui n'aime pas pouvoir interagir avec stdio

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: Semblable à `thread apply all bt` de gdb ou `thread backtrace all` de lldb. Exécute tous les threads tout en imprimant les traces de retour pour toutes les tâches existantes.
  * `jl_gdblookup($pc)` :: Pour rechercher la fonction et la ligne actuelles.
  * `jl_gdblookupinfo($pc)` :: Pour rechercher l'objet d'instance de méthode actuel.
  * `jl_gdbdumpcode(mi)` :: Pour dumper tout le `code_typed/code_llvm/code_asm` lorsque le REPL ne fonctionne pas correctement.
  * `jlbacktrace()` :: Pour afficher la pile de backtrace actuelle de Julia sur stderr. Utilisable uniquement après que `record_backtrace()` a été appelé.
  * `jl_dump_llvm_value(Value*)` :: Pour invoquer `Value->dump()` dans gdb, où cela ne fonctionne pas nativement. Par exemple, `f->linfo->functionObject`, `f->linfo->specFunctionObject`, et `to_function(f->linfo)`.
  * `jl_dump_llvm_module(Module*)` :: Pour invoquer `Module->dump()` dans gdb, où cela ne fonctionne pas nativement.
  * `Type->dump()` :: ne fonctionne que dans lldb. Remarque : ajoutez quelque chose comme `;1` pour empêcher lldb d'imprimer son invite sur la sortie.
  * `jl_eval_string("expr")` :: pour invoquer des effets secondaires afin de modifier l'état actuel ou de rechercher des symboles
  * `jl_typeof(jl_value_t*)` :: pour extraire le tag de type d'une valeur Julia (dans gdb, appelez `macro define jl_typeof jl_typeof` d'abord, ou choisissez quelque chose de court comme `ty` pour le premier argument afin de définir un raccourci)

## Inserting breakpoints for inspection from gdb

Dans votre session `gdb`, définissez un point d'arrêt dans `jl_breakpoint` comme suit :

```
(gdb) break jl_breakpoint
```

Ensuite, dans votre code Julia, insérez un appel à `jl_breakpoint` en ajoutant

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

où `obj` peut être n'importe quelle variable ou tuple que vous souhaitez rendre accessible dans le point d'arrêt.

Il est particulièrement utile de revenir au cadre `jl_apply`, à partir duquel vous pouvez afficher les arguments d'une fonction en utilisant, par exemple,

```
(gdb) call jl_(args[0])
```

Un autre cadre utile est `to_function(jl_method_instance_t *li, bool cstyle)`. L'argument `jl_method_instance_t*` est une structure avec une référence à l'AST final envoyé au compilateur. Cependant, l'AST à ce stade sera généralement compressé ; pour voir l'AST, appelez `jl_uncompress_ast` puis passez le résultat à `jl_` :

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

Disons que le fichier est `sysimg.jl` :

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

Puisque cette fonction est utilisée pour chaque appel, vous rendrez tout 1000 fois plus lent si vous faites cela.

## Dealing with signals

Julia nécessite quelques signaux pour fonctionner correctement. Le profileur utilise `SIGUSR2` pour l'échantillonnage et le ramasse-miettes utilise `SIGSEGV` pour la synchronisation des threads. Si vous déboguez du code qui utilise le profileur ou plusieurs threads, vous voudrez peut-être laisser le débogueur ignorer ces signaux car ils peuvent être déclenchés très souvent pendant les opérations normales. La commande pour faire cela dans GDB est (remplacez `SIGSEGV` par `SIGUSR2` ou d'autres signaux que vous souhaitez ignorer) :

```
(gdb) handle SIGSEGV noprint nostop pass
```

La commande LLDB correspondante est (après le démarrage du processus) :

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

Si vous déboguez un segfault avec du code multithread, vous pouvez définir un point d'arrêt sur `jl_critical_error` (`sigdie_handler` devrait également fonctionner sur Linux et BSD) afin de ne capturer que le segfault réel plutôt que les points de synchronisation du GC.

## Debugging during Julia's build process (bootstrap)

Les erreurs qui se produisent pendant `make` nécessitent un traitement spécial. Julia est construite en deux étapes, en construisant `sys0` et `sys.ji`. Pour voir quelles commandes s'exécutent au moment de l'échec, utilisez `make VERBOSE=1`.

Au moment de la rédaction de ce document, vous pouvez déboguer les erreurs de construction pendant la phase `sys0` depuis le répertoire `base` en utilisant :

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

Vous devrez peut-être supprimer tous les fichiers dans `usr/lib/julia/` pour que cela fonctionne.

Vous pouvez déboguer la phase `sys.ji` en utilisant :

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

Par défaut, toute erreur fera quitter Julia, même sous gdb. Pour attraper une erreur "sur le fait", définissez un point d'arrêt dans `jl_error` (il existe plusieurs autres emplacements utiles, pour des types d'échecs spécifiques, y compris : `jl_too_few_args`, `jl_too_many_args` et `jl_throw`).

Une fois qu'une erreur est détectée, une technique utile consiste à remonter la pile et à examiner la fonction en inspectant l'appel associé à `jl_apply`. Pour prendre un exemple du monde réel :

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

Le `jl_apply` le plus récent est à la trame #3, donc nous pouvons y revenir et examiner l'AST pour la fonction `julia_convert_16886`. C'est le nom unique pour une méthode de `convert`. `f` dans cette trame est un `jl_function_t*`, donc nous pouvons examiner la signature de type, le cas échéant, à partir du champ `specTypes` :

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

Alors, nous pouvons examiner l'AST pour cette fonction :

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

Enfin, et peut-être de manière la plus utile, nous pouvons forcer la fonction à être recompilée afin de passer en revue le processus de génération de code. Pour ce faire, effacez le `functionObject` mis en cache de `jl_lamdbda_info_t*` :

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

Ensuite, définissez un point d'arrêt à un endroit utile (par exemple, `emit_function`, `emit_expr`, `emit_call`, etc.), et exécutez la génération de code :

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

La précompilation des modules génère un processus Julia séparé pour précompiler chaque module. Définir un point d'arrêt ou capturer des échecs dans un travail de précompilation nécessite de connecter un débogueur au travailleur. L'approche la plus simple consiste à configurer le débogueur pour surveiller les nouveaux lancements de processus correspondant à un nom donné. Par exemple :

```
(gdb) attach -w -n julia-debug
```

ou :

```
(lldb) process attach -w -n julia-debug
```

Ensuite, exécutez un script/commande pour démarrer la précompilation. Comme décrit précédemment, utilisez des points d'arrêt conditionnels dans le processus parent pour capturer des événements de chargement de fichiers spécifiques et réduire la fenêtre de débogage. (certains systèmes d'exploitation peuvent nécessiter des approches alternatives, comme suivre chaque `fork` à partir du processus parent)

## Mozilla's Record and Replay Framework (rr)

Julia fonctionne désormais directement avec [rr](https://rr-project.org/), le cadre d'enregistrement léger et de débogage déterministe de Mozilla. Cela vous permet de rejouer le tracé d'une exécution de manière déterministe. Les espaces d'adresses, le contenu des registres, les données des appels système, etc., de l'exécution rejouée sont exactement les mêmes à chaque exécution.

Une version récente de rr (3.1.0 ou supérieure) est requise.

### Reproducing concurrency bugs with rr

rr simule une machine à un seul fil par défaut. Pour déboguer du code concurrent, vous pouvez utiliser `rr record --chaos`, ce qui amènera rr à simuler entre un et huit cœurs, choisis au hasard. Vous voudrez donc peut-être définir `JULIA_NUM_THREADS=8` et relancer votre code sous rr jusqu'à ce que vous ayez trouvé votre bug.

# [Proper maintenance and care of multi-threading locks](@id Proper-maintenance-and-care-of-multi-threading-locks)

Les stratégies suivantes sont utilisées pour garantir que le code est exempt de blocage (généralement en s'attaquant à la 4ème condition de Coffman : l'attente circulaire).

> 1. structure le code de manière à ce qu'un seul verrou doive être acquis à la fois
> 2. acquérir toujours des verrous partagés dans le même ordre, comme indiqué dans le tableau ci-dessous
> 3. évitez les constructions qui s'attendent à avoir besoin d'une récursion illimitée


## Locks

Voici tous les verrous qui existent dans le système et les mécanismes pour les utiliser qui évitent le potentiel de blocage (aucun algorithme d'autruche autorisé ici) :

Les éléments suivants sont définitivement des verrous de feuille (niveau 1) et ne doivent pas essayer d'acquérir d'autres verrous :

>   * safepoint
>
>     > Notez que ce verrou est acquis implicitement par `JL_LOCK` et `JL_UNLOCK`. Utilisez les variantes `_NOGC` pour éviter cela pour les verrous de niveau 1.
>     >
>     > Tout en tenant ce verrou, le code ne doit pas effectuer d'allocation ni atteindre des points de sécurité. Notez qu'il y a des points de sécurité lors de l'allocation, de l'activation / désactivation du GC, de l'entrée / restauration des cadres d'exception, et de la prise / libération de verrous.
>   * carte_partagée
>   * finalisateurs
>   * pagealloc
>   * gc*perm*lock
>   * flisp
>   * jl*in*stackwalk (Win32)
>   * ResourcePool<?>::mutex
>   * RLST_mutex
>   * llvm*impression*mutex
>   * jl*verrouillé*flux::mutex
>   * debuginfo_asyncsafe
>   * inférence*temps*déverrouillage
>   * ExecutionEngine::SessionLock
>
>     > flisp lui-même est déjà thread-safe, ce verrou protège uniquement le pool `jl_ast_context_list_t`, de même que les mutexes ResourcePool<?>::protègent simplement le pool de ressources associé.


Le suivant est un verrou de feuille (niveau 2), et n'acquiert que des verrous de niveau 1 (safepoint) en interne :

>   * global*roots*lock
>   * Module->verrouiller
>   * JLDebuginfoPlugin::PluginMutex
>   * nouvellement*inféré*mutex


Le suivant est un verrou de niveau 3, qui ne peut acquérir que des verrous de niveau 1 ou de niveau 2 en interne :

>   * Méthode->verrouillageécriture
>   * typecache


Le suivant est un verrou de niveau 4, qui ne peut se récursivement acquérir que des verrous de niveau 1, 2 ou 3 :

>   * MethodTable->verrouillageécriture


Aucun code Julia ne peut être appelé tout en maintenant un verrou au-dessus de ce point.

orc::ThreadSafeContext (TSCtx) locks occupent une place spéciale dans la hiérarchie de verrouillage. Ils sont utilisés pour protéger l'état global non thread-safe d'LLVM, mais il peut y en avoir un nombre arbitraire. Par défaut, tous ces verrous peuvent être considérés comme des verrous de niveau 5 aux fins de comparaison avec le reste de la hiérarchie. L'acquisition d'un TSCtx ne doit être effectuée qu'à partir du pool de TSCtx du JIT, et tous les verrous sur ce TSCtx doivent être libérés avant de le retourner au pool. Si plusieurs verrous TSCtx doivent être acquis en même temps (en raison d'une compilation récursive), alors les verrous doivent être acquis dans l'ordre dans lequel les TSCtx ont été empruntés au pool.

Le niveau suivant est un verrou de niveau 5

>   * JuliaOJIT::EmissionMutex


Le suivant est un verrou de niveau 6, qui ne peut se récursivement acquérir des verrous à des niveaux inférieurs :

>   * codegen
>   * jl*modules*mutex


Le suivant est un verrou presque racine (niveau fin-1), ce qui signifie que seul le verrou racine peut être détenu lors de la tentative de l'acquérir :

>   * typeinf
>
>     > celui-ci est peut-être l'un des plus délicats, car l'inférence de type peut être invoquée à partir de nombreux points
>     >
>     > actuellement, le verrou est fusionné avec le verrou de génération de code, car ils s'appellent mutuellement de manière récursive.


Le verrou suivant synchronise l'opération d'E/S. Soyez conscient que faire des E/S (par exemple, imprimer des messages d'avertissement ou des informations de débogage) tout en maintenant un autre verrou énuméré ci-dessus peut entraîner des interblocages pernicieux et difficiles à détecter. SOYEZ TRÈS PRUDENT !

>   * iolock
>   * Verrous de synchronisation de fil individuels
>
>     > cela peut continuer à être maintenu après la libération de l'iolock, ou acquis sans lui, mais soyez très prudent de ne jamais tenter d'acquérir l'iolock tout en le tenant
>   * Libdl.LazyLibrary verrou


Le suivant est le verrou racine, ce qui signifie qu'aucun autre verrou ne doit être détenu lors de la tentative de l'acquérir :

>   * niveau supérieur
>
>     > cela devrait être effectué lors de la tentative d'une action de haut niveau (comme la création d'un nouveau type ou la définition d'une nouvelle méthode) : essayer d'obtenir ce verrou à l'intérieur d'une fonction mise en scène provoquera une condition de blocage !
>     >
>     > de plus, il n'est pas clair si *quelque* code peut s'exécuter en toute sécurité en parallèle avec une expression de niveau supérieur arbitraire, donc il peut être nécessaire que tous les threads atteignent d'abord un point de sécurité


## Broken Locks

Les serrures suivantes sont cassées :

  * niveau supérieur

    > n'existe pas en ce moment
    >
    > corriger : créez-le
  * Module->verrouiller

    > Cela est vulnérable aux interblocages car il ne peut pas être certain qu'il est acquis dans l'ordre. Certaines opérations (comme `import_module`) manquent d'un verrou.
    >
    > fix : remplacer par `jl_modules_mutex` ?
  * loading.jl : `require` et `register_root_module`

    > Ce fichier a potentiellement de nombreux problèmes.
    >
    > fix : nécessite des verrous

## Shared Global Data Structures

Ces structures de données nécessitent chacune des verrous en raison de l'état global mutable partagé. C'est la liste inverse de la liste de priorité des verrous ci-dessus. Cette liste n'inclut pas les ressources de niveau 1 en raison de leur simplicité.

Modifications de MethodTable (def, cache) : MethodTable->verrouillage d'écriture

Déclarations de type : verrouillage de niveau supérieur

Type application : verrou de cache de type

Tables de variables globales : Module->verrou

Module sérialiseur : verrou de niveau supérieur

JIT et inférence de type : verrouillage de génération de code

Mises à jour de MethodInstance/CodeInstance : Method->verrou d'écriture, verrou de génération de code

>   * Ceci est défini lors de la construction et immuable :
>
>       * typesDeSpec
>       * sparam_vals
>       * def
>       * propriétaire


>   * Ceci est défini par `jl_type_infer` (tout en maintenant le verrou de génération de code) :
>
>       * cache
>       * rettype
>       * inféré


```
    * valid ages
```

>   * `inInference` drapeau :
>
>       * optimisation pour éviter rapidement de retomber dans `jl_type_infer` alors qu'il est déjà en cours d'exécution
>       * l'état actuel (de la définition de `inferred`, puis `fptr`) est protégé par le verrou de génération de code


>   * Pointeurs de fonction :
>
>       * ces transitions se produisent une fois, de `NULL` à une valeur, pendant que le verrou de génération de code est maintenu
>   * Cache du générateur de code (le contenu de `functionObjectsDecls`) :
>
>       * ces derniers peuvent passer plusieurs fois, mais uniquement pendant que le verrou de génération de code est maintenu
>       * il est valide d'utiliser une ancienne version de cela, ou de bloquer pour de nouvelles versions de cela, donc les courses sont bénignes, tant que le code veille à ne pas référencer d'autres données dans l'instance de méthode (comme `rettype`) et suppose qu'elles sont coordonnées, à moins de détenir également le verrou de génération de code


LLVMContext : verrouillage de la génération de code

Méthode : Méthode->verrouillerécriture

  * racines tableau (sérialiseur et génération de code)
  * invoquer / spécialisations / modifications de tfunc

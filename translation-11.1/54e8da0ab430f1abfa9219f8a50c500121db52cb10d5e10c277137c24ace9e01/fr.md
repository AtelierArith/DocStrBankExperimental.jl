```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/NEWS.md"
```

# Julia v1.11 Release Notes

## New language features

  * Nouveau type `Memory` qui fournit un conteneur de niveau inférieur comme alternative à `Array`. `Memory` a moins de surcharge et un constructeur plus rapide, ce qui en fait un bon choix pour les situations qui n'ont pas besoin de toutes les fonctionnalités de `Array` (par exemple, plusieurs dimensions). La plupart du type `Array` est maintenant implémentée en Julia sur la base de `Memory`, ce qui entraîne des gains de vitesse significatifs pour plusieurs fonctions (par exemple, `push!`) ainsi qu'un code plus maintenable ([#51319](https://github.com/JuliaLang/julia/issues/51319)).
  * `public` is a new keyword. Symbols marked with `public` are considered public API. Symbols marked with `export` are now also treated as public API. The difference between `public` and `export` is that `public` names do not become available when `using` a package/module ([#50105](https://github.com/JuliaLang/julia/issues/50105)).
  * `ScopedValue` implémente un scope dynamique avec héritage à travers les tâches ([#50958](https://github.com/JuliaLang/julia/issues/50958)).
  * Les fichiers `Manifest.toml` peuvent désormais être renommés au format `Manifest-v{major}.{minor}.toml` pour être préférentiellement utilisés par la version julia donnée. Par exemple, dans le même dossier, un `Manifest-v1.11.toml` serait utilisé par v1.11 et `Manifest.toml` par toutes les autres versions de julia. Cela facilite la gestion des environnements pour plusieurs versions de julia en même temps ([#43845](https://github.com/JuliaLang/julia/issues/43845)).
  * Support pour Unicode 15.1 ([#51799](https://github.com/JuliaLang/julia/issues/51799)).

## Language changes

  * Lors de la précompilation, les hooks `atexit` s'exécutent maintenant avant d'enregistrer le fichier de sortie. Cela permet aux utilisateurs de détruire en toute sécurité l'état en arrière-plan (comme la fermeture des `Timer`s et l'envoi de notifications de déconnexion aux tâches de heartbeat) et de nettoyer d'autres ressources lorsque le programme souhaite commencer à quitter.
  * La couverture de code et le suivi de malloc ne sont plus générés pendant la phase de précompilation du package. De plus, pendant ces modes, des caches pkgimage sont désormais utilisés pour les packages qui ne sont pas suivis. Cela signifie que les tests de couverture (le paramètre par défaut pour `julia-actions/julia-runtest`) utiliseront par défaut des caches pkgimage pour tous les autres packages que le package testé, ce qui signifie probablement une exécution des tests plus rapide ([#52123](https://github.com/JuliaLang/julia/issues/52123)).
  * Spécifier un chemin dans `JULIA_DEPOT_PATH` entraîne désormais l'expansion des chaînes vides pour omettre le dépôt utilisateur par défaut ([#51448](https://github.com/JuliaLang/julia/issues/51448)).
  * Les fichiers de cache de précompilation sont désormais déplaçables et leur validité est maintenant vérifiée par un hachage de contenu de leurs fichiers sources au lieu de leur `mtime` ([#49866](https://github.com/JuliaLang/julia/issues/49866)).
  * Les extensions peuvent désormais dépendre d'autres extensions, si leurs déclencheurs incluent tous les déclencheurs de toute extension dont elles souhaitent dépendre (+ au moins un autre déclencheur). Les dépendances d'extension à extension qui ne répondent pas à cette exigence sont désormais bloquées de l'utilisation de `Base.get_extension` pendant la pré-compilation, afin de prévenir les cycles d'extension [#55557](https://github.com/JuliaLang/julia/issues/55557).

## Compiler/Runtime improvements

  * Mise à jour des heuristiques GC pour compter les pages allouées au lieu des objets individuels ([#50144](https://github.com/JuliaLang/julia/issues/50144)).
  * Added support for annotating `Base.@assume_effects` on code blocks ([#52400](https://github.com/JuliaLang/julia/issues/52400)).

## Command-line option changes

  * Le point d'entrée pour Julia a été standardisé en `Main.main(args)`. Cela doit être explicitement choisi en utilisant le macro `@main` (voir la docstring pour plus de détails). Lorsqu'il est choisi, et que `julia` est invoqué pour exécuter un script ou une expression (c'est-à-dire en utilisant `julia script.jl` ou `julia -e expr`), `julia` exécutera ensuite automatiquement la fonction `Main.main`. Cela vise à unifier les flux de travail de script et de compilation, où le chargement de code peut se produire dans le compilateur et l'exécution de `Main.main` peut se produire dans l'exécutable résultant. Pour une utilisation interactive, il n'y a pas de différence sémantique entre la définition d'une fonction `main` et l'exécution du code directement à la fin du script ([#50974](https://github.com/JuliaLang/julia/issues/50974)).
  * Les options `--compiled-modules` et `--pkgimages` peuvent désormais être définies sur `existing`, ce qui amènera Julia à envisager le chargement de fichiers de cache existants, mais pas à en créer de nouveaux ([#50586](https://github.com/JuliaLang/julia/issues/50586), [#52573](https://github.com/JuliaLang/julia/issues/52573)).
  * L'argument `--project` accepte désormais `@script` pour donner un chemin vers un répertoire avec un Project.toml relatif au fichier de script passé. `--project=@script/foo` pour le sous-répertoire `foo`. Si aucun chemin n'est donné après (c'est-à-dire `--project=@script`), alors (comme `--project=@.`) le répertoire et ses parents sont recherchés pour un Project.toml ([#50864](https://github.com/JuliaLang/julia/issues/50864) et [#53352](https://github.com/JuliaLang/julia/issues/53352))

## Multi-threading changes

  * `Threads.@threads` prend désormais en charge le planificateur `:greedy`, destiné aux charges de travail non uniformes ([#52096](https://github.com/JuliaLang/julia/issues/52096)).
  * Une nouvelle structure publique (mais non exportée) `Base.Lockable{T, L<:AbstractLock}` facilite le regroupement d'une ressource et de son verrou ensemble ([#52898](https://github.com/JuliaLang/julia/issues/52898)).

## Build system changes

  * Il y a un nouveau `Makefile` pour construire Julia et LLVM en utilisant les stratégies d'optimisations guidées par le profil et d'optimisations au moment de la liaison (PGO et LTO), voir `contrib/pgo-lto/Makefile` ([#45641](https://github.com/JuliaLang/julia/issues/45641)).

## New library functions

  * Trois nouveaux types autour de l'idée de texte avec des "annotations" (`Pair{Symbol, Any}` entrées, par exemple `:lang => "en"` ou `:face => :magenta`). Ces annotations sont préservées à travers les opérations (par exemple, la concaténation de chaînes avec `*`) lorsque cela est possible.

      * `AnnotatedString` est un nouveau type `AbstractString`. Il enveloppe une chaîne sous-jacente et permet d'attacher des annotations à des régions de la chaîne. Ce type est utilisé de manière extensive dans la nouvelle bibliothèque standard `StyledStrings` pour contenir des informations de style.
      * `AnnotatedChar` est un nouveau type `AbstractChar`. Il enveloppe un autre char et contient une liste d'annotations qui s'appliquent à celui-ci.
      * `AnnotatedIOBuffer` est un nouveau type `IO` qui imite un `IOBuffer`, mais possède des méthodes `read`/`write` spécialisées pour le contenu annoté. Cela peut être considéré à la fois comme une sorte de "constructeur de chaînes" et aussi comme un lien entre le contenu annoté et non annoté.
  * `in!(x, s::AbstractSet)` renverra si `x` est dans `s`, et insérera `x` dans `s` si ce n'est pas le cas ([#45156](https://github.com/JuliaLang/julia/issues/45156), [#51636](https://github.com/JuliaLang/julia/issues/51636)).
  * La nouvelle fonction `Libc.mkfifo` enveloppe la fonction C `mkfifo` sur les plateformes Unix ([#34587](https://github.com/JuliaLang/julia/issues/34587)).
  * `logrange(start, stop; length)` makes a range of constant ratio, instead of constant step ([#39071](https://github.com/JuliaLang/julia/issues/39071))
  * `copyuntil(out, io, delim)` et `copyline(out, io)` copient des données dans un flux `out::IO` ([#48273](https://github.com/JuliaLang/julia/issues/48273)).
  * `eachrsplit(string, pattern)` itère sur les sous-chaînes séparées de droite à gauche ([#51646](https://github.com/JuliaLang/julia/issues/51646)).
  * `Sys.username()` peut être utilisé pour renvoyer le nom d'utilisateur actuel ([#51897](https://github.com/JuliaLang/julia/issues/51897)).
  * `Sys.isreadable(), Sys.iswritable()` peuvent être utilisés pour vérifier si l'utilisateur actuel a des permissions d'accès qui permettent la lecture et l'écriture, respectivement. ([#53320](https://github.com/JuliaLang/julia/issues/53320)).
  * `GC.logging_enabled()` peut être utilisé pour tester si la journalisation GC a été activée via `GC.enable_logging` ([#51647](https://github.com/JuliaLang/julia/issues/51647)).
  * `IdSet` est maintenant exporté de Base et considéré comme public ([#53262](https://github.com/JuliaLang/julia/issues/53262)).
  * `@time` rapporte maintenant un compte de tous les conflits de verrouillage où un `ReentrantLock` a dû attendre, plus une nouvelle macro `@lock_conflicts` qui renvoie ce compte ([#52883](https://github.com/JuliaLang/julia/issues/52883)).
  * Le nouveau macro `Base.Cartesian.@ncallkw` est analogue à `Base.Cartesian.@ncall`, mais permet d'ajouter des arguments de mot-clé à l'appel de fonction ([#51501](https://github.com/JuliaLang/julia/issues/51501)).
  * Nouvelle fonction `Docs.hasdoc(module, symbol)` indique si un nom a une docstring ([#52139](https://github.com/JuliaLang/julia/issues/52139)).
  * Nouvelle fonction `Docs.undocumented_names(module)` renvoie les noms publics non documentés d'un module ([#52413](https://github.com/JuliaLang/julia/issues/52413)).

## New library features

  * `invmod(n, T)` où `T` est un type entier natif calcule maintenant l'inverse modulaire de `n` dans l'anneau d'entiers modulaires que définit `T` ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `invmod(n)` est une abréviation pour `invmod(n, typeof(n))` pour les types d'entiers natifs ([#52180](https://github.com/JuliaLang/julia/issues/52180)).
  * `replace(string, pattern...)` prend désormais en charge un argument `IO` optionnel pour écrire la sortie dans un flux plutôt que de renvoyer une chaîne ([#48625](https://github.com/JuliaLang/julia/issues/48625)).
  * Nouvelles méthodes `allequal(f, itr)` et `allunique(f, itr)` prenant une fonction prédicat ([#47679](https://github.com/JuliaLang/julia/issues/47679)).
  * `sizehint!(s, n)` prend maintenant en charge un argument `shrink` optionnel pour désactiver le rétrécissement ([#51929](https://github.com/JuliaLang/julia/issues/51929)).
  * Passer un `IOBuffer` comme argument stdout pour le spawn de `Process` fonctionne désormais comme prévu, synchronisé avec `wait` ou `success`, donc un `Base.BufferStream` n'est plus requis là pour garantir l'exactitude afin d'éviter les courses de données ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * Après qu'un processus se termine, `closewrite` ne sera plus appelé automatiquement sur le flux qui lui a été passé. Appelez `wait` sur le processus à la place pour vous assurer que le contenu est entièrement écrit, puis appelez `closewrite` manuellement pour éviter les courses de données, ou utilisez la forme de rappel de `open` pour que tout cela soit géré automatiquement ([#52461](https://github.com/JuliaLang/julia/issues/52461)).
  * `@timed` renvoie désormais également le temps de compilation et de recompilation écoulé ([#52889](https://github.com/JuliaLang/julia/issues/52889)).
  * `filter` peut maintenant agir sur un `NamedTuple` ([#50795](https://github.com/JuliaLang/julia/issues/50795)).
  * `Iterators.cycle(iter, n)` parcourt `iter` un nombre fixe de fois, au lieu de le faire indéfiniment ([#47354](https://github.com/JuliaLang/julia/issues/47354)).
  * `zero(::AbstractArray)` s'applique maintenant de manière récursive, donc `zero([[1,2],[3,4,5]])` produit maintenant l'identité additive `[[0,0],[0,0,0]]` au lieu de générer une erreur ([#38064](https://github.com/JuliaLang/julia/issues/38064)).
  * `include_dependency(path; track_content=true)` permet de passer de l'utilisation de `mtime` au hachage de la dépendance de précompilation afin de restaurer la relocatabilité des caches de précompilation ([#51798](https://github.com/JuliaLang/julia/issues/51798)).

## Standard library changes

  * La méthode de secours `write(::IO, ::AbstractArray)` qui appelait récursivement `write` sur chaque élément, écrit maintenant la représentation en mémoire de chaque valeur. Par exemple, `write(io, 'a':'b')` écrit maintenant 4 octets pour chaque caractère, au lieu d'écrire la représentation UTF-8 de chaque caractère. Le nouveau format est compatible avec celui utilisé par `Array`, ce qui permet d'utiliser `read!` pour récupérer les données ([#42593](https://github.com/JuliaLang/julia/issues/42593)).
  * Il n'est pas possible de définir `length` pour les itérateurs avec état de manière généralement cohérente. Le potentiel de résultats incorrects silencieux pour les itérateurs `Stateful` est abordé en supprimant la méthode `length(::Stateful)`. Le dernier paramètre de type de `Stateful` a également disparu. Problème : ([#47790](https://github.com/JuliaLang/julia/issues/47790)), PR : ([#51747](https://github.com/JuliaLang/julia/issues/51747)).

#### Package Manager

  * Il est désormais possible de spécifier des "sources" pour les paquets dans une section `[sources]` dans Project.toml. Cela peut être utilisé pour ajouter des dépendances normales ou de test non enregistrées.
  * Pkg respecte désormais les limites `[compat]` pour `julia` et génère une erreur si la version du binaire Julia en cours d'exécution est incompatible avec les limites dans `Project.toml`. Pkg a toujours respecté cette compatibilité lors du travail avec des packages de registre. Ce changement affecte principalement les packages locaux.
  * `pkg> add` et `Pkg.add` ajouteront désormais des entrées de compatibilité pour les nouvelles dépendances directes si l'environnement actif est un package (a une entrée `name` et `uuid`).
  * Les dépendances peuvent désormais être ajoutées directement en tant que dépendances faibles ou extras via les formes `pkg> add --weak/extra Foo` ou `Pkg.add("Foo", target=:weakdeps/:extras)`.

#### StyledStrings

  * Une nouvelle bibliothèque standard pour gérer le style de manière plus complète et structurée ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * La nouvelle structure `Faces` sert de conteneur pour les informations de style de texte (pensez à la police, ainsi qu'à la couleur et à la décoration), et est accompagnée d'un cadre pour fournir une approche pratique, extensible (via `addface!`) et personnalisable (avec un fichier `Faces.toml` de l'utilisateur et `loadfaces!`) pour le contenu stylisé ([#49586](https://github.com/JuliaLang/julia/issues/49586)).
  * Le nouveau macro de chaîne `@styled_str` fournit un moyen pratique de créer un `AnnotatedString` avec diverses faces ou autres attributs appliqués ([#49586](https://github.com/JuliaLang/julia/issues/49586)).

#### Libdl

  * Un nouveau type `LazyLibrary` est exporté depuis `Libdl` pour être utilisé dans la construction de chargements de bibliothèques paresseux en chaîne, principalement destiné à être utilisé dans les JLL ([#50074](https://github.com/JuliaLang/julia/issues/50074)).

#### LinearAlgebra

  * `cbrt(::AbstractMatrix{<:Real})` est maintenant défini et renvoie des racines cubiques de matrices à valeurs réelles de matrices à valeurs réelles. ([#50661](https://github.com/JuliaLang/julia/issues/50661))
  * `eigvals/eigen(A, bunchkaufman(B))` et `eigvals/eigen(A, lu(B))`, qui utilisent respectivement la décomposition Bunchkaufman (LDL) et LU de `B`, calculent maintenant efficacement les valeurs propres généralisées (`eigen`: et vecteurs propres) de `A` et `B`. Remarque : Le deuxième argument est la sortie de `bunchkaufman` ou `lu` ([#50471](https://github.com/JuliaLang/julia/issues/50471)).
  * Il existe maintenant un dispatch spécialisé pour `eigvals/eigen(::Hermitian{<:Tridiagonal})` qui effectue une transformation de similarité pour créer une matrice tridiagonale symétrique réelle, et la résout en utilisant les routines LAPACK ([#49546](https://github.com/JuliaLang/julia/issues/49546)).
  * Les matrices structurées conservent maintenant soit les axes du parent (pour `Symmetric`/`Hermitian`/`AbstractTriangular`/`UpperHessenberg`), soit ceux de la diagonale principale (pour les matrices bandées) ([#52480](https://github.com/JuliaLang/julia/issues/52480)).
  * `bunchkaufman` et `bunchkaufman!` fonctionnent désormais pour tout `AbstractFloat`, `Rational` et leurs variantes complexes. `bunchkaufman` prend désormais en charge les types `Integer`, en effectuant une conversion interne en `Rational{BigInt}`. Une nouvelle fonction `inertia` a été ajoutée, qui calcule l'inertie du facteur diagonal donné par l'objet de factorisation `BunchKaufman` d'une matrice réelle symétrique ou hermitienne. Pour les matrices symétriques complexes, `inertia` ne calcule que le nombre de valeurs propres nulles du facteur diagonal ([#51487](https://github.com/JuliaLang/julia/issues/51487)).
  * Packages that specialize matrix-matrix `mul!` with a method signature of the form `mul!(::AbstractMatrix, ::MyMatrix, ::AbstractMatrix, ::Number, ::Number)` no longer encounter method ambiguities when interacting with `LinearAlgebra`. Previously, ambiguities used to arise when multiplying a `MyMatrix` with a structured matrix type provided by LinearAlgebra, such as `AbstractTriangular`, which used to necessitate additional methods to resolve such ambiguities. Similar sources of ambiguities have also been removed for matrix-vector `mul!` operations ([#52837](https://github.com/JuliaLang/julia/issues/52837)).
  * `lu` et `issuccess(::LU)` acceptent maintenant un argument clé `allowsingular`. Lorsqu'il est défini sur `true`, une factorisation valide avec un facteur U de rang déficient sera considérée comme un succès au lieu de générer une erreur. De telles factorizations sont désormais affichées en imprimant les facteurs accompagnés d'une note "rang déficient" au lieu d'imprimer un message "Échec de la factorisation" ([#52957](https://github.com/JuliaLang/julia/issues/52957)).

#### Random

  * `rand` prend désormais en charge l'échantillonnage sur les types `Tuple` ([#35856](https://github.com/JuliaLang/julia/issues/35856), [#50251](https://github.com/JuliaLang/julia/issues/50251)).
  * `rand` prend désormais en charge l'échantillonnage sur les types `Pair` ([#28705](https://github.com/JuliaLang/julia/issues/28705)).
  * Lors de l'initialisation des RNG fournis par `Random`, des graines entières négatives peuvent désormais être utilisées ([#51416](https://github.com/JuliaLang/julia/issues/51416)).
  * Les générateurs de nombres aléatoires semables de `Random` peuvent désormais être initialisés par une chaîne, par exemple `seed!(rng, "a random seed")` ([#51527](https://github.com/JuliaLang/julia/issues/51527)).

#### REPL

  * Les indices de complétion par tabulation s'affichent maintenant en texte plus clair lors de la saisie dans le REPL. Pour désactiver, définissez `Base.active_repl.options.hint_tab_completes = false` de manière interactive, ou dans startup.jl :

    ```
    if VERSION >= v"1.11.0-0"
      atreplinit() do repl
          repl.options.hint_tab_completes = false
      end
    end
    ```

    ([#51229](https://github.com/JuliaLang/julia/issues/51229)).
  * Meta-M avec un prompt vide bascule maintenant le module contextuel entre le précédent module contextuel non-Main et le Main, de sorte que le passage d'un à l'autre soit simple ([#51616](https://github.com/JuliaLang/julia/issues/51616), [#52670](https://github.com/JuliaLang/julia/issues/52670)).

#### Dates

La fonction non documentée `adjust` n'est plus exportée mais est maintenant documentée ([#53092](https://github.com/JuliaLang/julia/issues/53092)).

#### Statistics

  * Les statistiques sont désormais une bibliothèque standard évolutive ([#46501](https://github.com/JuliaLang/julia/issues/46501)).

#### Distributed

  * `pmap` utilise désormais par défaut un `CachingPool` ([#33892](https://github.com/JuliaLang/julia/issues/33892)).

## Deprecated or removed

  * `Base.map`, `Iterators.map` et `foreach` ont perdu leurs méthodes à un seul argument ([#52631](https://github.com/JuliaLang/julia/issues/52631)).

## External dependencies

  * La bibliothèque libuv a été mise à jour d'une version de v1.44.2 à v1.48.0 ([#49937](https://github.com/JuliaLang/julia/issues/49937)).
  * `tput` n'est plus appelé pour vérifier les capacités du terminal ; il a été remplacé par un analyseur terminfo pur-Julia ([#50797](https://github.com/JuliaLang/julia/issues/50797)).
  * La base de données d'informations sur le terminal, `terminfo`, est désormais intégrée par défaut, offrant une meilleure expérience utilisateur REPL lorsque `terminfo` n'est pas disponible sur le système. Julia peut être construite sans intégrer la base de données en utilisant l'option Makefile `WITH_TERMINFO=0`. ([#55411](https://github.com/JuliaLang/julia/issues/55411))

## Tooling Improvements

  * CI effectue désormais une détection automatique limitée des fautes de frappe sur toutes les PR. Si vous fusionnez une PR avec un échec de vérification de faute de frappe CI, les fautes de frappe signalées seront automatiquement ignorées lors des futures exécutions CI sur les PR qui modifient ces mêmes fichiers ([#51704](https://github.com/JuliaLang/julia/issues/51704)).

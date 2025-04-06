# Profiling

Le module `Profile` fournit des outils pour aider les développeurs à améliorer les performances de leur code. Lorsqu'il est utilisé, il prend des mesures sur le code en cours d'exécution et produit une sortie qui vous aide à comprendre combien de temps est passé sur chaque ligne. L'utilisation la plus courante est d'identifier les "goulots d'étranglement" comme cibles pour l'optimisation.

`Profile` implémente ce que l'on appelle un "échantillonnage" ou [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming)). Il fonctionne en prenant périodiquement une trace de retour pendant l'exécution de toute tâche. Chaque trace de retour capture la fonction actuellement en cours d'exécution et le numéro de ligne, ainsi que la chaîne complète des appels de fonction qui ont conduit à cette ligne, et constitue donc un "instantané" de l'état actuel de l'exécution.

Si une grande partie de votre temps d'exécution est consacrée à l'exécution d'une ligne de code particulière, cette ligne apparaîtra fréquemment dans l'ensemble de toutes les traces de retour. En d'autres termes, le "coût" d'une ligne donnée – ou en réalité, le coût de la séquence d'appels de fonction jusqu'à et y compris cette ligne – est proportionnel à la fréquence à laquelle elle apparaît dans l'ensemble de toutes les traces de retour.

Un profileur d'échantillonnage ne fournit pas une couverture complète ligne par ligne, car les traces de retour se produisent à des intervalles (par défaut, 1 ms sur les systèmes Unix et 10 ms sur Windows, bien que la planification réelle soit soumise à la charge du système d'exploitation). De plus, comme discuté plus loin, parce que les échantillons sont collectés à un sous-ensemble clairsemé de tous les points d'exécution, les données collectées par un profileur d'échantillonnage sont sujettes à du bruit statistique.

Malgré ces limitations, les profileurs d'échantillonnage ont des forces substantielles :

  * Vous n'avez pas besoin de modifier votre code pour prendre des mesures de temps.
  * Il peut se profiler dans le code source de Julia et même (optionnellement) dans les bibliothèques C et Fortran.
  * En exécutant "infrequently", il y a très peu de surcharge de performance ; lors du profilage, votre code peut s'exécuter à une vitesse presque native.

Pour ces raisons, il est recommandé d'essayer d'utiliser le profileur d'échantillonnage intégré avant d'envisager d'autres alternatives.

## Basic usage

Travaillons avec un cas de test simple :

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

C'est une bonne idée d'exécuter d'abord le code que vous souhaitez profiler au moins une fois (à moins que vous ne souhaitiez profiler le compilateur JIT de Julia) :

```julia-repl
julia> myfunc() # run once to force compilation
```

Maintenant, nous sommes prêts à profiler cette fonction :

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

Pour voir les résultats de profilage, il existe plusieurs navigateurs graphiques. Une "famille" de visualiseurs est basée sur [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl), chaque membre de la famille offrant une interface utilisateur différente :

  * [VS Code](https://www.julia-vscode.org/) est un IDE complet avec un support intégré pour la visualisation de profils.
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl) est un visualiseur autonome basé sur GTK.
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl) utilise VegaLight et s'intègre bien avec les notebooks Jupyter.
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl) produit du HTML et présente des résumés supplémentaires, et s'intègre également bien avec les notebooks Jupyter.
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl) rend un SVG
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl) sert un site web local pour inspecter des graphiques, des flammes graphiques et plus encore.
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) est une interface utilisateur de visualisation de profil basée sur un canvas HTML, utilisée par le [Julia VS Code extension](https://www.julia-vscode.org/), mais peut également générer des fichiers HTML interactifs.

Une approche entièrement indépendante pour la visualisation de profil est [PProf.jl](https://github.com/vchuravy/PProf.jl), qui utilise l'outil externe `pprof`.

Ici, cependant, nous utiliserons l'affichage basé sur le texte qui vient avec la bibliothèque standard :

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

Chaque ligne de cet affichage représente un emplacement particulier (numéro de ligne) dans le code. L'indentation est utilisée pour indiquer la séquence imbriquée des appels de fonction, les lignes plus indentées étant plus profondes dans la séquence des appels. Dans chaque ligne, le premier "champ" est le nombre de traces de retour (échantillons) prises *à cette ligne ou dans toutes les fonctions exécutées par cette ligne*. Le deuxième champ est le nom du fichier et le numéro de ligne, et le troisième champ est le nom de la fonction. Notez que les numéros de ligne spécifiques peuvent changer à mesure que le code de Julia évolue ; si vous souhaitez suivre, il est préférable d'exécuter cet exemple vous-même.

Dans cet exemple, nous pouvons voir que la fonction de niveau supérieur appelée se trouve dans le fichier `event.jl`. C'est la fonction qui exécute le REPL lorsque vous lancez Julia. Si vous examinez la ligne 97 de `REPL.jl`, vous verrez que c'est là que la fonction `eval_user_input()` est appelée. C'est la fonction qui évalue ce que vous tapez dans le REPL, et comme nous travaillons de manière interactive, ces fonctions ont été invoquées lorsque nous avons entré `@profile myfunc()`. La ligne suivante reflète les actions entreprises dans le macro [`@profile`](@ref).

La première ligne montre que 80 traces de retour ont été prises à la ligne 73 de `event.jl`, mais ce n'est pas que cette ligne était "coûteuse" en soi : la troisième ligne révèle que toutes ces 80 traces de retour ont en fait été déclenchées à l'intérieur de son appel à `eval_user_input`, et ainsi de suite. Pour découvrir quelles opérations prennent réellement du temps, nous devons examiner plus en profondeur la chaîne d'appels.

La première ligne "importante" dans cette sortie est celle-ci :

```
52 ./REPL[1]:2; myfunc()
```

`REPL` fait référence au fait que nous avons défini `myfunc` dans le REPL, plutôt que de le mettre dans un fichier ; si nous avions utilisé un fichier, cela montrerait le nom du fichier. Le `[1]` indique que la fonction `myfunc` était la première expression évaluée dans cette session REPL. La ligne 2 de `myfunc()` contient l'appel à `rand`, et il y a eu 52 (sur 80) traces de retour qui se sont produites à cette ligne. En dessous, vous pouvez voir un appel à `dsfmt_fill_array_close_open!` à l'intérieur de `dSFMT.jl`.

Un peu plus bas, vous voyez :

```
28 ./REPL[1]:3; myfunc()
```

La ligne 3 de `myfunc` contient l'appel à `maximum`, et il y a eu 28 (sur 80) traces de retour prises ici. En dessous, vous pouvez voir les endroits spécifiques dans `base/reduce.jl` qui effectuent les opérations chronophages dans la fonction `maximum` pour ce type de données d'entrée.

Dans l'ensemble, nous pouvons conclure de manière provisoire que la génération de nombres aléatoires est environ deux fois plus coûteuse que la recherche de l'élément maximum. Nous pourrions augmenter notre confiance dans ce résultat en collectant davantage d'échantillons :

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

En général, si vous avez `N` échantillons collectés à une ligne, vous pouvez vous attendre à une incertitude de l'ordre de `sqrt(N)` (en écartant d'autres sources de bruit, comme la charge de l'ordinateur avec d'autres tâches). La principale exception à cette règle est la collecte des déchets, qui s'exécute rarement mais tend à être assez coûteuse. (Puisque le collecteur de déchets de Julia est écrit en C, de tels événements peuvent être détectés en utilisant le mode de sortie `C=true` décrit ci-dessous, ou en utilisant [ProfileView.jl](https://github.com/timholy/ProfileView.jl).)

Ceci illustre le dump "arbre" par défaut ; une alternative est le dump "plat", qui accumule les comptes indépendamment de leur imbrication :

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

Si votre code contient de la récursion, un point potentiellement déroutant est qu'une ligne dans une fonction "enfant" peut accumuler plus de comptes qu'il n'y a de retours en arrière au total. Considérez les définitions de fonction suivantes :

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

Si vous deviez profiler `dumbsum3`, et qu'une trace de pile était prise pendant son exécution `dumbsum(1)`, la trace de pile ressemblerait à ceci :

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

Par conséquent, cette fonction enfant obtient 3 comptes, même si le parent n'en obtient qu'un. La représentation en "arbre" rend cela beaucoup plus clair, et pour cette raison (entre autres), c'est probablement la manière la plus utile de voir les résultats.

## Accumulation and clearing

Les résultats de [`@profile`](@ref) s'accumulent dans un tampon ; si vous exécutez plusieurs morceaux de code sous `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566`, alors [`Profile.print()`](@ref) vous montrera les résultats combinés. Cela peut être très utile, mais parfois vous voulez repartir de zéro ; vous pouvez le faire avec [`Profile.clear()`](@ref).

## Options for controlling the display of profile results

[`Profile.print`](@ref) a plus d'options que celles que nous avons décrites jusqu'à présent. Voyons la déclaration complète :

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

Discutons d'abord des deux arguments positionnels, puis des arguments par mot-clé :

  * `io` – Vous permet d'enregistrer les résultats dans un tampon, par exemple un fichier, mais la valeur par défaut est d'imprimer sur `stdout` (la console).
  * `data` – Contient les données que vous souhaitez analyser ; par défaut, cela est obtenu à partir de [`Profile.fetch()`](@ref), qui extrait les traces de retour d'un tampon pré-alloué. Par exemple, si vous souhaitez profiler le profileur, vous pourriez dire :

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

Les arguments de mot-clé peuvent être n'importe quelle combinaison de :

  * `format` – Introduit ci-dessus, détermine si les traces de retour sont imprimées avec (par défaut, `:tree`) ou sans (`:flat`) indentation indiquant la structure arborescente.
  * `C` – Si `true`, les traces de retour du code C et Fortran sont affichées (normalement, elles sont exclues). Essayez d'exécuter l'exemple d'introduction avec `Profile.print(C = true)`. Cela peut être extrêmement utile pour décider si c'est le code Julia ou le code C qui cause un goulet d'étranglement ; définir `C = true` améliore également l'interprétabilité de l'imbrication, au prix de dumps de profil plus longs.
  * `combine` – Certaines lignes de code contiennent plusieurs opérations ; par exemple, `s += A[i]` contient à la fois une référence de tableau (`A[i]`) et une opération de somme. Celles-ci correspondent à différentes lignes dans le code machine généré, et il peut donc y avoir deux adresses ou plus capturées lors des traces de retour sur cette ligne. `combine = true` les regroupe, et c'est probablement ce que vous souhaitez généralement, mais vous pouvez générer une sortie séparée pour chaque pointeur d'instruction unique avec `combine = false`.
  * `maxdepth` – Limite les cadres à une profondeur supérieure à `maxdepth` dans le format `:tree`.
  * `sortedby` – Contrôle l'ordre dans le format `:flat`. `:filefuncline` (par défaut) trie par ligne source, tandis que `:count` trie par ordre du nombre d'échantillons collectés.
  * `noisefloor` – Limite les trames qui sont en dessous du seuil de bruit heuristique de l'échantillon (s'applique uniquement au format `:tree`). Une valeur suggérée à essayer pour cela est 2.0 (la valeur par défaut est 0). Ce paramètre masque les échantillons pour lesquels `n <= noisefloor * √N`, où `n` est le nombre d'échantillons sur cette ligne, et `N` est le nombre d'échantillons pour l'appelant.
  * `mincount` – Limite les trames avec moins de `mincount` occurrences.

Les noms de fichiers/fonctions sont parfois tronqués (avec `...`), et l'indentation est tronquée avec un `+n` au début, où `n` est le nombre d'espaces supplémentaires qui auraient été insérés, s'il y avait eu de la place. Si vous souhaitez un profil complet de code profondément imbriqué, il est souvent judicieux de sauvegarder dans un fichier en utilisant une `displaysize` large dans un [`IOContext`](@ref) :

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref) accumule simplement les traces de retour, et l'analyse se produit lorsque vous appelez [`Profile.print()`](@ref). Pour un calcul de longue durée, il est tout à fait possible que le tampon pré-alloué pour stocker les traces de retour soit rempli. Si cela se produit, les traces de retour s'arrêtent mais votre calcul continue. En conséquence, vous pourriez manquer certaines données de profilage importantes (vous recevrez un avertissement lorsque cela se produira).

Vous pouvez obtenir et configurer les paramètres pertinents de cette manière :

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n` est le nombre total de pointeurs d'instruction que vous pouvez stocker, avec une valeur par défaut de `10^6`. Si votre backtrace typique est de 20 pointeurs d'instruction, alors vous pouvez collecter 50000 backtraces, ce qui suggère une incertitude statistique de moins de 1 %. Cela peut être suffisant pour la plupart des applications.

Par conséquent, vous êtes plus susceptible d'avoir besoin de modifier `delay`, exprimé en secondes, qui définit la durée pendant laquelle Julia dispose entre les instantanés pour effectuer les calculs demandés. Un travail très long peut ne pas nécessiter de backtraces fréquents. Le paramètre par défaut est `delay = 0.001`. Bien sûr, vous pouvez diminuer le délai ainsi que l'augmenter ; cependant, le coût de la profilage augmente une fois que le délai devient similaire au temps nécessaire pour prendre un backtrace (~30 microsecondes sur l'ordinateur portable de l'auteur).

## Memory allocation analysis

L'une des techniques les plus courantes pour améliorer les performances est de réduire l'allocation de mémoire. Julia fournit plusieurs outils pour mesurer cela :

### `@time`

Le montant total de l'allocation peut être mesuré avec [`@time`](@ref), [`@allocated`](@ref) et [`@allocations`](@ref), et des lignes spécifiques déclenchant l'allocation peuvent souvent être déduites du profilage via le coût de la collecte des ordures que ces lignes entraînent. Cependant, parfois, il est plus efficace de mesurer directement la quantité de mémoire allouée par chaque ligne de code.

### GC Logging

Alors que [`@time`](@ref) enregistre des statistiques de haut niveau sur l'utilisation de la mémoire et la collecte des déchets au cours de l'évaluation d'une expression, il peut être utile d'enregistrer chaque événement de collecte des déchets, afin d'avoir une idée intuitive de la fréquence à laquelle le collecteur de déchets s'exécute, combien de temps il s'exécute à chaque fois et combien de déchets il collecte à chaque fois. Cela peut être activé avec [`GC.enable_logging(true)`](@ref), ce qui fait que Julia enregistre sur stderr chaque fois qu'une collecte de déchets se produit.

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    Cette fonctionnalité nécessite au moins Julia 1.8.


Le profileur d'allocation enregistre la trace de la pile, le type et la taille de chaque allocation pendant son exécution. Il peut être invoqué avec [`Profile.Allocs.@profile`](@ref).

Cette information sur les allocations est renvoyée sous forme d'un tableau d'objets `Alloc`, enveloppés dans un objet `AllocResults`. La meilleure façon de visualiser cela est actuellement avec les packages [PProf.jl](https://github.com/JuliaPerf/PProf.jl) et [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl), qui peuvent visualiser les piles d'appels qui effectuent le plus d'allocations.

Le profileur d'allocation a un coût significatif, donc un argument `sample_rate` peut être passé pour l'accélérer en lui faisant sauter certaines allocations. Passer `sample_rate=1.0` fera en sorte qu'il enregistre tout (ce qui est lent) ; `sample_rate=0.1` n'enregistrera que 10 % des allocations (plus rapide), etc.

!!! compat "Julia 1.11"
    Les anciennes versions de Julia ne pouvaient pas capturer les types dans tous les cas. Dans les anciennes versions de Julia, si vous voyez une allocation de type `Profile.Allocs.UnknownType`, cela signifie que le profileur ne sait pas quel type d'objet a été alloué. Cela se produisait principalement lorsque l'allocation provenait de code généré par le compilateur. Voir [issue #43688](https://github.com/JuliaLang/julia/issues/43688) pour plus d'infos.

    Depuis Julia 1.11, toutes les allocations doivent avoir un type signalé.


Pour plus de détails sur l'utilisation de cet outil, veuillez consulter la conférence suivante de JuliaCon 2022 : https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

Dans cet exemple simple, nous utilisons PProf pour visualiser le profil d'allocation. Vous pourriez utiliser un autre outil de visualisation à la place. Nous collectons le profil (en spécifiant un taux d'échantillonnage), puis nous le visualisons.

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

Voici un exemple plus approfondi, montrant comment nous pouvons ajuster le taux d'échantillonnage. Un bon nombre d'échantillons à viser est d'environ 1 à 10 mille. Trop d'échantillons, et le visualiseur de profil peut être submergé, et le profilage sera lent. Trop peu, et vous n'avez pas un échantillon représentatif.

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

Vous pouvez ensuite afficher le profil en naviguant vers http://localhost:62261, et le profil est enregistré sur le disque. Consultez le package PProf pour plus d'options.

##### Allocation Profiling Tips

Comme indiqué ci-dessus, visez environ 1 à 10 mille échantillons dans votre profil.

Notez que nous échantillonnons uniformément dans l'espace de *toutes les allocations*, et nous ne pondérons pas nos échantillons par la taille de l'allocation. Ainsi, un profil d'allocation donné peut ne pas donner un profil représentatif de l'endroit où la plupart des octets sont alloués dans votre programme, à moins que vous n'ayez défini `sample_rate=1`.

Les allocations peuvent provenir des utilisateurs construisant directement des objets, mais peuvent également venir de l'intérieur du runtime ou être insérées dans du code compilé pour gérer l'instabilité de type. Regarder la vue "code source" peut être utile pour les isoler, et d'autres outils externes tels que [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl) peuvent être utiles pour identifier la cause de l'allocation.

##### Allocation Profile Visualization Tools

Il existe plusieurs outils de visualisation de profilage qui peuvent tous afficher des Profils d'Allocation. Voici une petite liste de certains des principaux que nous connaissons :

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * Le visualiseur de profil intégré de VSCode (`@profview_allocs`) [documentation nécessaire]
  * Afficher les résultats directement dans le REPL

      * Vous pouvez inspecter les résultats dans le REPL via [`Profile.Allocs.fetch()`](@ref), pour voir la trace de la pile et le type de chaque allocation.

#### Line-by-Line Allocation Tracking

Une manière alternative de mesurer les allocations est de démarrer Julia avec l'option de ligne de commande `--track-allocation=<setting>`, pour laquelle vous pouvez choisir `none` (par défaut, ne pas mesurer l'allocation), `user` (mesurer l'allocation mémoire partout sauf dans le code de base de Julia), ou `all` (mesurer l'allocation mémoire à chaque ligne de code Julia). L'allocation est mesurée pour chaque ligne de code compilé. Lorsque vous quittez Julia, les résultats cumulés sont écrits dans des fichiers texte avec `.mem` ajouté après le nom du fichier, se trouvant dans le même répertoire que le fichier source. Chaque ligne liste le nombre total d'octets alloués. Le [`Coverage` package](https://github.com/JuliaCI/Coverage.jl) contient quelques outils d'analyse élémentaires, par exemple pour trier les lignes par ordre de nombre d'octets alloués.

En interprétant les résultats, il y a quelques détails importants. Sous le paramètre `user`, la première ligne de toute fonction appelée directement depuis le REPL affichera une allocation en raison des événements qui se produisent dans le code REPL lui-même. Plus significativement, la compilation JIT ajoute également aux comptes d'allocation, car une grande partie du compilateur de Julia est écrite en Julia (et la compilation nécessite généralement une allocation de mémoire). La procédure recommandée consiste à forcer la compilation en exécutant toutes les commandes que vous souhaitez analyser, puis à appeler [`Profile.clear_malloc_data()`](@ref) pour réinitialiser tous les compteurs d'allocation. Enfin, exécutez les commandes souhaitées et quittez Julia pour déclencher la génération des fichiers `.mem`.

!!! note
    `--track-allocation` modifie la génération de code pour enregistrer les allocations, et donc les allocations peuvent être différentes de ce qui se passe sans l'option. Nous recommandons d'utiliser le [allocation profiler](@ref allocation-profiler) à la place.


## External Profiling

Actuellement, Julia prend en charge `Intel VTune`, `OProfile` et `perf` en tant qu'outils de profilage externes.

Selon l'outil que vous choisissez, compilez avec `USE_INTEL_JITEVENTS`, `USE_OPROFILE_JITEVENTS` et `USE_PERF_JITEVENTS` définis sur 1 dans `Make.user`. Plusieurs indicateurs sont pris en charge.

Avant d'exécuter Julia, définissez la variable d'environnement [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING) à 1.

Maintenant, vous avez une multitude de façons d'utiliser ces outils ! Par exemple, avec `OProfile`, vous pouvez essayer un enregistrement simple :

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

Ou de manière similaire avec `perf` :

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

Il y a beaucoup d'autres choses intéressantes que vous pouvez mesurer à propos de votre programme. Pour obtenir une liste complète, veuillez lire le [Linux perf examples page](https://www.brendangregg.com/perf.html).

N'oubliez pas que perf enregistre pour chaque exécution un fichier `perf.data` qui, même pour de petits programmes, peut devenir assez volumineux. De plus, le module LLVM de perf enregistre temporairement des objets de débogage dans `~/.debug/jit`, n'oubliez pas de nettoyer ce dossier fréquemment.

# Multi-processing and Distributed Computing

Une implémentation de calcul parallèle en mémoire distribuée est fournie par le module [`Distributed`](@ref man-distributed) dans le cadre de la bibliothèque standard livrée avec Julia.

La plupart des ordinateurs modernes possèdent plus d'un CPU, et plusieurs ordinateurs peuvent être combinés dans un cluster. Exploiter la puissance de ces multiples CPU permet d'effectuer de nombreux calculs plus rapidement. Il y a deux facteurs majeurs qui influencent la performance : la vitesse des CPU eux-mêmes et la vitesse de leur accès à la mémoire. Dans un cluster, il est assez évident qu'un CPU donné aura le plus rapide accès à la RAM au sein du même ordinateur (nœud). Peut-être plus surprenant, des problèmes similaires sont pertinents sur un ordinateur portable multicœur typique, en raison des différences de vitesse de la mémoire principale et du [cache](https://www.akkadia.org/drepper/cpumemory.pdf). Par conséquent, un bon environnement de multiprocessus devrait permettre de contrôler la "propriété" d'un morceau de mémoire par un CPU particulier. Julia fournit un environnement de multiprocessus basé sur le passage de messages pour permettre aux programmes de s'exécuter sur plusieurs processus dans des domaines de mémoire séparés en même temps.

L'implémentation du passage de messages de Julia est différente des autres environnements tels que MPI[^1]. La communication en Julia est généralement "unilatérale", ce qui signifie que le programmeur doit gérer explicitement un seul processus dans une opération à deux processus. De plus, ces opérations ne ressemblent généralement pas à "l'envoi de message" et "la réception de message", mais ressemblent plutôt à des opérations de niveau supérieur comme des appels à des fonctions utilisateur.

La programmation distribuée en Julia repose sur deux primitives : *références distantes* et *appels distants*. Une référence distante est un objet qui peut être utilisé par n'importe quel processus pour faire référence à un objet stocké sur un processus particulier. Un appel distant est une demande d'un processus pour appeler une certaine fonction avec certains arguments sur un autre processus (éventuellement le même).

Les références distantes se présentent sous deux formes : [`Future`](@ref Distributed.Future) et [`RemoteChannel`](@ref).

Un appel distant renvoie un [`Future`](@ref Distributed.Future) à son résultat. Les appels distants retournent immédiatement ; le processus qui a effectué l'appel passe à son opération suivante pendant que l'appel distant se produit ailleurs. Vous pouvez attendre qu'un appel distant se termine en appelant [`wait`](@ref) sur le `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` retourné, et vous pouvez obtenir la valeur complète du résultat en utilisant [`fetch`](@ref).

D'autre part, [`RemoteChannel`](@ref) s sont réécrits. Par exemple, plusieurs processus peuvent coordonner leur traitement en faisant référence au même `Channel` distant.

Chaque processus a un identifiant associé. Le processus fournissant l'invite interactive de Julia a toujours un `id` égal à 1. Les processus utilisés par défaut pour les opérations parallèles sont appelés "travailleurs". Lorsqu'il n'y a qu'un seul processus, le processus 1 est considéré comme un travailleur. Sinon, les travailleurs sont considérés comme tous les processus autres que le processus 1. En conséquence, l'ajout de 2 processus ou plus est nécessaire pour tirer parti des méthodes de traitement parallèle comme [`pmap`](@ref). L'ajout d'un seul processus est bénéfique si vous souhaitez simplement faire d'autres choses dans le processus principal pendant qu'un long calcul s'exécute sur le travailleur.

Commençons par cela. Démarrer avec `julia -p n` fournit `n` processus de travail sur la machine locale. En général, il est logique que `n` soit égal au nombre de threads CPU (cœurs logiques) sur la machine. Notez que l'argument `-p` charge implicitement le module [`Distributed`](@ref man-distributed).

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

Le premier argument de [`remotecall`](@ref) est la fonction à appeler. La plupart de la programmation parallèle en Julia ne fait pas référence à des processus spécifiques ou au nombre de processus disponibles, mais `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` est considéré comme une interface de bas niveau offrant un contrôle plus précis. Le deuxième argument de `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` est l'`id` du processus qui effectuera le travail, et les arguments restants seront passés à la fonction appelée.

Comme vous pouvez le voir, dans la première ligne, nous avons demandé au processus 2 de construire une matrice aléatoire 2 par 2, et dans la deuxième ligne, nous lui avons demandé d'y ajouter 1. Le résultat des deux calculs est disponible dans les deux futurs, `r` et `s`. La macro [`@spawnat`](@ref) évalue l'expression dans le deuxième argument sur le processus spécifié par le premier argument.

Occasionnellement, vous pourriez vouloir une valeur calculée à distance immédiatement. Cela se produit généralement lorsque vous lisez à partir d'un objet distant pour obtenir des données nécessaires à la prochaine opération locale. La fonction [`remotecall_fetch`](@ref) existe à cet effet. Elle est équivalente à `fetch(remotecall(...))` mais est plus efficace.

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

Cela récupère le tableau sur le travailleur 2 et renvoie la première valeur. Notez que `fetch` ne déplace aucune donnée dans ce cas, car il est exécuté sur le travailleur qui possède le tableau. On peut également écrire :

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

Rappelez-vous que [`getindex(r,1,1)`](@ref) est [equivalent](@ref man-array-indexing) à `r[1,1]`, donc cet appel récupère le premier élément du futur `r`.

Pour faciliter les choses, le symbole `:any` peut être passé à [`@spawnat`](@ref), qui choisit où effectuer l'opération pour vous :

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

Notez que nous avons utilisé `1 .+ fetch(r)` au lieu de `1 .+ r`. Cela est dû au fait que nous ne savons pas où le code sera exécuté, donc en général un [`fetch`](@ref) pourrait être nécessaire pour déplacer `r` vers le processus effectuant l'addition. Dans ce cas, [`@spawnat`](@ref) est suffisamment intelligent pour effectuer le calcul sur le processus qui possède `r`, donc le `4d61726b646f776e2e436f64652822222c202266657463682229_40726566` sera une opération nulle (aucun travail n'est effectué).

(Il est à noter que [`@spawnat`](@ref) n'est pas intégré mais défini en Julia comme un [macro](@ref man-macros). Il est possible de définir vos propres constructions de ce type.)

Une chose importante à retenir est qu'une fois récupéré, un [`Future`](@ref Distributed.Future) mettra en cache sa valeur localement. D'autres appels [`fetch`](@ref) n'entraînent pas de saut réseau. Une fois que toutes les références à `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` ont été récupérées, la valeur stockée à distance est supprimée.

[`@async`](@ref) est similaire à [`@spawnat`](@ref), mais exécute uniquement des tâches sur le processus local. Nous l'utilisons pour créer une tâche "alimenteuse" pour chaque processus. Chaque tâche prend l'index suivant qui doit être calculé, puis attend que son processus se termine, puis répète jusqu'à ce que nous manquions d'indices. Notez que les tâches alimentatrices ne commencent pas à s'exécuter tant que la tâche principale n'atteint pas la fin du bloc [`@sync`](@ref), à quel point elle abandonne le contrôle et attend que toutes les tâches locales soient terminées avant de revenir de la fonction. En ce qui concerne v0.7 et au-delà, les tâches alimentatrices peuvent partager l'état via `nextidx` car elles s'exécutent toutes sur le même processus. Même si les `Tasks` sont planifiées de manière coopérative, un verrouillage peut encore être nécessaire dans certains contextes, comme dans [asynchronous I/O](@ref faq-async-io). Cela signifie que les changements de contexte ne se produisent qu'à des points bien définis : dans ce cas, lorsque [`remotecall_fetch`](@ref) est appelé. C'est l'état actuel de l'implémentation et il peut changer pour les futures versions de Julia, car il est destiné à rendre possible l'exécution de jusqu'à N `Tasks` sur M `Process`, alias [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models). Ensuite, un modèle d'acquisition/libération de verrou pour `nextidx` sera nécessaire, car il n'est pas sûr de laisser plusieurs processus lire-écrire une ressource en même temps.

## [Code Availability and Loading Packages](@id code-availability)

Votre code doit être disponible sur tout processus qui l'exécute. Par exemple, tapez ce qui suit dans l'invite Julia :

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

Le processus 1 connaissait la fonction `rand2`, mais le processus 2 ne la connaissait pas.

La plupart du temps, vous chargerez du code à partir de fichiers ou de packages, et vous avez une flexibilité considérable pour contrôler quels processus chargent le code. Considérez un fichier, `DummyModule.jl`, contenant le code suivant :

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

Pour faire référence à `MyType` dans tous les processus, `DummyModule.jl` doit être chargé sur chaque processus. Appeler `include("DummyModule.jl")` ne le charge que sur un seul processus. Pour le charger sur chaque processus, utilisez le macro [`@everywhere`](@ref) (en démarrant Julia avec `julia -p 2`) :

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

Comme d'habitude, cela ne met pas `DummyModule` dans le champ d'application de l'un des processus, ce qui nécessite [`using`](@ref) ou [`import`](@ref). De plus, lorsque `DummyModule` est mis dans le champ d'application d'un processus, il ne l'est pas dans les autres :

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

Cependant, il est toujours possible, par exemple, d'envoyer un `MyType` à un processus qui a chargé `DummyModule`, même s'il n'est pas dans le champ d'application :

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

Un fichier peut également être préchargé sur plusieurs processus au démarrage avec le drapeau `-L`, et un script de pilote peut être utilisé pour piloter le calcul :

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

Le processus Julia exécutant le script du pilote dans l'exemple ci-dessus a un `id` égal à 1, tout comme un processus fournissant un invite interactive.

Enfin, si `DummyModule.jl` n'est pas un fichier autonome mais un package, alors `using DummyModule` va *charger* `DummyModule.jl` sur tous les processus, mais ne l'apportera dans le scope que sur le processus où [`using`](@ref) a été appelé.

## Starting and managing worker processes

L'installation de base de Julia prend en charge deux types de clusters :

  * Un cluster local spécifié avec l'option `-p` comme indiqué ci-dessus.
  * Un cluster s'étendant sur des machines en utilisant l'option `--machine-file`. Cela utilise une connexion `ssh` sans mot de passe pour démarrer des processus de travail Julia (à partir du même chemin que l'hôte actuel) sur les machines spécifiées. Chaque définition de machine prend la forme `[count*][user@]host[:port] [bind_addr[:port]]`. `user` par défaut est l'utilisateur actuel, `port` est le port ssh standard. `count` est le nombre de travailleurs à lancer sur le nœud, et par défaut, il est de 1. L'option `bind-to bind_addr[:port]` spécifie l'adresse IP et le port que les autres travailleurs doivent utiliser pour se connecter à ce travailleur.

!!! note
    Bien que Julia s'efforce généralement de maintenir la compatibilité ascendante, la distribution de code aux processus de travail repose sur [`Serialization.serialize`](@ref). Comme indiqué dans la documentation correspondante, cela ne peut pas être garanti de fonctionner à travers différentes versions de Julia, il est donc conseillé que tous les travailleurs sur toutes les machines utilisent la même version.


Les fonctions [`addprocs`](@ref), [`rmprocs`](@ref), [`workers`](@ref), et d'autres sont disponibles comme un moyen programmatique d'ajouter, de supprimer et de interroger les processus dans un cluster.

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

Le module [`Distributed`](@ref man-distributed) doit être explicitement chargé sur le processus maître avant d'invoquer [`addprocs`](@ref). Il est automatiquement mis à disposition sur les processus de travail.

!!! note
    Notez que les travailleurs ne exécutent pas de script de démarrage `~/.julia/config/startup.jl`, ni ne synchronisent leur état global (comme les options de ligne de commande, les variables globales, les définitions de nouvelles méthodes et les modules chargés) avec les autres processus en cours d'exécution. Vous pouvez utiliser `addprocs(exeflags="--project")` pour initialiser un travailleur avec un environnement particulier, puis `@everywhere using <modulename>` ou `@everywhere include("file.jl")`.


D'autres types de clusters peuvent être pris en charge en écrivant votre propre `ClusterManager`, comme décrit ci-dessous dans la section [ClusterManagers](@ref).

## Data Movement

L'envoi de messages et le transfert de données constituent la majeure partie de la surcharge dans un programme distribué. Réduire le nombre de messages et la quantité de données envoyées est essentiel pour atteindre des performances et une évolutivité optimales. Dans ce but, il est important de comprendre le mouvement des données effectué par les différents constructs de programmation distribuée de Julia.

[`fetch`](@ref) peut être considéré comme une opération de mouvement de données explicite, car il demande directement qu'un objet soit déplacé vers la machine locale. [`@spawnat`](@ref) (et quelques constructions connexes) déplace également des données, mais ce n'est pas aussi évident, donc on peut l'appeler une opération de mouvement de données implicite. Considérez ces deux approches pour construire et élever au carré une matrice aléatoire :

Méthode 1 :

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

Méthode 2 :

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

La différence semble triviale, mais en fait elle est assez significative en raison du comportement de [`@spawnat`](@ref). Dans la première méthode, une matrice aléatoire est construite localement, puis envoyée à un autre processus où elle est mise au carré. Dans la deuxième méthode, une matrice aléatoire est à la fois construite et mise au carré sur un autre processus. Par conséquent, la deuxième méthode envoie beaucoup moins de données que la première.

Dans cet exemple simplifié, les deux méthodes sont faciles à distinguer et à choisir. Cependant, dans un programme réel, la conception du mouvement des données peut nécessiter plus de réflexion et probablement quelques mesures. Par exemple, si le premier processus a besoin de la matrice `A`, alors la première méthode pourrait être meilleure. Ou, si le calcul de `A` est coûteux et que seul le processus actuel l'a, alors le déplacer vers un autre processus pourrait être inévitable. Ou, si le processus actuel a très peu à faire entre le [`@spawnat`](@ref) et `fetch(Bref)`, il pourrait être préférable d'éliminer complètement le parallélisme. Ou imaginez que `rand(1000,1000)` soit remplacé par une opération plus coûteuse. Dans ce cas, il pourrait être judicieux d'ajouter une autre instruction `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566` juste pour cette étape.

## Global variables

Les expressions exécutées à distance via [`@spawnat`](@ref), ou les fermetures spécifiées pour une exécution à distance en utilisant [`remotecall`](@ref) peuvent faire référence à des variables globales. Les liaisons globales sous le module `Main` sont traitées un peu différemment par rapport aux liaisons globales dans d'autres modules. Considérez le code suivant :

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

Dans ce cas, [`sum`](@ref) DOIT être défini dans le processus distant. Notez que `A` est une variable globale définie dans l'espace de travail local. Le travailleur 2 n'a pas de variable appelée `A` sous `Main`. L'acte d'expédier la fermeture `()->sum(A)` au travailleur 2 entraîne la définition de `Main.A` sur 2. `Main.A` continue d'exister sur le travailleur 2 même après que l'appel [`remotecall_fetch`](@ref) retourne. Les appels distants avec des références globales intégrées (sous le module `Main` uniquement) gèrent les globals comme suit :

  * De nouveaux liens globaux sont créés sur les travailleurs de destination s'ils sont référencés dans le cadre d'un appel à distance.
  * Les constantes globales sont déclarées comme constantes sur les nœuds distants également.
  * Les globals sont renvoyés à un travailleur de destination uniquement dans le contexte d'un appel à distance, et seulement si leur valeur a changé. De plus, le cluster ne synchronise pas les liaisons globales entre les nœuds. Par exemple :

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    L'exécution du snippet ci-dessus entraîne que `Main.A` sur le worker 2 a une valeur différente de `Main.A` sur le worker 3, tandis que la valeur de `Main.A` sur le nœud 1 est définie sur `nothing`.

Comme vous l'avez peut-être réalisé, bien que la mémoire associée aux variables globales puisse être collectée lorsqu'elles sont réaffectées sur le maître, aucune action de ce type n'est effectuée sur les travailleurs car les liaisons continuent d'être valides. [`clear!`](@ref) peut être utilisé pour réaffecter manuellement des variables globales spécifiques sur des nœuds distants à `nothing` une fois qu'elles ne sont plus nécessaires. Cela libérera toute mémoire qui leur est associée dans le cadre d'un cycle de collecte des ordures régulier.

Ainsi, les programmes doivent être prudents lorsqu'ils font référence à des variables globales dans des appels distants. En fait, il est préférable de les éviter complètement si possible. Si vous devez faire référence à des variables globales, envisagez d'utiliser des blocs `let` pour localiser les variables globales.

Pour exemple :

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

Comme on peut le voir, la variable globale `A` est définie sur le travailleur 2, mais `B` est capturée en tant que variable locale et donc un lien pour `B` n'existe pas sur le travailleur 2.

## Parallel Map and Loops

Heureusement, de nombreux calculs parallèles utiles ne nécessitent pas de déplacement de données. Un exemple courant est une simulation de Monte Carlo, où plusieurs processus peuvent gérer des essais de simulation indépendants simultanément. Nous pouvons utiliser [`@spawnat`](@ref) pour lancer des pièces sur deux processus. Tout d'abord, écrivez la fonction suivante dans `count_heads.jl` :

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

La fonction `count_heads` additionne simplement `n` bits aléatoires. Voici comment nous pouvons effectuer quelques essais sur deux machines et additionner les résultats :

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

Cet exemple démontre un modèle de programmation parallèle puissant et souvent utilisé. De nombreuses itérations s'exécutent indépendamment sur plusieurs processus, puis leurs résultats sont combinés à l'aide d'une fonction. Le processus de combinaison est appelé *réduction*, car il réduit généralement le rang du tenseur : un vecteur de nombres est réduit à un seul nombre, ou une matrice est réduite à une seule ligne ou colonne, etc. Dans le code, cela ressemble généralement au modèle `x = f(x,v[i])`, où `x` est l'accumulateur, `f` est la fonction de réduction, et les `v[i]` sont les éléments à réduire. Il est souhaitable que `f` soit associative, de sorte que l'ordre dans lequel les opérations sont effectuées n'ait pas d'importance.

Remarquez que notre utilisation de ce modèle avec `count_heads` peut être généralisée. Nous avons utilisé deux déclarations explicites [`@spawnat`](@ref), ce qui limite le parallélisme à deux processus. Pour exécuter sur n'importe quel nombre de processus, nous pouvons utiliser une *boucle for parallèle*, fonctionnant en mémoire distribuée, qui peut être écrite en Julia en utilisant [`@distributed`](@ref) comme ceci :

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

Cette construction implémente le modèle d'attribution d'itérations à plusieurs processus et de combinaison de celles-ci avec une réduction spécifiée (dans ce cas, `(+)`). Le résultat de chaque itération est pris comme la valeur de la dernière expression à l'intérieur de la boucle. L'ensemble de l'expression de boucle parallèle elle-même évalue à la réponse finale.

Notez que bien que les boucles for parallèles ressemblent à des boucles for sérielles, leur comportement est radicalement différent. En particulier, les itérations ne se déroulent pas dans un ordre spécifié, et les écritures dans des variables ou des tableaux ne seront pas visibles globalement puisque les itérations s'exécutent sur différents processus. Toutes les variables utilisées à l'intérieur de la boucle parallèle seront copiées et diffusées à chaque processus.

Par exemple, le code suivant ne fonctionnera pas comme prévu :

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

Ce code n'initialisera pas tout `a`, car chaque processus aura une copie séparée de celui-ci. Les boucles parallèles comme celles-ci doivent être évitées. Heureusement, [Shared Arrays](@ref man-shared-arrays) peut être utilisé pour contourner cette limitation :

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

Utiliser des variables "externes" dans des boucles parallèles est tout à fait raisonnable si les variables sont en lecture seule :

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

Ici, chaque itération applique `f` à un échantillon choisi au hasard d'un vecteur `a` partagé par tous les processus.

Comme vous pouvez le voir, l'opérateur de réduction peut être omis s'il n'est pas nécessaire. Dans ce cas, la boucle s'exécute de manière asynchrone, c'est-à-dire qu'elle génère des tâches indépendantes sur tous les travailleurs disponibles et renvoie immédiatement un tableau de [`Future`](@ref Distributed.Future) sans attendre la fin. L'appelant peut attendre les complétions de `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` à un moment ultérieur en appelant [`fetch`](@ref) sur celles-ci, ou attendre la fin à la fin de la boucle en le préfixant avec [`@sync`](@ref), comme `@sync @distributed for`.

Dans certains cas, aucun opérateur de réduction n'est nécessaire, et nous souhaitons simplement appliquer une fonction à tous les entiers dans une certaine plage (ou, plus généralement, à tous les éléments d'une collection). C'est une autre opération utile appelée *carte parallèle*, implémentée en Julia sous la forme de la fonction [`pmap`](@ref). Par exemple, nous pourrions calculer les valeurs singulières de plusieurs grandes matrices aléatoires en parallèle comme suit :

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

Le [`pmap`](@ref) de Julia est conçu pour les cas où chaque appel de fonction effectue une grande quantité de travail. En revanche, `@distributed for` peut gérer des situations où chaque itération est minuscule, peut-être simplement la somme de deux nombres. Seuls les processus de travail sont utilisés par `4d61726b646f776e2e436f64652822222c2022706d61702229_40726566` et `@distributed for` pour le calcul parallèle. Dans le cas de `@distributed for`, la réduction finale est effectuée sur le processus appelant.

## Remote References and AbstractChannels

Les références distantes font toujours référence à une implémentation d'un `AbstractChannel`.

Une implémentation concrète d'un `AbstractChannel` (comme `Channel`), doit implémenter [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) et [`wait`](@ref). L'objet distant référencé par un [`Future`](@ref Distributed.Future) est stocké dans un `Channel{Any}(1)`, c'est-à-dire un `Channel` de taille 1 capable de contenir des objets de type `Any`.

[`RemoteChannel`](@ref), qui est réécrivable, peut pointer vers tout type et taille de canaux, ou toute autre implémentation d'un `AbstractChannel`.

Le constructeur `RemoteChannel(f::Function, pid)()` nous permet de construire des références à des canaux contenant plus d'une valeur d'un type spécifique. `f` est une fonction exécutée sur `pid` et elle doit retourner un `AbstractChannel`.

Par exemple, `RemoteChannel(()->Channel{Int}(10), pid)`, renverra une référence à un canal de type `Int` et de taille 10. Le canal existe sur le travailleur `pid`.

Les méthodes [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) et [`wait`](@ref) sur un [`RemoteChannel`](@ref) sont proxy sur le magasin de données dans le processus distant.

[`RemoteChannel`](@ref) peut donc être utilisé pour faire référence aux objets `AbstractChannel` implémentés par l'utilisateur. Un exemple simple de cela est le `DictChannel` suivant qui utilise un dictionnaire comme son stockage distant :

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * Un [`Channel`](@ref) est local à un processus. Le travailleur 2 ne peut pas se référer directement à un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` sur le travailleur 3 et vice-versa. Un [`RemoteChannel`](@ref), cependant, peut mettre et prendre des valeurs entre les travailleurs.
  * Un [`RemoteChannel`](@ref) peut être considéré comme un *handle* pour un [`Channel`](@ref).
  * L'identifiant de processus, `pid`, associé à un [`RemoteChannel`](@ref) identifie le processus où le magasin de sauvegarde, c'est-à-dire le [`Channel`](@ref) existe.
  * Tout processus faisant référence à un [`RemoteChannel`](@ref) peut mettre et prendre des éléments du canal. Les données sont automatiquement envoyées à (ou récupérées depuis) le processus auquel un `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` est associé.
  * La sérialisation d'un [`Channel`](@ref) sérialise également toutes les données présentes dans le canal. La désérialisation en fait donc effectivement une copie de l'objet original.
  * D'autre part, la sérialisation d'un [`RemoteChannel`](@ref) implique uniquement la sérialisation d'un identifiant qui identifie l'emplacement et l'instance de [`Channel`](@ref) référencé par le handle. Un objet `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` désérialisé (sur n'importe quel worker) pointe donc également vers le même magasin de données que l'original.

L'exemple de canaux ci-dessus peut être modifié pour la communication interprocessus, comme indiqué ci-dessous.

Nous démarrons 4 travailleurs pour traiter un seul canal distant `jobs`. Les travaux, identifiés par un id (`job_id`), sont écrits dans le canal. Chaque tâche exécutée à distance dans cette simulation lit un `job_id`, attend un temps aléatoire et écrit un tuple de `job_id`, temps pris et son propre `pid` dans le canal des résultats. Enfin, tous les `results` sont imprimés dans le processus maître.

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

Les objets référencés par des références distantes ne peuvent être libérés que lorsque *toutes* les références détenues dans le cluster sont supprimées.

Le nœud où la valeur est stockée garde une trace de quels travailleurs ont une référence à celle-ci. Chaque fois qu'un [`RemoteChannel`](@ref) ou un [`Future`](@ref Distributed.Future) (non récupéré) est sérialisé vers un travailleur, le nœud pointé par la référence est notifié. Et chaque fois qu'un `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` ou un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` (non récupéré) est collecté comme déchet localement, le nœud possédant la valeur est à nouveau notifié. Cela est implémenté dans un sérialiseur interne conscient du cluster. Les références distantes ne sont valides que dans le contexte d'un cluster en cours d'exécution. La sérialisation et la désérialisation de références vers et depuis des objets `IO` réguliers ne sont pas prises en charge.

Les notifications se font par l'envoi de messages de "suivi" – un message "ajouter référence" lorsqu'une référence est sérialisée vers un autre processus et un message "supprimer référence" lorsqu'une référence est collectée localement par le ramasse-miettes.

Puisque [`Future`](@ref Distributed.Future) sont en écriture unique et mis en cache localement, l'acte de [`fetch`](@ref) un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` met également à jour les informations de suivi de référence sur le nœud possédant la valeur.

Le nœud qui possède la valeur la libère une fois que toutes les références à celle-ci sont supprimées.

Avec [`Future`](@ref Distributed.Future), la sérialisation d'un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` déjà récupéré vers un nœud différent envoie également la valeur, car le magasin distant d'origine peut avoir collecté la valeur d'ici là.

Il est important de noter que *quand* un objet est collecté par le ramasse-miettes localement dépend de la taille de l'objet et de la pression mémoire actuelle dans le système.

En cas de références distantes, la taille de l'objet de référence local est assez petite, tandis que la valeur stockée sur le nœud distant peut être assez grande. Étant donné que l'objet local peut ne pas être collecté immédiatement, il est bon de pratiquer d'appeler explicitement [`finalize`](@ref) sur les instances locales d'un [`RemoteChannel`](@ref), ou sur des [`Future`](@ref Distributed.Future) non récupérées. Étant donné que l'appel de [`fetch`](@ref) sur un `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` supprime également sa référence du magasin distant, cela n'est pas nécessaire sur les `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` récupérés. L'appel explicite de `4d61726b646f776e2e436f64652822222c202266696e616c697a652229_40726566` entraîne l'envoi immédiat d'un message au nœud distant pour procéder à la suppression de sa référence à la valeur.

Une fois finalisée, une référence devient invalide et ne peut plus être utilisée dans d'autres appels.

## Local invocations

Les données doivent nécessairement être copiées sur le nœud distant pour exécution. C'est le cas à la fois pour les appels distants et lorsque les données sont stockées dans un [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future) sur un nœud différent. Comme prévu, cela entraîne une copie des objets sérialisés sur le nœud distant. Cependant, lorsque le nœud de destination est le nœud local, c'est-à-dire que l'identifiant du processus appelant est le même que l'identifiant du nœud distant, il est exécuté comme un appel local. Il est généralement (mais pas toujours) exécuté dans une tâche différente - mais il n'y a pas de sérialisation/désérialisation des données. Par conséquent, l'appel fait référence aux mêmes instances d'objet que celles passées - aucune copie n'est créée. Ce comportement est mis en évidence ci-dessous :

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

Comme on peut le voir, [`put!`](@ref) sur un [`RemoteChannel`](@ref) appartenant localement avec le même objet `v` modifié entre les appels résulte en la même instance d'objet unique stockée. Contrairement à des copies de `v` étant créées lorsque le nœud possédant `rc` est un nœud différent.

Il convient de noter que cela n'est généralement pas un problème. C'est quelque chose à prendre en compte uniquement si l'objet est à la fois stocké localement et modifié après l'appel. Dans de tels cas, il peut être approprié de stocker un `deepcopy` de l'objet.

Ceci est également vrai pour les appels distants sur le nœud local comme le montre l'exemple suivant :

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

Comme on peut le voir une fois de plus, un appel distant sur le nœud local se comporte exactement comme une invocation directe. L'appel modifie les objets locaux passés en arguments. Dans l'invocation distante, il opère sur une copie des arguments.

Pour répéter, en général, ce n'est pas un problème. Si le nœud local est également utilisé comme nœud de calcul, et que les arguments utilisés après l'appel, ce comportement doit être pris en compte et, si nécessaire, des copies profondes des arguments doivent être transmises à l'appel invoqué sur le nœud local. Les appels sur des nœuds distants fonctionneront toujours sur des copies des arguments.

## [Shared Arrays](@id man-shared-arrays)

Les tableaux partagés utilisent la mémoire partagée du système pour mapper le même tableau à travers plusieurs processus. Un [`SharedArray`](@ref) est un bon choix lorsque vous souhaitez avoir une grande quantité de données accessibles conjointement à deux processus ou plus sur la même machine. Le support des tableaux partagés est disponible via le module `SharedArrays`, qui doit être explicitement chargé sur tous les travailleurs participants.

Une structure de données complémentaire est fournie par le package externe [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) sous la forme d'un `DArray`. Bien qu'il existe certaines similitudes avec un [`SharedArray`](@ref), le comportement d'un [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl) est assez différent. Dans un `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`, chaque processus "participant" a accès à l'ensemble du tableau ; en revanche, dans un `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c`, chaque processus a un accès local à juste un morceau des données, et aucun des deux processus ne partage le même morceau.

[`SharedArray`](@ref) l'indexation (attribution et accès aux valeurs) fonctionne exactement comme avec des tableaux réguliers, et est efficace car la mémoire sous-jacente est disponible pour le processus local. Par conséquent, la plupart des algorithmes fonctionnent naturellement sur `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`, bien que dans un mode à processus unique. Dans les cas où un algorithme insiste sur une entrée [`Array`](@ref), le tableau sous-jacent peut être récupéré d'un `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` en appelant [`sdata`](@ref). Pour d'autres types `AbstractArray`, `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` renvoie simplement l'objet lui-même, il est donc sûr d'utiliser `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` sur tout objet de type `Array`.

Le constructeur pour un tableau partagé est de la forme :

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

qui crée un tableau partagé `N`-dimensionnel de type `T` de bits et de taille `dims` à travers les processus spécifiés par `pids`. Contrairement aux tableaux distribués, un tableau partagé n'est accessible que par les travailleurs participants spécifiés par l'argument nommé `pids` (et le processus créateur également, s'il est sur le même hôte). Notez que seuls les éléments qui sont [`isbits`](@ref) sont pris en charge dans un SharedArray.

Si une fonction `init`, de signature `initfn(S::SharedArray)`, est spécifiée, elle est appelée sur tous les travailleurs participants. Vous pouvez spécifier que chaque travailleur exécute la fonction `init` sur une portion distincte du tableau, parallélisant ainsi l'initialisation.

Voici un bref exemple :

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref) fournit des plages d'indices unidimensionnelles disjointes, et il est parfois pratique de diviser les tâches entre les processus. Vous pouvez, bien sûr, diviser le travail comme vous le souhaitez :

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

Puisque tous les processus ont accès aux données sous-jacentes, vous devez faire attention à ne pas créer de conflits. Par exemple :

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

cela entraînerait un comportement indéfini. Parce que chaque processus remplit le *total* du tableau avec son propre `pid`, quel que soit le processus qui s'exécute en dernier (pour un élément particulier de `S`), son `pid` sera conservé.

En tant qu'exemple plus étendu et complexe, envisagez d'exécuter le "noyau" suivant en parallèle :

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

Dans ce cas, si nous essayons de diviser le travail en utilisant un index unidimensionnel, nous risquons de rencontrer des problèmes : si `q[i,j,t]` est proche de la fin du bloc attribué à un travailleur et `q[i,j,t+1]` est proche du début du bloc attribué à un autre, il est très probable que `q[i,j,t]` ne soit pas prêt au moment où il est nécessaire pour le calcul de `q[i,j,t+1]`. Dans de tels cas, il est préférable de diviser manuellement le tableau. Divisons le long de la deuxième dimension. Définissez une fonction qui renvoie les indices `(irange, jrange)` attribués à ce travailleur :

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

Ensuite, définissez le noyau :

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

Nous définissons également un wrapper de commodité pour une implémentation de `SharedArray`.

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

Maintenant, comparons trois versions différentes, dont une qui s'exécute dans un seul processus :

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

un qui utilise [`@distributed`](@ref) :

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

et un qui délègue par morceaux :

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

Si nous créons des `SharedArray`s et chronométrons ces fonctions, nous obtenons les résultats suivants (avec `julia -p 4`) :

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

Exécutez les fonctions une fois pour les compiler en JIT et [`@time`](@ref) les lors de la deuxième exécution :

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

Le plus grand avantage de `advection_shared!` est qu'il minimise le trafic entre les travailleurs, permettant à chacun de calculer pendant une période prolongée sur la partie assignée.

### Shared Arrays and Distributed Garbage Collection

Comme les références distantes, les tableaux partagés dépendent également de la collecte des ordures sur le nœud créateur pour libérer les références de tous les travailleurs participants. Le code qui crée de nombreux objets de tableau partagé à courte durée de vie bénéficierait d'une finalisation explicite de ces objets dès que possible. Cela permet de libérer plus tôt à la fois la mémoire et les descripteurs de fichiers mappant le segment partagé.

## ClusterManagers

Le lancement, la gestion et le mise en réseau des processus Julia dans un cluster logique se font via des gestionnaires de cluster. Un `ClusterManager` est responsable de

  * lancement de processus de travail dans un environnement de cluster
  * gérer les événements pendant la durée de vie de chaque travailleur
  * optionnellement, fournissant le transport de données

Un cluster Julia a les caractéristiques suivantes :

  * Le processus Julia initial, également appelé `maître`, est spécial et a un `id` de 1.
  * Seul le processus `master` peut ajouter ou supprimer des processus de travail.
  * Tous les processus peuvent communiquer directement entre eux.

Les connexions entre les travailleurs (en utilisant le transport TCP/IP intégré) sont établies de la manière suivante :

  * [`addprocs`](@ref) est appelé sur le processus maître avec un objet `ClusterManager`.
  * [`addprocs`](@ref) appelle la méthode appropriée [`launch`](@ref) qui génère le nombre requis de processus de travail sur les machines appropriées.
  * Chaque travailleur commence à écouter sur un port libre et écrit ses informations d'hôte et de port dans [`stdout`](@ref).
  * Le gestionnaire de cluster capture le [`stdout`](@ref) de chaque travailleur et le rend disponible au processus maître.
  * Le processus maître analyse ces informations et établit des connexions TCP/IP avec chaque travailleur.
  * Chaque travailleur est également informé des autres travailleurs dans le cluster.
  * Chaque travailleur se connecte à tous les travailleurs dont l'`id` est inférieur à son propre `id`.
  * De cette manière, un réseau maillé est établi, dans lequel chaque travailleur est directement connecté à chaque autre travailleur.

Bien que la couche de transport par défaut utilise [`TCPSocket`](@ref) en clair, il est possible pour un cluster Julia de fournir son propre transport.

Julia fournit deux gestionnaires de clusters intégrés :

  * `LocalManager`, utilisé lorsque [`addprocs()`](@ref) ou [`addprocs(np::Integer)`](@ref) sont appelés
  * `SSHManager`, utilisé lorsque [`addprocs(hostnames::Array)`](@ref) est appelé avec une liste de noms d'hôtes.

`LocalManager` est utilisé pour lancer des travailleurs supplémentaires sur le même hôte, tirant ainsi parti du matériel multi-cœur et multi-processeur.

Ainsi, un gestionnaire de cluster minimal devrait :

  * être un sous-type de l'abstrait `ClusterManager`
  * implémenter [`launch`](@ref), une méthode responsable du lancement de nouveaux travailleurs
  * implémenter [`manage`](@ref), qui est appelé à divers événements au cours de la vie d'un travailleur (par exemple, l'envoi d'un signal d'interruption)

[`addprocs(manager::FooManager)`](@ref addprocs) nécessite que `FooManager` implémente :

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

En tant qu'exemple, voyons comment le `LocalManager`, le gestionnaire responsable du démarrage des travailleurs sur le même hôte, est implémenté :

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

La méthode [`launch`](@ref) prend les arguments suivants :

  * `manager::ClusterManager`: le gestionnaire de cluster qui est appelé avec [`addprocs`](@ref)
  * `params::Dict`: tous les arguments de mot-clé passés à [`addprocs`](@ref)
  * `launched::Array`: le tableau auquel ajouter un ou plusieurs objets `WorkerConfig`
  * `c::Condition` : la variable de condition à notifier lorsque des travailleurs sont lancés.

La méthode [`launch`](@ref) est appelée de manière asynchrone dans une tâche séparée. La terminaison de cette tâche signale que tous les travailleurs demandés ont été lancés. Par conséquent, la fonction `4d61726b646f776e2e436f64652822222c20226c61756e63682229_40726566` DOIT se terminer dès que tous les travailleurs demandés ont été lancés.

Les travailleurs nouvellement lancés sont connectés les uns aux autres et au processus maître de manière tous à tous. La spécification de l'argument de ligne de commande `--worker[=<cookie>]` entraîne l'initialisation des processus lancés en tant que travailleurs et l'établissement de connexions via des sockets TCP/IP.

Tous les travailleurs dans un cluster partagent le même [cookie](@ref man-cluster-cookie) que le maître. Lorsque le cookie n'est pas spécifié, c'est-à-dire avec l'option `--worker`, le travailleur essaie de le lire à partir de son entrée standard. `LocalManager` et `SSHManager` transmettent tous deux le cookie aux travailleurs nouvellement lancés via leurs entrées standard.

Par défaut, un worker écoutera sur un port libre à l'adresse retournée par un appel à [`getipaddr()`](@ref). Une adresse spécifique sur laquelle écouter peut être spécifiée par l'argument optionnel `--bind-to bind_addr[:port]`. Cela est utile pour les hôtes multi-homés.

En tant qu'exemple d'un transport non-TCP/IP, une implémentation peut choisir d'utiliser MPI, auquel cas `--worker` ne doit PAS être spécifié. Au lieu de cela, les travailleurs nouvellement lancés doivent appeler `init_worker(cookie)` avant d'utiliser l'un des constructs parallèles.

Pour chaque travailleur lancé, la méthode [`launch`](@ref) doit ajouter un objet `WorkerConfig` (avec les champs appropriés initialisés) à `launched`

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

La plupart des champs dans `WorkerConfig` sont utilisés par les gestionnaires intégrés. Les gestionnaires de cluster personnalisés spécifieraient généralement uniquement `io` ou `host` / `port` :

  * Si `io` est spécifié, il est utilisé pour lire les informations d'hôte/port. Un travailleur Julia imprime son adresse de liaison et son port au démarrage. Cela permet aux travailleurs Julia d'écouter sur n'importe quel port libre disponible au lieu d'exiger que les ports des travailleurs soient configurés manuellement.
  * Si `io` n'est pas spécifié, `host` et `port` sont utilisés pour se connecter.
  * `count`, `exename` et `exeflags` sont pertinents pour lancer des travailleurs supplémentaires à partir d'un travailleur. Par exemple, un gestionnaire de cluster peut lancer un seul travailleur par nœud et l'utiliser pour lancer des travailleurs supplémentaires.

      * `count` avec une valeur entière `n` lancera un total de `n` travailleurs.
      * `count` avec une valeur de `:auto` lancera autant de travailleurs que le nombre de threads CPU (cœurs logiques) sur cette machine.
      * `exename` est le nom de l'exécutable `julia`, y compris le chemin complet.
      * `exeflags` doit être défini sur les arguments de ligne de commande requis pour les nouveaux travailleurs.
  * `tunnel`, `bind_addr`, `sshflags` et `max_parallel` sont utilisés lorsqu'un tunnel ssh est nécessaire pour se connecter aux travailleurs depuis le processus maître.
  * `userdata` est fourni pour que les gestionnaires de clusters personnalisés puissent stocker leurs propres informations spécifiques aux travailleurs.

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)` est appelé à différents moments au cours de la vie du travailleur avec des valeurs `op` appropriées :

  * avec `:register`/`:deregister` lorsque un travailleur est ajouté / retiré du pool de travailleurs Julia.
  * avec `:interrupt` lorsque `interrupt(workers)` est appelé. Le `ClusterManager` doit signaler le travailleur approprié avec un signal d'interruption.
  * avec `:finalize` à des fins de nettoyage.

### Cluster Managers with Custom Transports

Remplacer les connexions de socket TCP/IP par défaut par une couche de transport personnalisée est un peu plus complexe. Chaque processus Julia a autant de tâches de communication que de travailleurs auxquels il est connecté. Par exemple, considérons un cluster Julia de 32 processus dans un réseau maillé tout-à-tous :

  * Chaque processus Julia a donc 31 tâches de communication.
  * Chaque tâche gère tous les messages entrants d'un seul travailleur à distance dans une boucle de traitement des messages.
  * La boucle de traitement des messages attend sur un objet `IO` (par exemple, un [`TCPSocket`](@ref) dans l'implémentation par défaut), lit un message entier, le traite et attend le suivant.
  * L'envoi de messages à un processus se fait directement depuis n'importe quelle tâche Julia – pas seulement les tâches de communication – encore une fois, via l'objet `IO` approprié.

Remplacer le transport par défaut nécessite que la nouvelle implémentation établisse des connexions avec des travailleurs distants et fournisse des objets `IO` appropriés sur lesquels les boucles de traitement des messages peuvent attendre. Les rappels spécifiques au gestionnaire à mettre en œuvre sont :

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

L'implémentation par défaut (qui utilise des sockets TCP/IP) est implémentée comme `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)`.

`connect` doit renvoyer une paire d'objets `IO`, l'un pour lire les données envoyées par le `pid` du travailleur, et l'autre pour écrire les données qui doivent être envoyées au `pid` du travailleur. Les gestionnaires de cluster personnalisés peuvent utiliser un `BufferStream` en mémoire comme tuyauterie pour faire passer les données entre le transport personnalisé, éventuellement non `IO`, et l'infrastructure parallèle intégrée de Julia.

Un `BufferStream` est un [`IOBuffer`](@ref) en mémoire qui se comporte comme un `IO` – c'est un flux qui peut être géré de manière asynchrone.

Le dossier `clustermanager/0mq` dans le [Examples repository](https://github.com/JuliaAttic/Examples) contient un exemple d'utilisation de ZeroMQ pour connecter des travailleurs Julia dans une topologie en étoile avec un courtier 0MQ au milieu. Remarque : Les processus Julia sont toujours tous *logiquement* connectés les uns aux autres – tout travailleur peut envoyer un message à tout autre travailleur directement sans avoir conscience que 0MQ est utilisé comme couche de transport.

Lors de l'utilisation de transports personnalisés :

  * Les travailleurs Julia ne doivent PAS être démarrés avec `--worker`. Démarrer avec `--worker` entraînera le fait que les nouveaux travailleurs lancés utiliseront par défaut l'implémentation de transport par socket TCP/IP.
  * Pour chaque connexion logique entrante avec un travailleur, `Base.process_messages(rd::IO, wr::IO)()` doit être appelé. Cela lance une nouvelle tâche qui gère la lecture et l'écriture de messages depuis/vers le travailleur représenté par les objets `IO`.
  * `init_worker(cookie, manager::FooManager)` *doit* être appelé dans le cadre de l'initialisation du processus de travail.
  * Le champ `connect_at::Any` dans `WorkerConfig` peut être défini par le gestionnaire de cluster lorsque [`launch`](@ref) est appelé. La valeur de ce champ est transmise dans tous les rappels [`connect`](@ref). En général, il contient des informations sur *comment se connecter* à un travailleur. Par exemple, le transport par socket TCP/IP utilise ce champ pour spécifier le tuple `(hôte, port)` auquel se connecter à un travailleur.

`kill(manager, pid, config)` est appelé pour retirer un travailleur du cluster. Dans le processus maître, les objets `IO` correspondants doivent être fermés par l'implémentation pour garantir un nettoyage approprié. L'implémentation par défaut exécute simplement un appel `exit()` sur le travailleur distant spécifié.

Le dossier Exemples `clustermanager/simple` est un exemple qui montre une implémentation simple utilisant des sockets de domaine UNIX pour la configuration du cluster.

### Network Requirements for LocalManager and SSHManager

Les clusters Julia sont conçus pour être exécutés dans des environnements déjà sécurisés sur des infrastructures telles que des ordinateurs portables locaux, des clusters départementaux ou même le cloud. Cette section couvre les exigences de sécurité réseau pour le `LocalManager` et le `SSHManager` intégrés :

  * Le processus maître n'écoute sur aucun port. Il se connecte uniquement aux travailleurs.
  * Chaque travailleur se lie à l'une des interfaces locales et écoute sur un numéro de port éphémère attribué par le système d'exploitation.
  * `LocalManager`, utilisé par `addprocs(N)`, lie par défaut uniquement à l'interface de boucle locale. Cela signifie que les travailleurs démarrés plus tard sur des hôtes distants (ou par quiconque ayant de mauvaises intentions) ne peuvent pas se connecter au cluster. Un `addprocs(4)` suivi d'un `addprocs(["remote_host"])` échouera. Certains utilisateurs peuvent avoir besoin de créer un cluster comprenant leur système local et quelques systèmes distants. Cela peut être fait en demandant explicitement à `LocalManager` de se lier à une interface réseau externe via l'argument clé `restrict` : `addprocs(4; restrict=false)`.
  * `SSHManager`, utilisé par `addprocs(list_of_remote_hosts)`, lance des travailleurs sur des hôtes distants via SSH. Par défaut, SSH est uniquement utilisé pour lancer des travailleurs Julia. Les connexions ultérieures entre le maître et les travailleurs, ainsi qu'entre les travailleurs, utilisent des sockets TCP/IP non chiffrés. Les hôtes distants doivent avoir l'authentification sans mot de passe activée. Des options ou des identifiants SSH supplémentaires peuvent être spécifiés via l'argument clé `sshflags`.
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)` est utile lorsque nous souhaitons utiliser des connexions SSH pour le maître-travailleur également. Un scénario typique pour cela est un ordinateur portable local exécutant le REPL Julia (c'est-à-dire, le maître) avec le reste du cluster dans le cloud, par exemple sur Amazon EC2. Dans ce cas, seul le port 22 doit être ouvert sur le cluster distant associé à un client SSH authentifié via une infrastructure à clé publique (PKI). Les informations d'identification d'authentification peuvent être fournies via `sshflags`, par exemple ```sshflags=`-i <keyfile>` ```.

    Dans une topologie tous-à-tous (par défaut), tous les travailleurs se connectent entre eux via des sockets TCP simples. La politique de sécurité sur les nœuds du cluster doit donc garantir une connectivité libre entre les travailleurs pour la plage de ports éphémères (varie selon le système d'exploitation).

    Sécuriser et chiffrer tout le trafic entre travailleurs (via SSH) ou chiffrer des messages individuels peut être réalisé via un `ClusterManager` personnalisé.
  * Si vous spécifiez `multiplex=true` comme option à [`addprocs`](@ref), le multiplexage SSH est utilisé pour créer un tunnel entre le maître et les travailleurs. Si vous avez configuré le multiplexage SSH vous-même et que la connexion a déjà été établie, le multiplexage SSH est utilisé indépendamment de l'option `multiplex`. Si le multiplexage est activé, le transfert est configuré en utilisant la connexion existante (option `-O forward` dans ssh). Cela est bénéfique si vos serveurs nécessitent une authentification par mot de passe ; vous pouvez éviter l'authentification dans Julia en vous connectant au serveur avant `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566`. Le socket de contrôle sera situé à `~/.ssh/julia-%r@%h:%p` pendant la session, sauf si la connexion de multiplexage existante est utilisée. Notez que la bande passante peut être limitée si vous créez plusieurs processus sur un nœud et activez le multiplexage, car dans ce cas, les processus partagent une seule connexion TCP de multiplexage.

### [Cluster Cookie](@id man-cluster-cookie)

Tous les processus dans un cluster partagent le même cookie qui, par défaut, est une chaîne générée aléatoirement sur le processus maître :

  * [`cluster_cookie()`](@ref) renvoie le cookie, tandis que `cluster_cookie(cookie)()` le définit et renvoie le nouveau cookie.
  * Toutes les connexions sont authentifiées des deux côtés pour garantir que seuls les travailleurs démarrés par le maître sont autorisés à se connecter les uns aux autres.
  * Le cookie peut être passé aux travailleurs au démarrage via l'argument `--worker=<cookie>`. Si l'argument `--worker` est spécifié sans le cookie, le travailleur essaie de lire le cookie à partir de son entrée standard ([`stdin`](@ref)). L'`stdin` est fermé immédiatement après que le cookie a été récupéré.
  * Les `ClusterManager`s peuvent récupérer le cookie sur le maître en appelant [`cluster_cookie()`](@ref). Les gestionnaires de clusters ne utilisant pas le transport TCP/IP par défaut (et donc ne spécifiant pas `--worker`) doivent appeler `init_worker(cookie, manager)` avec le même cookie que sur le maître.

Notez que les environnements nécessitant des niveaux de sécurité plus élevés peuvent mettre en œuvre cela via un `ClusterManager` personnalisé. Par exemple, les cookies peuvent être pré-partagés et donc non spécifiés comme un argument de démarrage.

## Specifying Network Topology (Experimental)

L'argument clé `topology` passé à [`addprocs`](@ref) est utilisé pour spécifier comment les travailleurs doivent être connectés les uns aux autres :

  * `:all_to_all`, la valeur par défaut : tous les travailleurs sont connectés les uns aux autres.
  * `:master_worker` : seul le processus pilote, c'est-à-dire `pid` 1, a des connexions avec les travailleurs.
  * `:custom`: la méthode `launch` du gestionnaire de cluster spécifie la topologie de connexion via les champs `ident` et `connect_idents` dans `WorkerConfig`. Un travailleur avec une identité `ident` fournie par le gestionnaire de cluster se connectera à tous les travailleurs spécifiés dans `connect_idents`.

L'argument clé `lazy=true|false` n'affecte que l'option `topology` `:all_to_all`. Si `true`, le cluster commence avec le maître connecté à tous les travailleurs. Des connexions spécifiques entre travailleurs sont établies lors de la première invocation distante entre deux travailleurs. Cela aide à réduire les ressources initiales allouées pour la communication intra-cluster. Les connexions sont configurées en fonction des exigences d'exécution d'un programme parallèle. La valeur par défaut pour `lazy` est `true`.

Actuellement, l'envoi d'un message entre des travailleurs non connectés entraîne une erreur. Ce comportement, tout comme la fonctionnalité et l'interface, doit être considéré comme expérimental et peut changer dans les futures versions.

## Noteworthy external packages

Outside of Julia parallelism there are plenty of external packages that should be mentioned. For example, [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) is a Julia wrapper for the `MPI` protocol, [`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) provides functionality similar to Python's [Dask](https://dask.org/), and [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) provides array operations distributed across workers, as [outlined above](@ref man-shared-arrays).

Une mention doit être faite de l'écosystème de programmation GPU de Julia, qui comprend :

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) enveloppe les différentes bibliothèques CUDA et prend en charge la compilation des noyaux Julia pour les GPU Nvidia.
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl) enveloppe le modèle de programmation unifié oneAPI et prend en charge l'exécution des noyaux Julia sur les accélérateurs pris en charge. Actuellement, seul Linux est pris en charge.
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) enveloppe les bibliothèques AMD ROCm et prend en charge la compilation des noyaux Julia pour les GPU AMD. Actuellement, seul Linux est pris en charge.
4. Des bibliothèques de haut niveau comme [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [Tullio.jl](https://github.com/mcabbott/Tullio.jl) et [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl).

Dans l'exemple suivant, nous utiliserons à la fois `DistributedArrays.jl` et `CUDA.jl` pour distribuer un tableau sur plusieurs processus en le convertissant d'abord via `distribute()` et `CuArray()`.

Rappelez-vous qu'en important `DistributedArrays.jl`, il faut l'importer sur tous les processus en utilisant [`@everywhere`](@ref)

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

Dans l'exemple suivant, nous utiliserons à la fois `DistributedArrays.jl` et `CUDA.jl` pour distribuer un tableau sur plusieurs processus et appeler une fonction générique dessus.

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method` crée à plusieurs reprises un nouveau vecteur et le normalise. Nous n'avons pas spécifié de signature de type dans la déclaration de fonction, voyons si cela fonctionne avec les types de données mentionnés ci-dessus :

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

Pour mettre fin à cette brève exposition aux packages externes, nous pouvons considérer `MPI.jl`, un wrapper Julia du protocole MPI. Comme il serait trop long de considérer chaque fonction interne, il serait préférable d'apprécier simplement l'approche utilisée pour implémenter le protocole.

Considérez ce script de démonstration qui appelle simplement chaque sous-processus, instancie son rang et lorsque le processus maître est atteint, effectue la somme des rangs.

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).

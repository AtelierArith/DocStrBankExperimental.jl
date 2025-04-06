# [Code Loading](@id code-loading)

!!! note
    Ce chapitre couvre les détails techniques du chargement des paquets. Pour installer des paquets, utilisez [`Pkg`](@ref Pkg), le gestionnaire de paquets intégré de Julia, pour ajouter des paquets à votre environnement actif. Pour utiliser des paquets déjà présents dans votre environnement actif, écrivez `import X` ou `using X`, comme décrit dans le [Modules documentation](@ref modules).


## Definitions

Julia a deux mécanismes pour charger du code :

1. **Inclusion de code :** par exemple `include("source.jl")`. L'inclusion vous permet de diviser un programme unique en plusieurs fichiers sources. L'expression `include("source.jl")` fait en sorte que le contenu du fichier `source.jl` soit évalué dans le scope global du module où l'appel `include` se produit. Si `include("source.jl")` est appelé plusieurs fois, `source.jl` est évalué plusieurs fois. Le chemin inclus, `source.jl`, est interprété par rapport au fichier où l'appel `include` se produit. Cela facilite le déplacement d'un sous-arbre de fichiers sources. Dans le REPL, les chemins inclus sont interprétés par rapport au répertoire de travail actuel, [`pwd()`](@ref).
2. **Chargement de package :** par exemple `import X` ou `using X`. Le mécanisme d'importation vous permet de charger un package—c'est-à-dire une collection indépendante et réutilisable de code Julia, encapsulée dans un module—et rend le module résultant disponible sous le nom `X` à l'intérieur du module importateur. Si le même package `X` est importé plusieurs fois dans la même session Julia, il n'est chargé qu'une seule fois—lors des importations suivantes, le module importateur obtient une référence au même module. Notez cependant que `import X` peut charger différents packages dans différents contextes : `X` peut faire référence à un package nommé `X` dans le projet principal mais potentiellement à différents packages également nommés `X` dans chaque dépendance. Plus d'informations à ce sujet ci-dessous.

L'inclusion de code est assez simple et directe : elle évalue le fichier source donné dans le contexte de l'appelant. Le chargement de paquets est construit sur l'inclusion de code et sert un [different purpose](@ref modules). Le reste de ce chapitre se concentre sur le comportement et les mécanismes du chargement de paquets.

Un *package* est un arbre source avec une structure standard fournissant des fonctionnalités qui peuvent être réutilisées par d'autres projets Julia. Un package est chargé par les instructions `import X` ou `using X`. Ces instructions rendent également le module nommé `X`—qui résulte du chargement du code du package—disponible dans le module où l'instruction d'importation se produit. La signification de `X` dans `import X` dépend du contexte : quel package `X` est chargé dépend du code dans lequel l'instruction se trouve. Ainsi, le traitement de `import X` se fait en deux étapes : d'abord, il détermine **quel** package est défini comme étant `X` dans ce contexte ; ensuite, il détermine **où** ce package `X` particulier se trouve.

Ces questions sont répondues en recherchant dans les environnements de projet listés dans [`LOAD_PATH`](@ref) des fichiers de projet (`Project.toml` ou `JuliaProject.toml`), des fichiers de manifeste (`Manifest.toml` ou `JuliaManifest.toml`, ou les mêmes noms suffixés par `-v{major}.{minor}.toml` pour des versions spécifiques), ou des dossiers de fichiers source.

## Federation of packages

La plupart du temps, un package est identifiable de manière unique simplement par son nom. Cependant, il arrive parfois qu'un projet rencontre une situation où il doit utiliser deux packages différents qui partagent le même nom. Bien que vous puissiez résoudre ce problème en renommant l'un des packages, être contraint de le faire peut être très perturbant dans une grande base de code partagée. Au lieu de cela, le mécanisme de chargement de code de Julia permet au même nom de package de faire référence à différents packages dans différents composants d'une application.

Julia prend en charge la gestion fédérée des packages, ce qui signifie que plusieurs parties indépendantes peuvent maintenir à la fois des packages publics et privés ainsi que des registres de packages, et que les projets peuvent dépendre d'un mélange de packages publics et privés provenant de différents registres. Les packages provenant de divers registres sont installés et gérés à l'aide d'un ensemble commun d'outils et de flux de travail. Le gestionnaire de packages `Pkg` qui est fourni avec Julia vous permet d'installer et de gérer les dépendances de vos projets. Il aide à créer et à manipuler des fichiers de projet (qui décrivent les autres projets dont votre projet dépend) et des fichiers de manifeste (qui capturent les versions exactes de l'ensemble du graphe de dépendance de votre projet).

Une conséquence de la fédération est qu'il ne peut y avoir d'autorité centrale pour la nomination des paquets. Différentes entités peuvent utiliser le même nom pour désigner des paquets non liés. Cette possibilité est inévitable puisque ces entités ne se coordonnent pas et peuvent même ne pas être au courant les unes des autres. En raison du manque d'une autorité centrale de nomination, un seul projet peut finir par dépendre de différents paquets ayant le même nom. Le mécanisme de chargement des paquets de Julia ne nécessite pas que les noms des paquets soient globalement uniques, même au sein du graphe de dépendance d'un seul projet. Au lieu de cela, les paquets sont identifiés par [universally unique identifiers](https://en.wikipedia.org/wiki/Universally_unique_identifier) (UUIDs), qui sont attribués lorsque chaque paquet est créé. En général, vous n'aurez pas à travailler directement avec ces identifiants 128 bits quelque peu encombrants, car `Pkg` s'occupera de les générer et de les suivre pour vous. Cependant, ces UUIDs fournissent la réponse définitive à la question de *"quel paquet `X` désigne-t-il ?"*

Puisque le problème de nommage décentralisé est quelque peu abstrait, il peut être utile de passer par un scénario concret pour comprendre la question. Supposons que vous développiez une application appelée `App`, qui utilise deux packages : `Pub` et `Priv`. `Priv` est un package privé que vous avez créé, tandis que `Pub` est un package public que vous utilisez mais que vous ne contrôlez pas. Lorsque vous avez créé `Priv`, il n'y avait pas de package public du nom de `Priv`. Cependant, par la suite, un package non lié portant également le nom `Priv` a été publié et est devenu populaire. En fait, le package `Pub` a commencé à l'utiliser. Par conséquent, lorsque vous mettrez à jour `Pub` pour obtenir les derniers correctifs et fonctionnalités, `App` finira par dépendre de deux packages différents nommés `Priv`—sans aucune action de votre part autre que la mise à jour. `App` a une dépendance directe sur votre package privé `Priv`, et une dépendance indirecte, à travers `Pub`, sur le nouveau package public `Priv`. Étant donné que ces deux packages `Priv` sont différents mais sont tous deux nécessaires pour que `App` continue de fonctionner correctement, l'expression `import Priv` doit faire référence à différents packages `Priv` selon qu'elle se trouve dans le code de `App` ou dans le code de `Pub`. Pour gérer cela, le mécanisme de chargement des packages de Julia distingue les deux packages `Priv` par leur UUID et choisit le bon en fonction de son contexte (le module qui a appelé `import`). Comment cette distinction fonctionne est déterminé par les environnements, comme expliqué dans les sections suivantes.

## Environments

Un *environnement* détermine ce que signifie `import X` et `using X` dans divers contextes de code et quels fichiers ces déclarations entraînent à être chargés. Julia comprend deux types d'environnements :

1. **Un environnement de projet** est un répertoire contenant un fichier de projet et un fichier manifeste optionnel, et constitue un *environnement explicite*. Le fichier de projet détermine quels sont les noms et les identités des dépendances directes d'un projet. Le fichier manifeste, s'il est présent, fournit un graphe de dépendance complet, y compris toutes les dépendances directes et indirectes, les versions exactes de chaque dépendance, et des informations suffisantes pour localiser et charger la version correcte.
2. **Un répertoire de package** est un répertoire contenant les arbres source d'un ensemble de packages en tant que sous-répertoires, et forme un *environnement implicite*. Si `X` est un sous-répertoire d'un répertoire de package et que `X/src/X.jl` existe, alors le package `X` est disponible dans l'environnement du répertoire de package et `X/src/X.jl` est le fichier source par lequel il est chargé.

Ces éléments peuvent être mélangés pour créer **un environnement empilé** : un ensemble ordonné d'environnements de projet et de répertoires de paquets, superposés pour former un seul environnement composite. Les règles de priorité et de visibilité se combinent ensuite pour déterminer quels paquets sont disponibles et d'où ils sont chargés. Le chemin de chargement de Julia forme un environnement empilé, par exemple.

Ces environnements servent chacun un but différent :

  * Les environnements de projet offrent **reproductibilité**. En enregistrant un environnement de projet dans le contrôle de version—par exemple, un dépôt git—avec le reste du code source du projet, vous pouvez reproduire l'état exact du projet et de toutes ses dépendances. Le fichier manifeste, en particulier, capture la version exacte de chaque dépendance, identifiée par un hachage cryptographique de son arbre source, ce qui permet à `Pkg` de récupérer les bonnes versions et de s'assurer que vous exécutez le code exact qui a été enregistré pour toutes les dépendances.
  * Les répertoires de packages offrent **une commodité** lorsque l'environnement de projet complet et soigneusement suivi n'est pas nécessaire. Ils sont utiles lorsque vous souhaitez placer un ensemble de packages quelque part et pouvoir les utiliser directement, sans avoir besoin de créer un environnement de projet pour eux.
  * Les environnements empilés permettent **d'ajouter** des outils à l'environnement principal. Vous pouvez ajouter un environnement d'outils de développement à la fin de la pile pour les rendre disponibles depuis le REPL et les scripts, mais pas depuis l'intérieur des paquets.

À un niveau élevé, chaque environnement définit conceptuellement trois cartes : racines, graphique et chemins. Lors de la résolution de la signification de `import X`, les cartes des racines et du graphique sont utilisées pour déterminer l'identité de `X`, tandis que la carte des chemins est utilisée pour localiser le code source de `X`. Les rôles spécifiques des trois cartes sont :

  * **racines :** `nom::Symbole` ⟶ `uuid::UUID`

    Une carte des racines de l'environnement associe des noms de paquets à des UUID pour toutes les dépendances de premier niveau que l'environnement met à la disposition du projet principal (c'est-à-dire celles qui peuvent être chargées dans `Main`). Lorsque Julia rencontre `import X` dans le projet principal, elle recherche l'identité de `X` en tant que `roots[:X]`.
  * **graph:** `contexte::UUID` ⟶ `nom::Symbole` ⟶ `uuid::UUID`

    Un graphe d'environnement est une carte multilevel qui attribue, pour chaque UUID de `contexte`, une carte de noms à des UUID, similaire à la carte des racines mais spécifique à ce `contexte`. Lorsque Julia voit `import X` dans le code du package dont l'UUID est `contexte`, elle recherche l'identité de `X` comme `graph[contexte][:X]`. En particulier, cela signifie que `import X` peut faire référence à différents packages en fonction du `contexte`.
  * **chemins :** `uuid::UUID` × `name::Symbol` ⟶ `path::String`

    La carte des chemins assigne à chaque paire UUID-nom de package, l'emplacement du fichier source du point d'entrée de ce package. Après que l'identité de `X` dans `import X` a été résolue en un UUID via les racines ou le graphe (selon qu'il soit chargé depuis le projet principal ou une dépendance), Julia détermine quel fichier charger pour acquérir `X` en consultant `paths[uuid,:X]` dans l'environnement. L'inclusion de ce fichier devrait définir un module nommé `X`. Une fois ce package chargé, toute importation subséquente se résolvant au même `uuid` créera une nouvelle liaison au module de package déjà chargé.

Chaque type d'environnement définit ces trois cartes différemment, comme détaillé dans les sections suivantes.

!!! note
    Pour faciliter la compréhension, les exemples tout au long de ce chapitre montrent des structures de données complètes pour les racines, les graphes et les chemins. Cependant, le code de chargement des paquets de Julia ne crée pas explicitement ces structures. Au lieu de cela, il calcule paresseusement uniquement autant de chaque structure que nécessaire pour charger un paquet donné.


### Project environments

Un environnement de projet est déterminé par un répertoire contenant un fichier de projet appelé `Project.toml`, et éventuellement un fichier de manifeste appelé `Manifest.toml`. Ces fichiers peuvent également être appelés `JuliaProject.toml` et `JuliaManifest.toml`, auquel cas `Project.toml` et `Manifest.toml` sont ignorés. Cela permet la coexistence avec d'autres outils qui pourraient considérer les fichiers appelés `Project.toml` et `Manifest.toml` comme significatifs. Pour les projets purement Julia, cependant, les noms `Project.toml` et `Manifest.toml` sont préférés. Cependant, à partir de Julia v1.10.8, `(Julia)Manifest-v{major}.{minor}.toml` est reconnu comme un format pour faire en sorte qu'une version donnée de Julia utilise un fichier de manifeste spécifique, c'est-à-dire que dans le même dossier, un `Manifest-v1.11.toml` serait utilisé par v1.11 et `Manifest.toml` par toute autre version de Julia.

Les racines, le graphique et les cartes de chemins d'un environnement de projet sont définis comme suit :

**La carte des racines** de l'environnement est déterminée par le contenu du fichier de projet, en particulier par ses entrées `name` et `uuid` au niveau supérieur et sa section `[deps]` (toutes facultatives). Considérez le fichier de projet d'exemple suivant pour l'application hypothétique, `App`, comme décrit précédemment :

```toml
name = "App"
uuid = "8f986787-14fe-4607-ba5d-fbff2944afa9"

[deps]
Priv = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
Pub  = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
```

Ce fichier de projet implique la carte des racines suivante, si elle était représentée par un dictionnaire Julia :

```julia
roots = Dict(
    :App  => UUID("8f986787-14fe-4607-ba5d-fbff2944afa9"),
    :Priv => UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"),
    :Pub  => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
)
```

Étant donné cette carte des racines, dans le code de `App`, l'instruction `import Priv` amènera Julia à rechercher `roots[:Priv]`, ce qui donne `ba13f791-ae1d-465a-978b-69c3ad90f72b`, l'UUID du package `Priv` qui doit être chargé dans ce contexte. Cet UUID identifie quel package `Priv` charger et utiliser lorsque l'application principale évalue `import Priv`.

**Le graphe de dépendance** d'un environnement de projet est déterminé par le contenu du fichier manifeste, s'il est présent. S'il n'y a pas de fichier manifeste, le graphe est vide. Un fichier manifeste contient une strophe pour chacune des dépendances directes ou indirectes d'un projet. Pour chaque dépendance, le fichier liste l'UUID du paquet et un hachage de l'arbre source ou un chemin explicite vers le code source. Considérez le fichier manifeste d'exemple suivant pour `App` :

```toml
[[Priv]] # the private one
deps = ["Pub", "Zebra"]
uuid = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
path = "deps/Priv"

[[Priv]] # the public one
uuid = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
git-tree-sha1 = "1bf63d3be994fe83456a03b874b409cfd59a6373"
version = "0.1.5"

[[Pub]]
uuid = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
git-tree-sha1 = "9ebd50e2b0dd1e110e842df3b433cb5869b0dd38"
version = "2.1.4"

  [Pub.deps]
  Priv = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
  Zebra = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"

[[Zebra]]
uuid = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"
git-tree-sha1 = "e808e36a5d7173974b90a15a353b564f3494092f"
version = "3.4.2"
```

Ce fichier manifeste décrit un possible graphe de dépendances complet pour le projet `App` :

  * Il existe deux packages différents nommés `Priv` que l'application utilise. Elle utilise un package privé, qui est une dépendance racine, et un public, qui est une dépendance indirecte via `Pub`. Ceux-ci sont différenciés par leurs UUID distincts, et ils ont des dépendances différentes :

      * Le privé `Priv` dépend des paquets `Pub` et `Zebra`.
      * Le public `Priv` n'a pas de dépendances.
  * L'application dépend également du package `Pub`, qui dépend à son tour du public `Priv` et du même package `Zebra` dont dépend le package privé `Priv`.

Ce graphique de dépendance représenté sous forme de dictionnaire ressemble à ceci :

```julia
graph = Dict(
    # Priv – the private one:
    UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b") => Dict(
        :Pub   => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Priv – the public one:
    UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c") => Dict(),
    # Pub:
    UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1") => Dict(
        :Priv  => UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Zebra:
    UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62") => Dict(),
)
```

Étant donné ce `graph` de dépendance, lorsque Julia voit `import Priv` dans le package `Pub`—qui a l'UUID `c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1`—elle effectue une recherche :

```julia
graph[UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1")][:Priv]
```

et obtient `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`, ce qui indique que dans le contexte du package `Pub`, `import Priv` fait référence au package public `Priv`, plutôt qu'à celui privé dont l'application dépend directement. C'est ainsi que le nom `Priv` peut faire référence à différents packages dans le projet principal par rapport à l'un des packages dont il dépend, ce qui permet d'avoir des noms dupliqués dans l'écosystème des packages.

Que se passe-t-il si `import Zebra` est évalué dans la base de code principale `App` ? Étant donné que `Zebra` n'apparaît pas dans le fichier du projet, l'importation échouera même si `Zebra` *apparaît* dans le fichier manifeste. De plus, si `import Zebra` se produit dans le package public `Priv`—celui avec l'UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—cela échouera également puisque ce package `Priv` n'a pas de dépendances déclarées dans le fichier manifeste et ne peut donc pas charger de packages. Le package `Zebra` ne peut être chargé que par des packages pour lesquels il apparaît comme une dépendance explicite dans le fichier manifeste : le package `Pub` et l'un des packages `Priv`.

**La carte des chemins** d'un environnement de projet est extraite du fichier manifeste. Le chemin d'un package `uuid` nommé `X` est déterminé par ces règles (dans l'ordre) :

1. Si le fichier de projet dans le répertoire correspond à `uuid` et au nom `X`, alors soit :

      * Il y a une entrée `path` de niveau supérieur, puis `uuid` sera mappé à ce chemin, interprété par rapport au répertoire contenant le fichier du projet.
      * Sinon, `uuid` est mappé à `src/X.jl` par rapport au répertoire contenant le fichier du projet.
2. Si ce n'est pas le cas et que le fichier de projet a un fichier manifeste correspondant et que le manifeste contient une strophe correspondant à `uuid`, alors :

      * Si elle a une entrée `path`, utilisez ce chemin (par rapport au répertoire contenant le fichier manifeste).
      * Si elle a une entrée `git-tree-sha1`, calculez une fonction de hachage déterministe de `uuid` et `git-tree-sha1`—appelée `slug`—et recherchez un répertoire nommé `packages/X/$slug` dans chaque répertoire du tableau global `DEPOT_PATH` de Julia. Utilisez le premier répertoire qui existe.

Si l'un de ces résultats aboutit à un succès, le chemin vers le point d'entrée du code source sera soit ce résultat, soit le chemin relatif à partir de ce résultat plus `src/X.jl` ; sinon, il n'y a pas de mappage de chemin pour `uuid`. Lors du chargement de `X`, si aucun chemin de code source n'est trouvé, la recherche échouera, et l'utilisateur pourra être invité à installer la version appropriée du package ou à prendre d'autres mesures correctives (par exemple, déclarer `X` comme dépendance).

Dans le fichier manifeste d'exemple ci-dessus, pour trouver le chemin du premier package `Priv`—celui avec l'UUID `ba13f791-ae1d-465a-978b-69c3ad90f72b`—Julia recherche sa strophe dans le fichier manifeste, voit qu'il a une entrée `path`, regarde `deps/Priv` par rapport au répertoire du projet `App`—supposons que le code de `App` se trouve dans `/home/me/projects/App`—voit que `/home/me/projects/App/deps/Priv` existe et charge donc `Priv` à partir de là.

Si, en revanche, Julia chargeait le *autre* paquet `Priv`—celui avec l'UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—il trouve son strophe dans le manifeste, voit qu'il n'a *pas* d'entrée `path`, mais qu'il a une entrée `git-tree-sha1`. Il calcule ensuite le `slug` pour cette paire UUID/SHA-1, qui est `HDkrT` (les détails exacts de ce calcul ne sont pas importants, mais il est cohérent et déterministe). Cela signifie que le chemin vers ce paquet `Priv` sera `packages/Priv/HDkrT/src/Priv.jl` dans l'un des dépôts de paquets. Supposons que le contenu de `DEPOT_PATH` soit `["/home/me/.julia", "/usr/local/julia"]`, alors Julia examinera les chemins suivants pour voir s'ils existent :

1. `/home/me/.julia/packages/Priv/HDkrT`
2. `/usr/local/julia/packages/Priv/HDkrT`

Julia utilise le premier de ces éléments qui existe pour essayer de charger le package public `Priv` à partir du fichier `packages/Priv/HDKrT/src/Priv.jl` dans le dépôt où il a été trouvé.

Voici une représentation d'une carte des chemins possibles pour notre projet `App`, comme indiqué dans le manifeste ci-dessus pour le graphique de dépendances, après avoir recherché dans le système de fichiers local :

```julia
paths = Dict(
    # Priv – the private one:
    (UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"), :Priv) =>
        # relative entry-point inside `App` repo:
        "/home/me/projects/App/deps/Priv/src/Priv.jl",
    # Priv – the public one:
    (UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"), :Priv) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Priv/HDkr/src/Priv.jl",
    # Pub:
    (UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"), :Pub) =>
        # package installed in the user depot:
        "/home/me/.julia/packages/Pub/oKpw/src/Pub.jl",
    # Zebra:
    (UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"), :Zebra) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Zebra/me9k/src/Zebra.jl",
)
```

Cette carte d'exemple comprend trois types différents d'emplacements de paquets (le premier et le troisième font partie du chemin de chargement par défaut) :

1. Le package privé `Priv` est "[vendored](https://stackoverflow.com/a/35109534)" à l'intérieur du dépôt `App`.
2. Les paquets publics `Priv` et `Zebra` se trouvent dans le dépôt système, où les paquets installés et gérés par l'administrateur système résident. Ceux-ci sont disponibles pour tous les utilisateurs du système.
3. Le paquet `Pub` est dans le dépôt utilisateur, où se trouvent les paquets installés par l'utilisateur. Ceux-ci ne sont disponibles que pour l'utilisateur qui les a installés.

### Package directories

Les répertoires de packages offrent un type d'environnement plus simple sans la capacité de gérer les collisions de noms. Dans un répertoire de package, l'ensemble des packages de premier niveau est l'ensemble des sous-répertoires qui "ressemblent" à des packages. Un package `X` existe dans un répertoire de package si le répertoire contient l'un des fichiers "point d'entrée" suivants :

  * `X.jl`
  * `X/src/X.jl`
  * `X.jl/src/X.jl`

Les dépendances qu'un paquet dans un répertoire de paquet peut importer dépendent de la présence d'un fichier de projet dans le paquet :

  * S'il a un fichier de projet, il ne peut importer que les packages qui sont identifiés dans la section `[deps]` du fichier de projet.
  * S'il n'a pas de fichier de projet, il peut importer n'importe quel package de niveau supérieur—c'est-à-dire les mêmes packages qui peuvent être chargés dans `Main` ou le REPL.

**La carte des racines** est déterminée en examinant le contenu du répertoire du package pour générer une liste de tous les packages qui existent. De plus, un UUID sera attribué à chaque entrée comme suit : Pour un package donné trouvé dans le dossier `X`...

1. Si `X/Project.toml` existe et a une entrée `uuid`, alors `uuid` est cette valeur.
2. Si `X/Project.toml` existe mais n'a *pas* d'entrée UUID au niveau supérieur, `uuid` est un UUID fictif généré en hachant le chemin canonique (réel) vers `X/Project.toml`.
3. Sinon (si `Project.toml` n'existe pas), alors `uuid` est le tout-zéro [nil UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Nil_UUID).

**Le graphe de dépendance** d'un répertoire de projet est déterminé par la présence et le contenu des fichiers de projet dans le sous-répertoire de chaque package. Les règles sont :

  * Si un sous-répertoire de package n'a pas de fichier de projet, il est omis du graphique et les instructions d'importation dans son code sont traitées comme de niveau supérieur, de la même manière que le projet principal et le REPL.
  * Si un sous-répertoire de package a un fichier de projet, alors l'entrée du graphe pour son UUID est la carte `[deps]` du fichier de projet, qui est considérée comme vide si la section est absente.

En tant qu'exemple, supposons qu'un répertoire de package ait la structure et le contenu suivants :

```
Aardvark/
    src/Aardvark.jl:
        import Bobcat
        import Cobra

Bobcat/
    Project.toml:
        [deps]
        Cobra = "4725e24d-f727-424b-bca0-c4307a3456fa"
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Bobcat.jl:
        import Cobra
        import Dingo

Cobra/
    Project.toml:
        uuid = "4725e24d-f727-424b-bca0-c4307a3456fa"
        [deps]
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Cobra.jl:
        import Dingo

Dingo/
    Project.toml:
        uuid = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Dingo.jl:
        # no imports
```

Voici une structure de racines correspondante, représentée sous forme de dictionnaire :

```julia
roots = Dict(
    :Aardvark => UUID("00000000-0000-0000-0000-000000000000"), # no project file, nil UUID
    :Bobcat   => UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), # dummy UUID based on path
    :Cobra    => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), # UUID from project file
    :Dingo    => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), # UUID from project file
)
```

Voici la structure de graphe correspondante, représentée sous forme de dictionnaire :

```julia
graph = Dict(
    # Bobcat:
    UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf") => Dict(
        :Cobra => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"),
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Cobra:
    UUID("4725e24d-f727-424b-bca0-c4307a3456fa") => Dict(
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Dingo:
    UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc") => Dict(),
)
```

Quelques règles générales à noter :

1. Un package sans fichier de projet peut dépendre de n'importe quelle dépendance de premier niveau, et comme chaque package dans un répertoire de packages est disponible au niveau supérieur, il peut importer tous les packages dans l'environnement.
2. Un package avec un fichier de projet ne peut pas dépendre d'un sans fichier de projet, car les packages avec des fichiers de projet ne peuvent charger que des packages dans `graph` et les packages sans fichiers de projet n'apparaissent pas dans `graph`.
3. Un package avec un fichier de projet mais sans UUID explicite ne peut être dépendu que par des packages sans fichiers de projet, car les UUID fictifs attribués à ces packages sont strictement internes.

Veuillez observer les exemples spécifiques de ces règles dans notre exemple :

  * `Aardvark` peut importer sur n'importe lequel de `Bobcat`, `Cobra` ou `Dingo` ; il importe `Bobcat` et `Cobra`.
  * `Bobcat` peut et importe effectivement à la fois `Cobra` et `Dingo`, qui ont tous deux des fichiers de projet avec des UUID et sont déclarés comme dépendances dans la section `[deps]` de `Bobcat`.
  * `Bobcat` ne peut pas dépendre de `Aardvark` puisque `Aardvark` n'a pas de fichier de projet.
  * `Cobra` peut et fait importer `Dingo`, qui a un fichier de projet et un UUID, et est déclaré comme une dépendance dans la section `[deps]` de `Cobra`.
  * `Cobra` ne peut pas dépendre de `Aardvark` ou `Bobcat` car aucun d'eux n'a de UUID réel.
  * `Dingo` ne peut rien importer car il a un fichier de projet sans section `[deps]`.

**La carte des chemins** dans un répertoire de package est simple : elle associe les noms de sous-répertoires à leurs chemins d'entrée correspondants. En d'autres termes, si le chemin vers notre répertoire de projet exemple est `/home/me/animals`, alors la carte `paths` pourrait être représentée par ce dictionnaire :

```julia
paths = Dict(
    (UUID("00000000-0000-0000-0000-000000000000"), :Aardvark) =>
        "/home/me/AnimalPackages/Aardvark/src/Aardvark.jl",
    (UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), :Bobcat) =>
        "/home/me/AnimalPackages/Bobcat/src/Bobcat.jl",
    (UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), :Cobra) =>
        "/home/me/AnimalPackages/Cobra/src/Cobra.jl",
    (UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), :Dingo) =>
        "/home/me/AnimalPackages/Dingo/src/Dingo.jl",
)
```

Puisque tous les packages dans un environnement de répertoire de packages sont, par définition, des sous-répertoires avec les fichiers d'entrée attendus, leurs entrées de mappage `paths` ont toujours cette forme.

### Environment stacks

Le troisième et dernier type d'environnement est celui qui combine d'autres environnements en superposant plusieurs d'entre eux, rendant les paquets de chacun disponibles dans un seul environnement composite. Ces environnements composites sont appelés *piles d'environnement*. Le global `LOAD_PATH` de Julia définit une pile d'environnement—l'environnement dans lequel le processus Julia opère. Si vous souhaitez que votre processus Julia n'ait accès qu'aux paquets d'un seul projet ou répertoire de paquets, faites-en la seule entrée dans `LOAD_PATH`. Cependant, il est souvent très utile d'avoir accès à certains de vos outils préférés—bibliothèques standard, profileurs, débogueurs, utilitaires personnels, etc.—même s'ils ne sont pas des dépendances du projet sur lequel vous travaillez. En ajoutant un environnement contenant ces outils au chemin de chargement, vous y avez immédiatement accès dans le code de niveau supérieur sans avoir besoin de les ajouter à votre projet.

Le mécanisme pour combiner les racines, le graphique et les structures de données de chemins des composants d'une pile d'environnement est simple : elles sont fusionnées en tant que dictionnaires, favorisant les entrées antérieures sur les entrées ultérieures en cas de collisions de clés. En d'autres termes, si nous avons `stack = [env₁, env₂, …]`, alors nous avons :

```julia
roots = reduce(merge, reverse([roots₁, roots₂, …]))
graph = reduce(merge, reverse([graph₁, graph₂, …]))
paths = reduce(merge, reverse([paths₁, paths₂, …]))
```

Les variables sous-indexées `rootsᵢ`, `graphᵢ` et `pathsᵢ` correspondent aux environnements sous-indexés `envᵢ`, contenus dans `stack`. Le `reverse` est présent car `merge` privilégie le dernier argument plutôt que le premier lorsqu'il y a des collisions entre les clés dans ses dictionnaires d'arguments. Il y a quelques caractéristiques notables de ce design :

1. L'*environnement principal*—c'est-à-dire le premier environnement dans une pile—est fidèlement intégré dans un environnement empilé. Le graphique de dépendance complet du premier environnement dans une pile est garanti d'être inclus intact dans l'environnement empilé, y compris les mêmes versions de toutes les dépendances.
2. Les paquets dans des environnements non principaux peuvent finir par utiliser des versions incompatibles de leurs dépendances, même si leurs propres environnements sont entièrement compatibles. Cela peut se produire lorsque l'une de leurs dépendances est masquée par une version dans un environnement antérieur dans la pile (soit par graphe, soit par chemin, ou les deux).

Puisque l'environnement principal est généralement l'environnement d'un projet sur lequel vous travaillez, tandis que les environnements plus tard dans la pile contiennent des outils supplémentaires, c'est le bon compromis : il vaut mieux casser vos outils de développement mais garder le projet fonctionnel. Lorsque de telles incompatibilités se produisent, vous voudrez généralement mettre à jour vos outils de développement vers des versions compatibles avec le projet principal.

### [Package Extensions](@id man-extensions)

Un package "extension" est un module qui est chargé automatiquement lorsqu'un ensemble spécifié d'autres packages (ses "déclencheurs") est chargé dans la session Julia actuelle. Les extensions sont définies sous la section `[extensions]` dans le fichier de projet. Les déclencheurs d'une extension sont un sous-ensemble de ces packages listés sous la section `[weakdeps]` (et éventuellement, mais rarement, la section `[deps]`) du fichier de projet. Ces packages peuvent avoir des entrées de compatibilité comme d'autres packages.

```toml
name = "MyPackage"

[compat]
ExtDep = "1.0"
OtherExtDep = "1.0"

[weakdeps]
ExtDep = "c9a23..." # uuid
OtherExtDep = "862e..." # uuid

[extensions]
BarExt = ["ExtDep", "OtherExtDep"]
FooExt = "ExtDep"
...
```

Les clés sous `extensions` sont les noms des extensions. Elles sont chargées lorsque tous les packages du côté droit (les déclencheurs) de cette extension sont chargés. Si une extension n'a qu'un seul déclencheur, la liste des déclencheurs peut être écrite simplement comme une chaîne pour plus de concision. L'emplacement du point d'entrée de l'extension se trouve soit dans `ext/FooExt.jl`, soit dans `ext/FooExt/FooExt.jl` pour l'extension `FooExt`. Le contenu d'une extension est souvent structuré comme :

```
module FooExt

# Load main package and triggers
using MyPackage, ExtDep

# Extend functionality in main package with types from the triggers
MyPackage.func(x::ExtDep.SomeStruct) = ...

end
```

Lorsqu'un package avec des extensions est ajouté à un environnement, les sections `weakdeps` et `extensions` sont stockées dans le fichier manifeste dans la section de ce package. Les règles de recherche de dépendances pour un package sont les mêmes que pour son "parent", sauf que les déclencheurs listés sont également considérés comme des dépendances.

### [Package/Environment Preferences](@id preferences)

Les préférences sont des dictionnaires de métadonnées qui influencent le comportement des paquets au sein d'un environnement. Le système de préférences prend en charge la lecture des préférences au moment de la compilation, ce qui signifie qu'au moment du chargement du code, nous devons nous assurer que les fichiers de précompilation sélectionnés par Julia ont été construits avec les mêmes préférences que l'environnement actuel avant de les charger. L'API publique pour modifier les préférences est contenue dans le paquet [Preferences.jl](https://github.com/JuliaPackaging/Preferences.jl). Les préférences sont stockées sous forme de dictionnaires TOML dans un fichier `(Julia)LocalPreferences.toml` à côté du projet actuellement actif. Si une préférence est "exportée", elle est plutôt stockée dans le `(Julia)Project.toml`. L'intention est de permettre aux projets partagés de contenir des préférences partagées, tout en permettant aux utilisateurs de remplacer ces préférences par leurs propres paramètres dans le fichier LocalPreferences.toml, qui devrait être ignoré par git comme son nom l'indique.

Les préférences qui sont accessibles pendant la compilation sont automatiquement marquées comme des préférences à temps de compilation, et tout changement enregistré dans ces préférences entraînera la recompilation par le compilateur Julia de tout fichier de précompilation mis en cache (`.ji` et les fichiers correspondants `.so`, `.dll` ou `.dylib`) pour ce module. Cela se fait en sérialisant le hachage de toutes les préférences à temps de compilation pendant la compilation, puis en vérifiant ce hachage par rapport à l'environnement actuel lors de la recherche des fichiers appropriés à charger.

Les préférences peuvent être définies avec des valeurs par défaut à l'échelle du dépôt ; si le package Foo est installé dans votre environnement global et qu'il a des préférences définies, ces préférences s'appliqueront tant que votre environnement global fait partie de votre `LOAD_PATH`. Les préférences dans les environnements plus élevés dans la pile d'environnements sont remplacées par les entrées plus proches dans le chemin de chargement, se terminant par le projet actuellement actif. Cela permet d'avoir des valeurs par défaut de préférences à l'échelle du dépôt, les projets actifs pouvant fusionner ou même complètement écraser ces préférences héritées. Consultez la docstring pour `Preferences.set_preferences!()` pour tous les détails sur la façon de définir des préférences pour autoriser ou interdire la fusion.

## Conclusion

La gestion de paquets fédérée et la reproductibilité précise des logiciels sont des objectifs difficiles mais dignes d'intérêt dans un système de paquets. En combinaison, ces objectifs conduisent à un mécanisme de chargement de paquets plus complexe que la plupart des langages dynamiques, mais cela offre également une évolutivité et une reproductibilité qui sont plus couramment associées aux langages statiques. En général, les utilisateurs de Julia devraient être en mesure d'utiliser le gestionnaire de paquets intégré pour gérer leurs projets sans avoir besoin de comprendre précisément ces interactions. Un appel à `Pkg.add("X")` ajoutera aux fichiers de projet et de manifeste appropriés, sélectionnés via `Pkg.activate("Y")`, de sorte qu'un appel futur à `import X` chargera `X` sans réflexion supplémentaire.

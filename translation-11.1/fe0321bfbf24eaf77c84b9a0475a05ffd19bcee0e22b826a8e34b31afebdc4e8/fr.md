```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

Veuillez lire le [release notes](NEWS.md) pour voir ce qui a changé depuis la dernière version.

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

Voici une liste non exhaustive de liens qui vous seront utiles alors que vous apprenez et utilisez le langage de programmation Julia.

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

Le calcul scientifique a traditionnellement nécessité les meilleures performances, mais les experts en la matière se sont largement tournés vers des langages dynamiques plus lents pour leur travail quotidien. Nous croyons qu'il existe de nombreuses bonnes raisons de préférer les langages dynamiques pour ces applications, et nous ne nous attendons pas à ce que leur utilisation diminue. Heureusement, la conception moderne des langages et les techniques de compilation rendent possible l'élimination presque totale du compromis en matière de performance et fournissent un environnement suffisamment productif pour le prototypage et suffisamment efficace pour le déploiement d'applications nécessitant des performances élevées. Le langage de programmation Julia remplit ce rôle : c'est un langage dynamique flexible, approprié pour le calcul scientifique et numérique, avec des performances comparables à celles des langages statiquement typés traditionnels.

Parce que le compilateur de Julia est différent des interprètes utilisés pour des langages comme Python ou R, vous constaterez peut-être que les performances de Julia sont contre-intuitives au début. Si vous trouvez que quelque chose est lent, nous vous recommandons fortement de lire la section [Performance Tips](@ref man-performance-tips) avant d'essayer quoi que ce soit d'autre. Une fois que vous comprenez comment Julia fonctionne, il est facile d'écrire du code qui est presque aussi rapide que C.

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia propose un typage optionnel, un dispatch multiple et de bonnes performances, obtenues grâce à l'inférence de type et [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (et [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)), mis en œuvre à l'aide de [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine). C'est un langage multi-paradigme, combinant des caractéristiques de la programmation impérative, fonctionnelle et orientée objet. Julia offre facilité et expressivité pour le calcul numérique de haut niveau, de la même manière que des langages tels que R, MATLAB et Python, mais prend également en charge la programmation générale. Pour y parvenir, Julia s'appuie sur l'héritage des langages de programmation mathématique, mais emprunte également beaucoup aux langages dynamiques populaires, y compris [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)), et [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)).

Les départs les plus significatifs de Julia par rapport aux langages dynamiques typiques sont :

  * Le langage de base impose très peu ; Julia Base et la bibliothèque standard sont écrites en Julia lui-même, y compris les opérations primitives comme l'arithmétique entière.
  * Un langage riche de types pour construire et décrire des objets, qui peut également être utilisé de manière optionnelle pour faire des déclarations de type.
  * La capacité de définir le comportement des fonctions à travers de nombreuses combinaisons de types d'arguments via [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)
  * Génération automatique de code efficace et spécialisé pour différents types d'arguments
  * Bonne performance, approchant celle des langages compilés statiquement comme C

Bien que l'on parle parfois des langages dynamiques comme étant "sans type", ce n'est définitivement pas le cas. Chaque objet, qu'il soit primitif ou défini par l'utilisateur, a un type. L'absence de déclarations de type dans la plupart des langages dynamiques signifie cependant qu'on ne peut pas instruire le compilateur sur les types de valeurs, et souvent on ne peut pas parler explicitement des types du tout. Dans les langages statiques, en revanche, bien qu'on puisse – et doive généralement – annoter les types pour le compilateur, les types n'existent qu'au moment de la compilation et ne peuvent pas être manipulés ou exprimés au moment de l'exécution. Dans Julia, les types sont eux-mêmes des objets d'exécution, et peuvent également être utilisés pour transmettre des informations au compilateur.

### [What Makes Julia, Julia?](@id man-what-makes-julia)

Bien que le programmeur occasionnel n'ait pas besoin d'utiliser explicitement des types ou un dispatch multiple, ceux-ci sont les caractéristiques unificatrices essentielles de Julia : les fonctions sont définies sur différentes combinaisons de types d'arguments et sont appliquées en dispatchant vers la définition la plus spécifique correspondante. Ce modèle convient bien à la programmation mathématique, où il est peu naturel que le premier argument "possède" une opération comme dans le dispatch orienté objet traditionnel. Les opérateurs ne sont que des fonctions avec une notation spéciale – pour étendre l'addition à de nouveaux types de données définis par l'utilisateur, vous définissez de nouvelles méthodes pour la fonction `+`. Le code existant s'applique alors sans problème aux nouveaux types de données.

En partie à cause de l'inférence de type à l'exécution (augmentée par des annotations de type optionnelles), et en partie en raison d'un fort accent sur la performance depuis le début du projet, l'efficacité computationnelle de Julia dépasse celle des autres langages dynamiques et rivalise même avec celle des langages compilés statiquement. Pour les problèmes numériques à grande échelle, la vitesse a toujours été, continue d'être et sera probablement toujours cruciale : la quantité de données traitées a facilement suivi le rythme de la loi de Moore au cours des dernières décennies.

### [Advantages of Julia](@id man-advantages-of-julia)

Julia vise à créer une combinaison sans précédent de facilité d'utilisation, de puissance et d'efficacité dans un seul langage. En plus de ce qui précède, certains avantages de Julia par rapport à des systèmes comparables incluent :

  * Libre et open source ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * Les types définis par l'utilisateur sont aussi rapides et compacts que les types intégrés.
  * Pas besoin de vectoriser le code pour des performances ; le code dévectorisé est rapide.
  * Conçu pour le parallélisme et le calcul distribué
  * Filtrage léger "vert" ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * Système de type discret mais puissant
  * Conversions et promotions élégantes et extensibles pour les types numériques et autres
  * Support efficace pour [Unicode](https://en.wikipedia.org/wiki/Unicode), y compris, mais sans s'y limiter, [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * Appeler des fonctions C directement (aucun wrapper ou API spéciale nécessaire)
  * Capacités puissantes similaires à un shell pour gérer d'autres processus
  * Macros et autres facilités de métaprogrammation semblables à Lisp

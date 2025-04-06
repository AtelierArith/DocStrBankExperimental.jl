# [Workflow Tips](@id man-workflow-tips)

Voici quelques conseils pour travailler efficacement avec Julia.

## REPL-based workflow

Comme déjà élaboré dans [The Julia REPL](@ref), le REPL de Julia offre une riche fonctionnalité qui facilite un flux de travail interactif efficace. Voici quelques conseils qui pourraient encore améliorer votre expérience en ligne de commande.

### A basic editor/REPL workflow

Les workflows Julia les plus basiques impliquent l'utilisation d'un éditeur de texte en conjonction avec la ligne de commande `julia`.

Créez un fichier, disons `Tmp.jl`, et incluez-le à l'intérieur

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

Ensuite, dans le même répertoire, démarrez le REPL Julia (en utilisant la commande `julia`). Exécutez le nouveau fichier comme suit :

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

Explorez des idées dans le REPL. Enregistrez de bonnes idées dans `Tmp.jl`. Pour recharger le fichier après qu'il a été modifié, il suffit de l'`inclure` à nouveau.

La clé ci-dessus est que votre code est encapsulé dans un module. Cela vous permet de modifier les définitions de `struct` et de supprimer des méthodes, sans redémarrer Julia.

(Explication : les `struct`s ne peuvent pas être modifiés après leur définition, ni les méthodes supprimées. Mais vous *pouvez* écraser la définition d'un module, ce que nous faisons lorsque nous ré-`include("Tmp.jl")`).

De plus, l'encapsulation du code dans un module le protège d'être influencé par l'état précédent dans le REPL, vous protégeant ainsi des erreurs difficiles à détecter.

## Browser-based workflow

Il existe plusieurs façons d'interagir avec Julia dans un navigateur :

  * Utiliser des notebooks Pluto via [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * Utiliser des notebooks Jupyter via [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

Que vous soyez au REPL ou dans IJulia, vous pouvez généralement améliorer votre expérience de développement avec [Revise](https://github.com/timholy/Revise.jl). Il est courant de configurer Revise pour qu'il démarre chaque fois que julia est lancé, conformément aux instructions dans le [Revise documentation](https://timholy.github.io/Revise.jl/stable/). Une fois configuré, Revise suivra les modifications apportées aux fichiers dans tous les modules chargés, et à tous les fichiers chargés dans le REPL avec `includet` (mais pas avec `include` classique) ; vous pouvez alors modifier les fichiers et les changements prennent effet sans redémarrer votre session julia. Un flux de travail standard est similaire au flux de travail basé sur le REPL ci-dessus, avec les modifications suivantes :

1. Mettez votre code dans un module quelque part sur votre chemin de chargement. Il existe plusieurs options pour y parvenir, dont deux choix recommandés sont :

      * Pour les projets à long terme, utilisez [PkgTemplates](https://github.com/invenia/PkgTemplates.jl) :

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        Cela créera un package vide, `"MyPkg"`, dans votre répertoire `.julia/dev`. Notez que PkgTemplates vous permet de contrôler de nombreuses options différentes via son constructeur `Template`.

        Dans l'étape 2 ci-dessous, modifiez `MyPkg/src/MyPkg.jl` pour changer le code source, et `MyPkg/test/runtests.jl` pour les tests.
      * Pour les projets "jetables", vous pouvez éviter tout besoin de nettoyage en effectuant votre travail dans votre répertoire temporaire (par exemple, `/tmp`).

        Naviguez vers votre répertoire temporaire et lancez Julia, puis faites ce qui suit :

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        Si vous redémarrez votre session Julia, vous devrez réémettre cette commande modifiant `LOAD_PATH`.

        Dans l'étape 2 ci-dessous, modifiez `MyPkg/src/MyPkg.jl` pour changer le code source, et créez tout fichier de test de votre choix.
2. Développez votre package

    *Avant* de charger du code, assurez-vous que vous exécutez Revise : dites `using Revise` ou suivez sa documentation pour le configurer afin qu'il s'exécute automatiquement.

    Ensuite, naviguez vers le répertoire contenant votre fichier de test (ici supposé être `"runtests.jl"`) et faites ce qui suit :

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    Vous pouvez modifier le code dans MyPkg de manière itérative dans votre éditeur et relancer les tests avec `include("runtests.jl")`. Vous ne devriez généralement pas avoir besoin de redémarrer votre session Julia pour voir les changements prendre effet (sous réserve de quelques [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)).

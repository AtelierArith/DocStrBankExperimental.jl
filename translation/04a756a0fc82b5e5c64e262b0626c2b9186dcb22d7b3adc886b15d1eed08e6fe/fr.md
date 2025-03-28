# [Getting Started](@id man-getting-started)

L'installation de Julia est simple, que ce soit en utilisant des binaires précompilés ou en compilant à partir de la source. Téléchargez et installez Julia en suivant les instructions à l'adresse [https://julialang.org/downloads/](https://julialang.org/downloads/).

Si vous venez à Julia depuis l'un des langages suivants, vous devriez commencer par lire la section sur les différences notables par rapport à [MATLAB](@ref Noteworthy-differences-from-MATLAB), [R](@ref Noteworthy-differences-from-R), [Python](@ref Noteworthy-differences-from-Python), [C/C++](@ref Noteworthy-differences-from-C/C) ou [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp). Cela vous aidera à éviter certains pièges courants, car Julia diffère de ces langages de nombreuses manières subtiles.

La façon la plus simple d'apprendre et d'expérimenter avec Julia est de commencer une session interactive (également connue sous le nom de boucle de lecture-évaluation-impression ou "REPL") en double-cliquant sur l'exécutable Julia ou en exécutant `julia` depuis la ligne de commande :

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

Pour quitter la session interactive, tapez `CTRL-D` (appuyez sur la touche Control/`^` en même temps que la touche `d`), ou tapez `exit()`. Lorsqu'il est exécuté en mode interactif, `julia` affiche une bannière et invite l'utilisateur à entrer une commande. Une fois que l'utilisateur a saisi une expression complète, comme `1 + 2`, et appuie sur entrée, la session interactive évalue l'expression et affiche sa valeur. Si une expression est saisie dans une session interactive avec un point-virgule à la fin, sa valeur n'est pas affichée. La variable `ans` est liée à la valeur de la dernière expression évaluée, qu'elle soit affichée ou non. La variable `ans` n'est liée que dans les sessions interactives, pas lorsque le code Julia est exécuté d'autres manières.

Pour évaluer des expressions écrites dans un fichier source `file.jl`, écrivez `include("file.jl")`.

Pour exécuter du code dans un fichier de manière non interactive, vous pouvez le donner comme premier argument à la commande `julia` :

```
$ julia script.jl
```

Vous pouvez passer des arguments supplémentaires à Julia et à votre programme `script.jl`. Une liste détaillée de toutes les options disponibles peut être trouvée sous [Command-line Interface](@ref cli).

## Resources

Une liste soigneusement sélectionnée de ressources d'apprentissage utiles pour aider les nouveaux utilisateurs à commencer peut être trouvée sur la [learning](https://julialang.org/learning/) page du site principal de Julia.

Vous pouvez utiliser le REPL comme ressource d'apprentissage en passant en mode d'aide. Passez en mode d'aide en appuyant sur `?` à un invite `julia>` vide, avant de taper quoi que ce soit d'autre. Taper un mot-clé en mode d'aide récupérera la documentation pour celui-ci, ainsi que des exemples. De même pour la plupart des fonctions ou autres objets que vous pourriez rencontrer !

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

Si vous connaissez déjà un peu Julia, vous voudrez peut-être jeter un œil à [Performance Tips](@ref man-performance-tips) et [Workflow Tips](@ref man-workflow-tips).

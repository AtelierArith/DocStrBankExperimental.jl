```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia est livré avec un REPL (read-eval-print loop) interactif et complet intégré dans l'exécutable `julia`. En plus de permettre une évaluation rapide et facile des instructions Julia, il dispose d'un historique consultable, de la complétion par tabulation, de nombreuses touches de raccourci utiles, ainsi que de modes d'aide et de shell dédiés. Le REPL peut être démarré en appelant simplement `julia` sans arguments ou en double-cliquant sur l'exécutable :

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

Pour quitter la session interactive, tapez `^D` – la touche de contrôle avec la touche `d` sur une ligne vide – ou tapez `exit()` suivi de la touche retour ou entrée. Le REPL vous accueille avec une bannière et un prompt `julia>`.

## The different prompt modes

### The Julian mode

Le REPL a cinq modes principaux de fonctionnement. Le premier et le plus courant est l'invite Julian. C'est le mode de fonctionnement par défaut ; chaque nouvelle ligne commence initialement par `julia>`. C'est ici que vous pouvez entrer des expressions Julia. Appuyer sur retour ou entrer après avoir saisi une expression complète évaluera l'entrée et affichera le résultat de la dernière expression.

```jldoctest
julia> string(1 + 2)
"3"
```

Il existe un certain nombre de fonctionnalités utiles propres au travail interactif. En plus d'afficher le résultat, le REPL lie également le résultat à la variable `ans`. Un point-virgule à la fin de la ligne peut être utilisé comme un indicateur pour supprimer l'affichage du résultat.

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

En mode Julia, le REPL prend en charge quelque chose appelé *collage de prompt*. Cela s'active lorsque vous collez du texte qui commence par `julia>` dans le REPL. Dans ce cas, seules les expressions commençant par `julia>` (ainsi que les autres invites de mode REPL : `shell>`, `help?>`, `pkg>`) sont analysées, mais les autres sont supprimées. Cela permet de coller un bloc de texte qui a été copié d'une session REPL sans avoir à supprimer les invites et les sorties. Cette fonctionnalité est activée par défaut mais peut être désactivée ou activée à volonté avec `REPL.enable_promptpaste(::Bool)`. Si elle est activée, vous pouvez l'essayer en collant le bloc de code au-dessus de ce paragraphe directement dans le REPL. Cette fonctionnalité ne fonctionne pas sur l'invite de commande Windows standard en raison de sa limitation à détecter quand un collage se produit.

Les objets sont imprimés au REPL en utilisant la fonction [`show`](@ref) avec un [`IOContext`](@ref) spécifique. En particulier, l'attribut `:limit` est défini sur `true`. D'autres attributs peuvent recevoir dans certaines méthodes `show` une valeur par défaut si elle n'est pas déjà définie, comme `:compact`. Il est possible, en tant que fonctionnalité expérimentale, de spécifier les attributs utilisés par le REPL via le dictionnaire `Base.active_repl.options.iocontext` (associant des valeurs aux attributs). Par exemple :

```julia-repl
julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.8833    0.329197
 0.719708  0.59114

julia> show(IOContext(stdout, :compact => false), "text/plain", rand(2, 2))
 0.43540323669187075  0.15759787870609387
 0.2540832269192739   0.4597637838786053
julia> Base.active_repl.options.iocontext[:compact] = false;

julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.2083967319174056  0.13330606013126012
 0.6244375177790158  0.9777957560761545
```

Pour définir automatiquement les valeurs de ce dictionnaire au moment du démarrage, on peut utiliser la fonction [`atreplinit`](@ref) dans le fichier `~/.julia/config/startup.jl`, par exemple :

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

Lorsque le curseur est au début de la ligne, l'invite peut être changée en mode d'aide en tapant `?`. Julia tentera d'imprimer de l'aide ou de la documentation pour tout ce qui est saisi en mode d'aide :

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

Les macros, types et variables peuvent également être interrogés :

```
help?> @time
  @time

  A macro to execute an expression, printing the time it took to execute, the number of allocations,
  and the total number of bytes its execution caused to be allocated, before returning the value of the
  expression.

  See also @timev, @timed, @elapsed, and @allocated.

help?> Int32
search: Int32 UInt32

  Int32 <: Signed

  32-bit signed integer type.
```

Une chaîne ou un littéral regex recherche toutes les docstrings en utilisant [`apropos`](@ref) :

```
help?> "aprop"
REPL.stripmd
Base.Docs.apropos

help?> r"ap..p"
Base.:∘
Base.shell_escape_posixly
Distributed.CachingPool
REPL.stripmd
Base.Docs.apropos
```

Une autre fonctionnalité du mode d'aide est la possibilité d'accéder à des docstrings étendues. Vous pouvez le faire en tapant quelque chose comme `??Print` plutôt que `?Print`, ce qui affichera la section `# Aide étendue` de la documentation du code source.

Le mode d'aide peut être quitté en appuyant sur la touche retour arrière au début de la ligne.

### [Shell mode](@id man-shell-mode)

Tout comme le mode d'aide est utile pour un accès rapide à la documentation, une autre tâche courante consiste à utiliser le shell du système pour exécuter des commandes système. Tout comme `?` entre en mode d'aide lorsqu'il est au début de la ligne, un point-virgule (`;`) entrera en mode shell. Et il peut être quitté en appuyant sur la touche de retour arrière au début de la ligne.

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    Pour les utilisateurs de Windows, le mode shell de Julia n'expose pas les commandes de l'invite de commandes Windows. Par conséquent, cela échouera :


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

Cependant, vous pouvez accéder à `PowerShell` de cette manière :

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... et à `cmd.exe` comme ça (voir la commande `dir`) :

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> cmd
Microsoft Windows [version 10.0.17763.973]
(c) 2018 Microsoft Corporation. All rights reserved.
C:\Users\elm>dir
 Volume in drive C has no label
 Volume Serial Number is 1643-0CD7
  Directory of C:\Users\elm

29/01/2020  22:15    <DIR>          .
29/01/2020  22:15    <DIR>          ..
02/02/2020  08:06    <DIR>          .atom
```

### Pkg mode

Le mode gestionnaire de paquets accepte des commandes spécialisées pour charger et mettre à jour des paquets. Il est activé en appuyant sur la touche `]` à l'invite REPL de Julian et désactivé en appuyant sur CTRL-C ou en appuyant sur la touche de retour arrière au début de la ligne. L'invite pour ce mode est `pkg>`. Il prend en charge son propre mode d'aide, qui est activé en appuyant sur `?` au début de la ligne de l'invite `pkg>`. Le mode gestionnaire de paquets est documenté dans le manuel Pkg, disponible à [https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/).

### Search modes

Dans tous les modes ci-dessus, les lignes exécutées sont enregistrées dans un fichier d'historique, qui peut être recherché. Pour initier une recherche incrémentale dans l'historique précédent, tapez `^R` – la touche de contrôle avec la touche `r`. L'invite changera en ```(reverse-i-search)`':```, et au fur et à mesure que vous tapez, la requête de recherche apparaîtra entre les guillemets. Le résultat le plus récent qui correspond à la requête se mettra à jour dynamiquement à droite des deux-points au fur et à mesure que vous tapez. Pour trouver un résultat plus ancien en utilisant la même requête, tapez simplement `^R` à nouveau.

Tout comme `^R` est une recherche inversée, `^S` est une recherche avancée, avec l'invite ```(i-search)`':```. Les deux peuvent être utilisés conjointement pour naviguer à travers les résultats correspondants précédents ou suivants, respectivement.

Toutes les commandes exécutées dans le REPL Julia sont enregistrées dans `~/.julia/logs/repl_history.jl` avec un horodatage indiquant quand elles ont été exécutées et le mode REPL actuel dans lequel vous vous trouviez. Le mode de recherche interroge ce fichier journal afin de trouver les commandes que vous avez précédemment exécutées. Cela peut être désactivé au démarrage en passant le drapeau `--history-file=no` à Julia.

## Key bindings

Le REPL de Julia utilise très bien les raccourcis clavier. Plusieurs raccourcis avec la touche de contrôle ont déjà été introduits ci-dessus (`^D` pour quitter, `^R` et `^S` pour rechercher), mais il y en a beaucoup d'autres. En plus de la touche de contrôle, il existe également des raccourcis avec la touche méta. Ceux-ci varient davantage selon la plateforme, mais la plupart des terminaux par défaut utilisent la touche alt- ou option- maintenue enfoncée avec une touche pour envoyer la touche méta (ou peuvent être configurés pour le faire), ou en appuyant sur Échap puis sur la touche.

| Keybinding           | Description                                                                                                |
|:-------------------- |:---------------------------------------------------------------------------------------------------------- |
| **Program control**  |                                                                                                            |
| `^D`                 | Exit (when buffer is empty)                                                                                |
| `^C`                 | Interrupt or cancel                                                                                        |
| `^L`                 | Clear console screen                                                                                       |
| Return/Enter, `^J`   | New line, executing if it is complete                                                                      |
| meta-Return/Enter    | Insert new line without executing it                                                                       |
| `?` or `;`           | Enter help or shell mode (when at start of a line)                                                         |
| `^R`, `^S`           | Incremental history search, described above                                                                |
| **Cursor movement**  |                                                                                                            |
| Right arrow, `^F`    | Move right one character                                                                                   |
| Left arrow, `^B`     | Move left one character                                                                                    |
| ctrl-Right, `meta-F` | Move right one word                                                                                        |
| ctrl-Left, `meta-B`  | Move left one word                                                                                         |
| Home, `^A`           | Move to beginning of line                                                                                  |
| End, `^E`            | Move to end of line                                                                                        |
| Up arrow, `^P`       | Move up one line (or change to the previous history entry that matches the text before the cursor)         |
| Down arrow, `^N`     | Move down one line (or change to the next history entry that matches the text before the cursor)           |
| Shift-Arrow Key      | Move cursor according to the direction of the Arrow key, while activating the region ("shift selection")   |
| Page-up, `meta-P`    | Change to the previous history entry                                                                       |
| Page-down, `meta-N`  | Change to the next history entry                                                                           |
| `meta-<`             | Change to the first history entry (of the current session if it is before the current position in history) |
| `meta->`             | Change to the last history entry                                                                           |
| `^-Space`            | Set the "mark" in the editing region (and de-activate the region if it's active)                           |
| `^-Space ^-Space`    | Set the "mark" in the editing region and make the region "active", i.e. highlighted                        |
| `^G`                 | De-activate the region (i.e. make it not highlighted)                                                      |
| `^X^X`               | Exchange the current position with the mark                                                                |
| **Editing**          |                                                                                                            |
| Backspace, `^H`      | Delete the previous character, or the whole region when it's active                                        |
| Delete, `^D`         | Forward delete one character (when buffer has text)                                                        |
| meta-Backspace       | Delete the previous word                                                                                   |
| `meta-d`             | Forward delete the next word                                                                               |
| `^W`                 | Delete previous text up to the nearest whitespace                                                          |
| `meta-w`             | Copy the current region in the kill ring                                                                   |
| `meta-W`             | "Kill" the current region, placing the text in the kill ring                                               |
| `^U`                 | "Kill" to beginning of line, placing the text in the kill ring                                             |
| `^K`                 | "Kill" to end of line, placing the text in the kill ring                                                   |
| `^Y`                 | "Yank" insert the text from the kill ring                                                                  |
| `meta-y`             | Replace a previously yanked text with an older entry from the kill ring                                    |
| `^T`                 | Transpose the characters about the cursor                                                                  |
| `meta-Up arrow`      | Transpose current line with line above                                                                     |
| `meta-Down arrow`    | Transpose current line with line below                                                                     |
| `meta-u`             | Change the next word to uppercase                                                                          |
| `meta-c`             | Change the next word to titlecase                                                                          |
| `meta-l`             | Change the next word to lowercase                                                                          |
| `^/`, `^_`           | Undo previous editing action                                                                               |
| `^Q`                 | Write a number in REPL and press `^Q` to open editor at corresponding stackframe or method                 |
| `meta-Left Arrow`    | Indent the current line on the left                                                                        |
| `meta-Right Arrow`   | Indent the current line on the right                                                                       |
| `meta-.`             | Insert last word from previous history entry                                                               |
| `meta-e`             | Edit the current input in an editor                                                                        |

### Customizing keybindings

Les raccourcis clavier du REPL de Julia peuvent être entièrement personnalisés selon les préférences d'un utilisateur en passant un dictionnaire à `REPL.setup_interface`. Les clés de ce dictionnaire peuvent être des caractères ou des chaînes. La clé `'*'` fait référence à l'action par défaut. Les raccourcis Control plus le caractère `x` sont indiqués par `"^x"`. Meta plus `x` peut être écrit `"\\M-x"` ou `"\ex"`, et Control plus `x` peut être écrit `"\\C-x"` ou `"^x"`. Les valeurs de la carte de touches personnalisée doivent être `nothing` (indiquant que l'entrée doit être ignorée) ou des fonctions qui acceptent la signature `(PromptState, AbstractREPL, Char)`. La fonction `REPL.setup_interface` doit être appelée avant que le REPL ne soit initialisé, en enregistrant l'opération avec [`atreplinit`](@ref). Par exemple, pour lier les touches fléchées haut et bas pour naviguer dans l'historique sans recherche par préfixe, on pourrait mettre le code suivant dans `~/.julia/config/startup.jl` :

```julia
import REPL
import REPL.LineEdit

const mykeys = Dict{Any,Any}(
    # Up Arrow
    "\e[A" => (s,o...)->(LineEdit.edit_move_up(s) || LineEdit.history_prev(s, LineEdit.mode(s).hist)),
    # Down Arrow
    "\e[B" => (s,o...)->(LineEdit.edit_move_down(s) || LineEdit.history_next(s, LineEdit.mode(s).hist))
)

function customize_keys(repl)
    repl.interface = REPL.setup_interface(repl; extra_repl_keymap = mykeys)
end

atreplinit(customize_keys)
```

Les utilisateurs doivent se référer à `LineEdit.jl` pour découvrir les actions disponibles sur l'entrée de clé.

## Tab completion

Dans les modes Julian, pkg et help du REPL, on peut entrer les premiers caractères d'une fonction ou d'un type, puis appuyer sur la touche tab pour obtenir une liste de toutes les correspondances :

```julia-repl
julia> x[TAB]
julia> xor
```

Dans certains cas, il ne complète qu'une partie du nom, jusqu'à la prochaine ambiguïté :

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

Si vous appuyez à nouveau sur tab, vous obtiendrez la liste des éléments qui pourraient compléter cela :

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

Lorsque qu'un seul résultat de complétion par tabulation complet est disponible à la fin d'une ligne d'entrée et que 2 caractères ou plus ont été tapés, un indice de la complétion s'affichera dans une couleur plus claire. Cela peut être désactivé via `Base.active_repl.options.hint_tab_completes = false`.

!!! compat "Julia 1.11"
    L'auto-complétion par tabulation a été ajoutée dans Julia 1.11


Comme d'autres composants du REPL, la recherche est sensible à la casse :

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

La touche tab peut également être utilisée pour substituer les symboles mathématiques LaTeX par leurs équivalents Unicode, et obtenir une liste des correspondances LaTeX également :

```julia-repl
julia> \pi[TAB]
julia> π
π = 3.1415926535897...

julia> e\_1[TAB] = [1,0]
julia> e₁ = [1,0]
2-element Array{Int64,1}:
 1
 0

julia> e\^1[TAB] = [1 0]
julia> e¹ = [1 0]
1×2 Array{Int64,2}:
 1  0

julia> \sqrt[TAB]2     # √ is equivalent to the sqrt function
julia> √2
1.4142135623730951

julia> \hbar[TAB](h) = h / 2\pi[TAB]
julia> ħ(h) = h / 2π
ħ (generic function with 1 method)

julia> \h[TAB]
\hat              \hermitconjmatrix  \hkswarow          \hrectangle
\hatapprox        \hexagon           \hookleftarrow     \hrectangleblack
\hbar             \hexagonblack      \hookrightarrow    \hslash
\heartsuit        \hksearow          \house             \hspace

julia> α="\alpha[TAB]"   # LaTeX completion also works in strings
julia> α="α"
```

Une liste complète des complétions par tabulation peut être trouvée dans la section [Unicode Input](@ref) du manuel.

L'achèvement des chemins fonctionne pour les chaînes et le mode shell de Julia :

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

Les clés du dictionnaire peuvent également être complétées par tabulation :

```julia-repl
julia> foo = Dict("qwer1"=>1, "qwer2"=>2, "asdf"=>3)
Dict{String,Int64} with 3 entries:
  "qwer2" => 2
  "asdf"  => 3
  "qwer1" => 1

julia> foo["q[TAB]

"qwer1" "qwer2"
julia> foo["qwer
```

La complétion par tabulation peut également aider à compléter les champs :

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

Les champs pour la sortie des fonctions peuvent également être complétés :

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

La complétion des champs pour la sortie des fonctions utilise l'inférence de type, et elle ne peut suggérer des champs que si la fonction est stable en type.

La complétion par tabulation peut aider à l'exploration des méthodes disponibles correspondant aux arguments d'entrée :

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

Les mots-clés sont également affichés dans les méthodes suggérées après `;`, voir la ligne ci-dessous où `limit` et `keepempty` sont des arguments de mot-clé :

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

L'achèvement des méthodes utilise l'inférence de type et peut donc vérifier si les arguments correspondent même si les arguments proviennent de fonctions. La fonction doit être stable en termes de type pour que l'achèvement puisse supprimer les méthodes non correspondantes.

Si vous vous demandez quels méthodes peuvent être utilisées avec des types d'arguments particuliers, utilisez `?` comme nom de fonction. Cela montre un exemple de recherche de fonctions dans InteractiveUtils qui acceptent une seule chaîne :

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

Cette liste de méthodes dans le module `InteractiveUtils` qui peuvent être appelées sur une chaîne. Par défaut, cela exclut les méthodes où tous les arguments sont typés comme `Any`, mais vous pouvez également les voir en maintenant la touche SHIFT-TAB enfoncée au lieu de TAB :

```julia-repl
julia> InteractiveUtils.?("somefile")[SHIFT-TAB]
apropos(string) in REPL at REPL/src/docview.jl:796
clipboard(x) in InteractiveUtils at InteractiveUtils/src/clipboard.jl:64
code_llvm(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:221
code_native(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:243
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
edit(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:225
eval(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
include(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
less(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:274
report_bug(kind) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:391
separate_kwargs(args...; kwargs...) in InteractiveUtils at InteractiveUtils/src/macros.jl:7
```

Vous pouvez également utiliser `?("somefile")[TAB]` et parcourir tous les modules, mais les listes de méthodes peuvent être longues.

En omettant la parenthèse de fermeture, vous pouvez inclure des fonctions qui pourraient nécessiter des arguments supplémentaires :

```julia-repl
julia> using Mmap

help?> Mmap.?("file",[TAB]
Mmap.Anonymous(name::String, readonly::Bool, create::Bool) in Mmap at Mmap/src/Mmap.jl:16
mmap(file::AbstractString) in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}) where T<:Array in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
```

## Customizing Colors

Les couleurs utilisées par Julia et le REPL peuvent également être personnalisées. Pour changer la couleur de l'invite de commande Julia, vous pouvez ajouter quelque chose comme ce qui suit à votre fichier `~/.julia/config/startup.jl`, qui doit être placé dans votre répertoire personnel :

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

Les clés de couleur disponibles peuvent être vues en tapant `Base.text_colors` dans le mode d'aide du REPL. De plus, les entiers de 0 à 255 peuvent être utilisés comme clés de couleur pour les terminaux avec un support de 256 couleurs.

Vous pouvez également changer les couleurs pour les invites d'aide et de shell ainsi que pour le texte d'entrée et de réponse en définissant le champ approprié de `repl` dans la fonction `customize_colors` ci-dessus (respectivement, `help_color`, `shell_color`, `input_color` et `answer_color`). Pour ces deux derniers, assurez-vous que le champ `envcolors` est également défini sur false.

Il est également possible d'appliquer un formatage en gras en utilisant `Base.text_colors[:bold]` comme couleur. Par exemple, pour imprimer des réponses en police gras, on peut utiliser ce qui suit dans un fichier `~/.julia/config/startup.jl` :

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

Vous pouvez également personnaliser la couleur utilisée pour afficher les messages d'avertissement et d'information en définissant les variables d'environnement appropriées. Par exemple, pour afficher les messages d'erreur, d'avertissement et d'information respectivement en magenta, jaune et cyan, vous pouvez ajouter ce qui suit à votre fichier `~/.julia/config/startup.jl` :

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

Lorsque vous saisissez des expressions dans le REPL, elles sont par défaut évaluées dans le module `Main` ;

```julia-repl
julia> @__MODULE__
Main
```

Il est possible de changer ce module contextuel via la fonction `REPL.activate(m)` où `m` est un `Module` ou en tapant le module dans le REPL et en appuyant sur la combinaison de touches Alt-m avec le curseur sur le nom du module (Esc-m sur MacOS). Appuyer sur la combinaison de touches dans une invite vide bascule le contexte entre le module non-`Main` précédemment actif et `Main`. Le module actif est affiché dans l'invite (sauf s'il s'agit de `Main`) :

```julia-repl
julia> using REPL

julia> REPL.activate(Base)

(Base) julia> @__MODULE__
Base

(Base) julia> using REPL # Need to load REPL into Base module to use it

(Base) julia> REPL.activate(Main)

julia>

julia> Core<Alt-m> # using the keybinding to change module

(Core) julia>

(Core) julia> <Alt-m> # going back to Main via keybinding

julia>

julia> <Alt-m> # going back to previously-active Core via keybinding

(Core) julia>
```

Les fonctions qui prennent un argument de module optionnel utilisent souvent par défaut le module du contexte REPL. Par exemple, appeler `varinfo()` affichera les variables du module actif actuel :

```julia-repl
julia> module CustomMod
           export var, f
           var = 1
           f(x) = x^2
       end;

julia> REPL.activate(CustomMod)

(Main.CustomMod) julia> varinfo()
  name         size summary
  ––––––––– ––––––– ––––––––––––––––––––––––––––––––––
  CustomMod         Module
  f         0 bytes f (generic function with 1 method)
  var       8 bytes Int64
```

## Numbered prompt

Il est possible d'obtenir une interface similaire au REPL IPython et au notebook Mathematica avec des invites d'entrée numérotées et des préfixes de sortie. Cela se fait en appelant `REPL.numbered_prompt!()`. Si vous souhaitez que cela soit activé au démarrage, ajoutez

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

dans votre fichier `startup.jl`. Dans l'invite numérotée, la variable `Out[n]` (où `n` est un entier) peut être utilisée pour se référer à des résultats antérieurs :

```julia-repl
In [1]: 5 + 3
Out[1]: 8

In [2]: Out[1] + 5
Out[2]: 13

In [3]: Out
Out[3]: Dict{Int64, Any} with 2 entries:
  2 => 13
  1 => 8
```

!!! note
    Puisque toutes les sorties des évaluations REPL précédentes sont enregistrées dans la variable `Out`, il faut faire attention si l'on retourne de nombreux objets volumineux en mémoire comme des tableaux, car ils seront protégés de la collecte des ordures tant qu'une référence à eux reste dans `Out`. Si vous devez supprimer des références à des objets dans `Out`, vous pouvez effacer l'historique entier qu'il stocke avec `empty!(Out)`, ou effacer une entrée individuelle avec `Out[n] = nothing`.


## TerminalMenus

TerminalMenus est un sous-module du REPL Julia et permet de créer de petits menus interactifs discrets dans le terminal.

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

Le RadioMenu permet à l'utilisateur de sélectionner une option dans la liste. La fonction `request` affiche le menu interactif et retourne l'index du choix sélectionné. Si un utilisateur appuie sur 'q' ou `ctrl-c`, `request` renverra un `-1`.

```julia
# `pagesize` is the number of items to be displayed at a time.
#  The UI will scroll if the number of options is greater
#   than the `pagesize`
menu = RadioMenu(options, pagesize=4)

# `request` displays the menu and returns the index after the
#   user has selected a choice
choice = request("Choose your favorite fruit:", menu)

if choice != -1
    println("Your favorite fruit is ", options[choice], "!")
else
    println("Menu canceled.")
end

```

Veuillez fournir le contenu Markdown que vous souhaitez traduire.

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

Le MultiSelectMenu permet aux utilisateurs de sélectionner plusieurs choix dans une liste.

```julia
# here we use the default `pagesize` 10
menu = MultiSelectMenu(options)

# `request` returns a `Set` of selected indices
# if the menu us canceled (ctrl-c or q), return an empty set
choices = request("Select the fruits you like:", menu)

if length(choices) > 0
    println("You like the following fruits:")
    for i in choices
        println("  - ", options[i])
    end
else
    println("Menu canceled.")
end
```

Veuillez fournir le contenu Markdown que vous souhaitez traduire.

```
Select the fruits you like:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```

### Customization / Configuration

#### ConfiguredMenu subtypes

À partir de Julia 1.6, la méthode recommandée pour configurer les menus est via le constructeur. Par exemple, le menu de sélection multiple par défaut

```
julia> menu = MultiSelectMenu(options, pagesize=5);

julia> request(menu) # ASCII is used by default
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
   [X] orange
   [ ] grape
 > [X] strawberry
v  [ ] blueberry
```

peut plutôt être rendu avec des caractères de sélection et de navigation Unicode avec

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode);

julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   ⬚ apple
   ✓ orange
   ⬚ grape
 → ✓ strawberry
↓  ⬚ blueberry
```

Une configuration plus fine est également possible :

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode, checked="YEP!", unchecked="NOPE", cursor='⧐');

julia> request(menu)
julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   NOPE apple
   YEP! orange
   NOPE grape
 ⧐ YEP! strawberry
↓  NOPE blueberry
```

En plus de l'option `charset` globale, pour `RadioMenu`, les options configurables sont :

  * `cursor::Char='>'|'→'`: caractère à utiliser pour le curseur
  * `up_arrow::Char='^'|'↑'`: caractère à utiliser pour la flèche vers le haut
  * `down_arrow::Char='v'|'↓'`: caractère à utiliser pour la flèche vers le bas
  * `updown_arrow::Char='I'|'↕'`: caractère à utiliser pour la flèche haut/bas dans une page en une ligne
  * `scroll_wrap::Bool=false`: optionnellement faire un wrap-around au début/à la fin d'un menu
  * `ctrl_c_interrupt::Bool=true`: Si `false`, retourne vide sur ^C, si `true` lance InterruptException() sur ^C

`MultiSelectMenu` ajoute :

  * `checked::String="[X]"|"✓"`: chaîne à utiliser pour coché
  * `unchecked::String="[ ]"|"⬚")`: chaîne à utiliser pour non coché

Vous pouvez créer de nouveaux types de menus de votre propre choix. Les types dérivés de `TerminalMenus.ConfiguredMenu` configurent les options de menu au moment de la construction.

#### Legacy interface

Avant Julia 1.6, et toujours pris en charge dans Julia 1.x, on peut également configurer les menus en appelant `TerminalMenus.config()`.

## References

### REPL

```@docs
Base.atreplinit
```

### TerminalMenus

### Menus

```@docs
REPL.TerminalMenus.RadioMenu
REPL.TerminalMenus.MultiSelectMenu
```

#### Configuration

```@docs
REPL.TerminalMenus.Config
REPL.TerminalMenus.MultiSelectConfig
REPL.TerminalMenus.config
```

#### User interaction

```@docs
REPL.TerminalMenus.request
```

#### AbstractMenu extension interface

Tout sous-type de `AbstractMenu` doit être mutable et doit contenir les champs `pagesize::Int` et `pageoffset::Int`. Tout sous-type doit également implémenter les fonctions suivantes :

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

Il doit également implémenter soit `options` soit `numoptions` :

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

Si le sous-type n'a pas de champ nommé `selected`, il doit également implémenter

```@docs
REPL.TerminalMenus.selected
```

Les éléments suivants sont optionnels mais peuvent permettre une personnalisation supplémentaire :

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```

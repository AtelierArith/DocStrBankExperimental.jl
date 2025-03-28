# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    L'API pour StyledStrings et AnnotatedStrings est considérée comme expérimentale et est sujette à des modifications entre les versions de Julia.


## [Styling](@id stdlib-styledstrings-styling)

Lorsqu'on travaille avec des chaînes de caractères, le formatage et le style apparaissent souvent comme une préoccupation secondaire.

Par exemple, lorsque vous imprimez dans un terminal, vous pourriez vouloir saupoudrer [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters) dans la sortie. Lors de la sortie de constructions de style HTML (`<span style="...">`, etc.), cela sert un but similaire, et ainsi de suite. Il est possible d'insérer simplement les constructions de style brutes dans la chaîne à côté du contenu lui-même, mais il devient rapidement évident que ce n'est pas bien adapté à autre chose que les cas d'utilisation les plus basiques. Tous les terminaux ne prennent pas en charge les mêmes codes ANSI, les constructions de style doivent être soigneusement supprimées lors du calcul de la largeur du contenu déjà stylé, et cela avant même de commencer à gérer plusieurs formats de sortie.

Au lieu de laisser ce mal de tête être largement ressenti en aval, il est abordé de front par l'introduction d'un type de chaîne spécial ([`AnnotatedString`](@ref Base.AnnotatedString)). Ce type de chaîne enveloppe tout autre type [`AbstractString`](@ref) et permet d'appliquer des informations de formatage à des régions (par exemple, les caractères 1 à 7 sont en gras et rouges).

Les régions d'une chaîne sont stylisées en appliquant [`Face`](@ref StyledStrings.Face) (pensez à "police") à celles-ci — une structure qui contient des informations de style. Par commodité, les polices dans le dictionnaire global des polices (par exemple `shadow`) peuvent simplement être nommées au lieu de donner directement le `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`.

Avec ces capacités, nous fournissons également un moyen pratique de construire [`AnnotatedString`](@ref Base.AnnotatedString), détaillé dans [Styled String Literals](@ref stdlib-styledstring-literals).

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

Il est parfois utile de pouvoir conserver des métadonnées relatives à des régions d'une chaîne de caractères. Un [`AnnotatedString`](@ref Base.AnnotatedString) enveloppe une autre chaîne et permet d'annoter des régions avec des valeurs étiquetées (`:label => value`). Toutes les opérations de chaîne génériques sont appliquées à la chaîne sous-jacente. Cependant, lorsque cela est possible, les informations de style sont préservées. Cela signifie que vous pouvez manipuler un `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` — en prenant des sous-chaînes, en les remplissant, en les concaténant avec d'autres chaînes — et les annotations de métadonnées "viendront avec".

Ce type de chaîne est fondamental pour le [StyledStrings stdlib](@ref stdlib-styledstrings), qui utilise des annotations étiquetées `:face` pour contenir des informations de style.

Lors de la concaténation d'un [`AnnotatedString`](@ref Base.AnnotatedString), veillez à utiliser [`annotatedstring`](@ref StyledStrings.annotatedstring) au lieu de [`string`](@ref) si vous souhaitez conserver les annotations de chaîne.

```jldoctest
julia> str = AnnotatedString("hello there", [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
AnnotatedString{String}

julia> str2 = AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == annotatedstring(str, str2) # *-concatenation works
true
```

Les annotations d'un [`AnnotatedString`](@ref Base.AnnotatedString) peuvent être accessibles et modifiées via les fonctions [`annotations`](@ref StyledStrings.annotations) et [`annotate!`](@ref StyledStrings.annotate!).

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

Un [`Face`](@ref StyledStrings.Face) spécifie les détails d'une police de caractères dans laquelle le texte peut être mis en forme. Il couvre un ensemble d'attributs de base qui se généralisent bien à travers différents formats, à savoir :

  * `police`
  * `hauteur`
  * `poids`
  * `inclinaison`
  * `premier plan`
  * `arrière-plan`
  * `souligner`
  * `barré`
  * `inverse`
  * `hériter`

Pour des détails sur les formes particulières que prennent ces attributs, consultez la [`Face`](@ref StyledStrings.Face) docstring, mais ce qui est particulièrement intéressant est `inherit` car il vous permet de *hériter* des attributs d'autres `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`.

### The global faces dictionary

Pour rendre la référence à des styles particuliers plus pratique, il existe un `Dict{Symbol, Face}` global qui permet de référencer des [`Face`](@ref StyledStrings.Face) simplement par leur nom. Les packages peuvent ajouter des visages à ce dictionnaire via la fonction [`addface!`](@ref StyledStrings.addface!), et les visages chargés peuvent être facilement [customized](@ref stdlib-styledstrings-face-toml).

!!! warning "Appropriate face naming"
    Tout package enregistrant de nouveaux visages doit s'assurer qu'ils sont préfixés par le nom du package, c'est-à-dire suivre le format `mypackage_myface`. Cela est important pour la prévisibilité et pour éviter les conflits de noms.

    De plus, les packages devraient veiller à utiliser (et à introduire) des visages *sémantiques* (comme `code`) plutôt que des couleurs et styles directs (comme `cyan`). Cela est utile de plusieurs manières, en rendant l'intention d'utilisation plus évidente, en aidant à la composition et en rendant la personnalisation par l'utilisateur plus intuitive.


Il existe deux ensembles d'exemptions à la règle de préfixe de paquet :

  * l'ensemble des visages de base qui font partie de la valeur par défaut du dictionnaire des visages
  * faces introduits par la propre bibliothèque standard de Julia, à savoir `JuliaSyntaxHighlighting`

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

Les visages de base sont destinés à représenter une idée générale qui est largement applicable.

Pour définir un texte avec un certain attribut, nous avons les styles `gras`, `clair`, `italique`, `souligné`, `barré` et `inverse`.

Il existe également des noms pour les 16 couleurs terminales : `noir`, `rouge`, `vert`, `jaune`, `bleu`, `magenta`, `cyan`, `blanc`, `noir_clair`/`gris`, `rouge_clair`, `vert_clair`, `bleu_clair`, `magenta_clair`, `cyan_clair`, et `blanc_clair`.

Pour le texte ombragé (c'est-à-dire atténué mais présent), il y a la face `shadow`. Pour indiquer une région sélectionnée, il y a la face `region`. De même, pour l'accentuation et la mise en évidence, les faces `emphasis` et `highlight` sont définies. Il y a aussi `code` pour le texte de type code.

Pour indiquer visuellement la gravité des messages, les visages `error`, `warning`, `success`, `info`, `note` et `tip` sont définis.

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

Il est bon que les noms des visages dans le dictionnaire mondial des visages soient personnalisables. Le thème et l'esthétique sont agréables, et c'est également important pour des raisons d'accessibilité. Un fichier TOML peut être analysé en une liste de [`Face`](@ref StyledStrings.Face) spécifications qui sont fusionnées avec l'entrée préexistante dans le dictionnaire des visages.

Un [`Face`](@ref StyledStrings.Face) est représenté en TOML comme suit :

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

Par exemple, si le visage `shadow` est trop difficile à lire, il peut être éclairci comme ceci :

```toml
[shadow]
foreground = "white"
```

Lors de l'initialisation, le fichier `config/faces.toml` sous le premier dépôt Julia (généralement `~/.julia`) est chargé.

### Applying faces to a `AnnotatedString`

Par convention, les attributs `:face` d'un [`AnnotatedString`](@ref Base.AnnotatedString) contiennent des informations sur les [`Face`](@ref StyledStrings.Face) qui s'appliquent actuellement. Cela peut être donné sous plusieurs formes, comme un seul `Symbol` nommant un `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` dans le dictionnaire global des faces, un `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` lui-même, ou un vecteur de l'un ou l'autre.

Les méthodes `show(::IO, ::MIME"text/plain", ::AnnotatedString)` et `show(::IO, ::MIME"text/html", ::AnnotatedString)` examinent toutes deux les attributs `:face` et les fusionnent toutes ensemble lors de la détermination du style global.

Nous pouvons fournir des attributs `:face` à un `AnnotatedString` lors de la construction, les ajouter à la liste des propriétés par la suite, ou utiliser le pratique [Styled String literals](@ref stdlib-styledstring-literals).

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

Pour faciliter la construction de [`AnnotatedString`](@ref Base.AnnotatedString) avec [`Face`](@ref StyledStrings.Face) appliqués, le littéral de chaîne stylé [`styled"..."`](@ref @styled_str) permet d'exprimer facilement le contenu et les attributs ensemble via une grammaire personnalisée.

Dans un littéral [`styled"..."`](@ref @styled_str), les accolades sont considérées comme des caractères spéciaux et doivent être échappées dans une utilisation normale (`\{`, `\}`). Cela permet de les utiliser pour exprimer des annotations avec des constructions `{annotations...:text}` (imbriquées).

Le composant `annotations...` est une liste séparée par des virgules de trois types d'annotations.

  * Noms de visage
  * Expressions `Face` en ligne `(clé=val,...)`
  * `clé=valeur` paires

L'interpolation est possible partout sauf pour les clés de visage en ligne.

Pour plus d'informations sur la grammaire, consultez l'aide étendue de la docstring [`styled"..."`](@ref @styled_str).

En tant qu'exemple, nous pouvons démontrer la liste des visages intégrés mentionnés ci-dessus comme suit :

```julia-repl
julia> println(styled"
The basic font-style attributes are {bold:bold}, {light:light}, {italic:italic},
{underline:underline}, and {strikethrough:strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:
 {black:■} {red:■} {green:■} {yellow:■} {blue:■} {magenta:■} {cyan:■} {white:■}
 {bright_black:■} {bright_red:■} {bright_green:■} {bright_yellow:■} {bright_blue:■} {bright_magenta:■} {bright_cyan:■} {bright_white:■}

Since {code:bright_black} is effectively grey, we define two aliases for it:
{code:grey} and {code:gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the
{code:inverse} face, for example: {magenta:some {inverse:inverse} text}.

The intent-based basic faces are {shadow:shadow} (for dim but visible text),
{region:region} for selections, {emphasis:emphasis}, and {highlight:highlight}.
As above, {code:code} is used for code-like text.

Lastly, we have the 'message severity' faces: {error:error}, {warning:warning},
{success:success}, {info:info}, {note:note}, and {tip:tip}.

Remember that all these faces (and any user or package-defined ones) can
arbitrarily nest and overlap, {region,tip:like {bold,italic:so}}.")
```

```@raw comment
Documenter doesn't properly represent all the styling above, so I've converted it manually to HTML and LaTeX.
```

```@raw html
<pre>
 The basic font-style attributes are <span style="font-weight: 700;">bold</span>, <span style="font-weight: 300;">light</span>, <span style="font-style: italic;">italic</span>,
 <span style="text-decoration: underline;">underline</span>, and <span style="text-decoration: line-through">strikethrough</span>.

 In terms of color, we have named faces for the 16 standard terminal colors:
  <span style="color: #1c1a23;">■</span> <span style="color: #a51c2c;">■</span> <span style="color: #25a268;">■</span> <span style="color: #e5a509;">■</span> <span style="color: #195eb3;">■</span> <span style="color: #803d9b;">■</span> <span style="color: #0097a7;">■</span> <span style="color: #dddcd9;">■</span>
  <span style="color: #76757a;">■</span> <span style="color: #ed333b;">■</span> <span style="color: #33d079;">■</span> <span style="color: #f6d22c;">■</span> <span style="color: #3583e4;">■</span> <span style="color: #bf60ca;">■</span> <span style="color: #26c6da;">■</span> <span style="color: #f6f5f4;">■</span>

 Since <span style="color: #0097a7;">bright_black</span> is effectively grey, we define two aliases for it:
 <span style="color: #0097a7;">grey</span> and <span style="color: #0097a7;">gray</span> to allow for regional spelling differences.

 To flip the foreground and background colors of some text, you can use the
 <span style="color: #0097a7;">inverse</span> face, for example: <span style="color: #803d9b;">some </span><span style="background-color: #803d9b;">inverse</span><span style="color: #803d9b;"> text</span>.

 The intent-based basic faces are <span style="color: #76757a;">shadow</span> (for dim but visible text),
 <span style="background-color: #3a3a3a;">region</span> for selections, <span style="color: #195eb3;">emphasis</span>, and <span style="background-color: #195eb3;">highlight</span>.
 As above, <span style="color: #0097a7;">code</span> is used for code-like text.

 Lastly, we have the 'message severity' faces: <span style="color: #ed333b;">error</span>, <span style="color: #e5a509;">warning</span>,
 <span style="color: #25a268;">success</span>, <span style="color: #26c6da;">info</span>, <span style="color: #76757a;">note</span>, and <span style="color: #33d079;">tip</span>.

 Remember that all these faces (and any user or package-defined ones) can
 arbitrarily nest and overlap, <span style="color: #33d079;background-color: #3a3a3a;">like <span style="font-weight: 700;font-style: italic;">so</span></span>.</pre>
```

```@raw latex
\begingroup
\ttfamily
\setlength{\parindent}{0pt}
\setlength{\parskip}{\baselineskip}

The basic font-style attributes are {\fontseries{b}\selectfont bold}, {\fontseries{l}\selectfont light}, {\fontshape{it}\selectfont italic},\\
\underline{underline}, and {strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:\\
{\color[HTML]{1c1a23}\(\blacksquare\)} {\color[HTML]{a51c2c}\(\blacksquare\)} {\color[HTML]{25a268}\(\blacksquare\)}
{\color[HTML]{e5a509}\(\blacksquare\)} {\color[HTML]{195eb3}\(\blacksquare\)} {\color[HTML]{803d9b}\(\blacksquare\)}
{\color[HTML]{0097a7}\(\blacksquare\)} {\color[HTML]{dddcd9}\(\blacksquare\)} \\
{\color[HTML]{76757a}\(\blacksquare\)} {\color[HTML]{ed333b}\(\blacksquare\)} {\color[HTML]{33d079}\(\blacksquare\)} {\color[HTML]{f6d22c}\(\blacksquare\)} {\color[HTML]{3583e4}\(\blacksquare\)} {\color[HTML]{bf60ca}\(\blacksquare\)} {\color[HTML]{26c6da}\(\blacksquare\)} {\color[HTML]{f6f5f4}\(\blacksquare\)}

Since {\color[HTML]{0097a7}bright\_black} is effectively grey, we define two aliases for it:\\
{\color[HTML]{0097a7}grey} and {\color[HTML]{0097a7}gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the\\
{\color[HTML]{0097a7}inverse} face, for example: {\color[HTML]{803d9b}some \colorbox[HTML]{803d9b}{\color[HTML]{000000}inverse} text}.

The intent-based basic faces are {\color[HTML]{76757a}shadow} (for dim but visible text),\\
\colorbox[HTML]{3a3a3a}{region} for selections, {\color[HTML]{195eb3}emphasis}, and \colorbox[HTML]{195eb3}{highlight}.\\
As above, {\color[HTML]{0097a7}code} is used for code-like text.

Lastly, we have the 'message severity' faces: {\color[HTML]{ed333b}error}, {\color[HTML]{e5a509}warning},\\
{\color[HTML]{25a268}success}, {\color[HTML]{26c6da}info}, {\color[HTML]{76757a}note}, and {\color[HTML]{33d079}tip}.

Remember that all these faces (and any user or package-defined ones) can\\
arbitrarily nest and overlap, \colorbox[HTML]{3a3a3a}{\color[HTML]{33d079}like
  {\fontseries{b}\fontshape{it}\selectfont so}}.
\endgroup
```

## [API reference](@id stdlib-styledstrings-api)

### Styling and Faces

```@docs
StyledStrings.@styled_str
StyledStrings.styled
StyledStrings.Face
StyledStrings.addface!
StyledStrings.withfaces
StyledStrings.SimpleColor
StyledStrings.parse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.tryparse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.merge(::StyledStrings.Face, ::StyledStrings.Face)
```

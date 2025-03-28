# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    Die API für StyledStrings und AnnotatedStrings wird als experimentell betrachtet und kann sich zwischen den Julia-Versionen ändern.


## [Styling](@id stdlib-styledstrings-styling)

Beim Arbeiten mit Zeichenfolgen erscheinen Formatierung und Stil oft als sekundäre Anliegen.

Zum Beispiel, wenn Sie in ein Terminal drucken, möchten Sie möglicherweise [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters) in die Ausgabe streuen. Beim Ausgeben von HTML-Stil-Konstrukten (`<span style="...">`, usw.) dient dies einem ähnlichen Zweck, und so weiter. Es ist möglich, die rohen Stil-Konstrukte einfach in den String neben dem Inhalt selbst einzufügen, aber es wird schnell offensichtlich, dass dies nicht gut geeignet ist für anything but the most basic use cases. Nicht alle Terminals unterstützen die gleichen ANSI-Codes, die Stil-Konstrukte müssen mühsam entfernt werden, wenn die Breite bereits gestylter Inhalte berechnet wird, und das ist noch bevor Sie sich mit der Handhabung mehrerer Ausgabeformate befassen.

Statt dieses Kopfzerbrechen weit verbreitet downstream zu lassen, wird es direkt angegangen durch die Einführung eines speziellen String-Typs ([`AnnotatedString`](@ref Base.AnnotatedString)). Dieser String-Typ umschließt jeden anderen [`AbstractString`](@ref) Typ und ermöglicht es, Formatierungsinformationen auf Bereiche anzuwenden (z.B. sind die Zeichen 1 bis 7 fett und rot).

Regionen eines Strings werden gestylt, indem [`Face`](@ref StyledStrings.Face)s (denken Sie an "Schriftart") auf sie angewendet werden — eine Struktur, die Stylinginformationen enthält. Zur Vereinfachung können Schriftarten im globalen Schriftartenwörterbuch (z. B. `shadow`) einfach benannt werden, anstatt die `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` direkt anzugeben.

Neben diesen Fähigkeiten bieten wir auch eine bequeme Möglichkeit zum Erstellen von [`AnnotatedString`](@ref Base.AnnotatedString), die in [Styled String Literals](@ref stdlib-styledstring-literals) detailliert beschrieben ist.

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

Es ist manchmal nützlich, Metadaten zu Regionen eines Strings zu halten. Ein [`AnnotatedString`](@ref Base.AnnotatedString) umschließt einen anderen String und ermöglicht es, Regionen davon mit beschrifteten Werten (`:label => value`) zu annotieren. Alle generischen String-Operationen werden auf den zugrunde liegenden String angewendet. Wenn möglich, werden jedoch Stilinformationen beibehalten. Das bedeutet, dass Sie einen `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` manipulieren können — indem Sie Teilstrings entnehmen, sie auffüllen, sie mit anderen Strings verketten — und die Metadatenannotationen werden "mitkommen".

Dieser Stringtyp ist grundlegend für die [StyledStrings stdlib](@ref stdlib-styledstrings), die `:face`-beschriftete Annotationen verwendet, um Stilinformationen zu halten.

Beim Verketten von [`AnnotatedString`](@ref Base.AnnotatedString) achte darauf, [`annotatedstring`](@ref StyledStrings.annotatedstring) anstelle von [`string`](@ref) zu verwenden, wenn du die String-Anmerkungen beibehalten möchtest.

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

Die Anmerkungen eines [`AnnotatedString`](@ref Base.AnnotatedString) können über die Funktionen [`annotations`](@ref StyledStrings.annotations) und [`annotate!`](@ref StyledStrings.annotate!) zugegriffen und geändert werden.

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

Ein [`Face`](@ref StyledStrings.Face) spezifiziert Details einer Schriftart, in der Text gesetzt werden kann. Es umfasst eine Reihe grundlegender Attribute, die sich gut auf verschiedene Formate verallgemeinern lassen, nämlich:

  * `Schriftart`
  * `höhe`
  * `gewicht`
  * `schräg`
  * `Vordergrund`
  * `Hintergrund`
  * `unterstreichen`
  * `Durchgestrichen`
  * `invers`
  * `erben`

Für Details zu den spezifischen Formen, die diese Attribute annehmen, siehe die [`Face`](@ref StyledStrings.Face) Docstring, aber von besonderem Interesse ist `inherit`, da es Ihnen ermöglicht, Attribute von anderen `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`s *zu erben*.

### The global faces dictionary

Um das Verweisen auf bestimmte Stile bequemer zu gestalten, gibt es ein globales `Dict{Symbol, Face}`, das es ermöglicht, [`Face`](@ref StyledStrings.Face) einfach nur beim Namen zu nennen. Pakete können über die Funktion [`addface!`](@ref StyledStrings.addface!) Gesichter zu diesem Wörterbuch hinzufügen, und die geladenen Gesichter können leicht [customized](@ref stdlib-styledstrings-face-toml) werden.

!!! warning "Appropriate face naming"
    Jedes Paket, das neue Gesichter registriert, sollte sicherstellen, dass sie mit dem Paketnamen vorangestellt sind, d.h. dem Format `mypackage_myface` folgen. Dies ist wichtig für Vorhersehbarkeit und um Namenskonflikte zu vermeiden.

    Darüber hinaus sollten Pakete darauf achten, *semantische* Gesichter (wie `code`) anstelle von direkten Farben und Stilen (wie `cyan`) zu verwenden (und einzuführen). Dies ist in vielerlei Hinsicht hilfreich, von der Klarheit der Absicht in der Verwendung über die Unterstützung der Komponierbarkeit bis hin zur intuitiveren Benutzeranpassung.


Es gibt zwei Ausnahmen von der Paket-Präfixregel:

  * die Menge der grundlegenden Gesichter, die Teil des Standardwerts des Gesichter-Wörterbuchs sind
  * Gesichter, die von Julias eigener Standardbibliothek eingeführt wurden, nämlich `JuliaSyntaxHighlighting`

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

Basisgesichter sollen eine allgemeine Idee darstellen, die weit verbreitet anwendbar ist.

Für die Einstellung von Text mit einem bestimmten Attribut haben wir die Schriftarten `fett`, `leicht`, `kursiv`, `unterstrichen`, `durchgestrichen` und `inverse`.

Es gibt auch benannte Farben für die 16 Terminalfarben: `schwarz`, `rot`, `grün`, `gelb`, `blau`, `magenta`, `cyan`, `weiß`, `hellschwarz`/`grau`, `hellrot`, `hellgrün`, `hellblau`, `hellmagenta`, `hellcyan` und `hellweiß`.

Für schattierten Text (d.h. gedimmt, aber vorhanden) gibt es das `shadow`-Gesicht. Um einen ausgewählten Bereich anzuzeigen, gibt es das `region`-Gesicht. Ähnlich für Betonung und Hervorhebung sind die `emphasis`- und `highlight`-Gesichter definiert. Es gibt auch `code` für codeähnlichen Text.

Um die Schwere von Nachrichten visuell anzuzeigen, sind die Gesichter `error`, `warning`, `success`, `info`, `note` und `tip` definiert.

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

Es ist gut, dass die Namen in dem globalen Gesichtswörterbuch anpassbar sind. Themen und Ästhetik sind schön, und es ist auch aus Gründen der Barrierefreiheit wichtig. Eine TOML-Datei kann in eine Liste von [`Face`](@ref StyledStrings.Face) Spezifikationen geparst werden, die mit dem bereits vorhandenen Eintrag im Gesichtswörterbuch zusammengeführt werden.

Ein [`Face`](@ref StyledStrings.Face) wird in TOML wie folgt dargestellt:

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

Wenn zum Beispiel das `shadow`-Gesicht zu schwer zu lesen ist, kann es so heller gemacht werden:

```toml
[shadow]
foreground = "white"
```

Bei der Initialisierung wird die Datei `config/faces.toml` im ersten Julia-Depot (normalerweise `~/.julia`) geladen.

### Applying faces to a `AnnotatedString`

Nach Konvention enthalten die `:face`-Attribute eines [`AnnotatedString`](@ref Base.AnnotatedString) Informationen über die [`Face`](@ref StyledStrings.Face)s, die derzeit gelten. Dies kann in mehreren Formen angegeben werden, als ein einzelnes `Symbol`, das einen `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` im globalen Gesichtswörterbuch benennt, ein `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` selbst oder ein Vektor von beidem.

Die `show(::IO, ::MIME"text/plain", ::AnnotatedString)` und `show(::IO, ::MIME"text/html", ::AnnotatedString)` Methoden betrachten beide die `:face` Attribute und fügen sie zusammen, um die gesamte Formatierung zu bestimmen.

Wir können `:face`-Attribute während der Konstruktion zu einem `AnnotatedString` hinzufügen, sie anschließend zur Eigenschaftenliste hinzufügen oder die praktische [Styled String literals](@ref stdlib-styledstring-literals) verwenden.

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

Um den Bau von [`AnnotatedString`](@ref Base.AnnotatedString) zu erleichtern, mit [`Face`](@ref StyledStrings.Face), ermöglicht der [`styled"..."`](@ref @styled_str) formatierte String-Literal, dass der Inhalt und die Attribute zusammen über eine benutzerdefinierte Grammatik leicht ausgedrückt werden können.

Innerhalb eines [`styled"..."`](@ref @styled_str) Literals werden geschweifte Klammern als Sonderzeichen betrachtet und müssen in der normalen Verwendung escaped werden (`\{`, `\}`). Dies ermöglicht es, sie zu verwenden, um Annotationen mit (verschachtelbaren) `{annotations...:text}` Konstrukten auszudrücken.

Die `annotations...`-Komponente ist eine durch Kommas getrennte Liste von drei Arten von Annotationen.

  * Gesichtsnamen
  * Inline `Gesicht` Ausdrücke `(key=val,...)`
  * `key=value` Paare

Interpolation ist überall möglich, außer bei Inline-Gesichtsschlüsseln.

Für weitere Informationen zur Grammatik siehe die erweiterte Hilfe des [`styled"..."`](@ref @styled_str) Docstring.

Als Beispiel können wir die oben genannten integrierten Gesichter wie folgt demonstrieren:

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

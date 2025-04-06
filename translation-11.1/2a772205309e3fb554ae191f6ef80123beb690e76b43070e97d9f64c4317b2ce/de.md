```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

Dieser Abschnitt beschreibt Julias Markdown-Syntax, die durch die Markdown-Standardbibliothek aktiviert wird. Die folgenden Markdown-Elemente werden unterstützt:

## Inline elements

Hier bezieht sich "inline" auf Elemente, die innerhalb von Textblöcken, d.h. Absätzen, gefunden werden können. Dazu gehören die folgenden Elemente.

### Bold

Um Wörter mit zwei Sternchen, `**`, zu umgeben, um den eingeschlossenen Text fett darzustellen.

```
A paragraph containing a **bold** word.
```

### Italics

Um Wörter kursiv darzustellen, umgeben Sie sie mit einem Sternchen, `*`.

```
A paragraph containing an *italicized* word.
```

### Literals

Umgeben Sie den Text, der genau so angezeigt werden soll, wie er geschrieben ist, mit einfachen Backticks, ``` ` ```.

```
A paragraph containing a `literal` word.
```

Literale sollten verwendet werden, wenn man Text schreibt, der sich auf Namen von Variablen, Funktionen oder anderen Teilen eines Julia-Programms bezieht.

!!! tip
    Um ein Backtick-Zeichen innerhalb von literalem Text einzufügen, verwenden Sie drei Backticks anstelle von einem, um den Text einzuschließen.

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    Durch Erweiterung kann jede ungerade Anzahl von Backticks verwendet werden, um eine geringere Anzahl von Backticks einzuschließen.


### $\LaTeX$

Um Text, der als Mathematik angezeigt werden soll, mit der $\LaTeX$-Syntax zu umgeben, verwenden Sie doppelte Backticks, ``` `` ```.

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    Wie bei Literalen im vorherigen Abschnitt, wenn literale Backticks innerhalb von doppelten Backticks geschrieben werden müssen, verwenden Sie eine gerade Anzahl größer als zwei. Beachten Sie, dass, wenn ein einzelner literaler Backtick innerhalb von $\LaTeX$-Markup enthalten sein muss, zwei umschließende Backticks ausreichen.


!!! note
    Das `\`-Zeichen sollte angemessen escaped werden, wenn der Text in einen Julia-Quellcode eingebettet ist, zum Beispiel ```"``\\LaTeX``-Syntax in einem Docstring."```, da es als Stringliteral interpretiert wird. Alternativ ist es möglich, um das Escapen zu vermeiden, das `raw`-String-Makro zusammen mit dem `@doc`-Makro zu verwenden:

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

Links zu externen oder internen Zielen können mit der folgenden Syntax geschrieben werden, wobei der Text in eckigen Klammern, `[ ]`, der Name des Links ist und der Text in runden Klammern, `( )`, die URL ist.

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

Es ist auch möglich, Querverweise zu anderen dokumentierten Funktionen/Methoden/Variablen innerhalb der Julia-Dokumentation selbst hinzuzufügen. Zum Beispiel:

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

Dies wird einen Link in den generierten Dokumenten zur [`parse`](@ref)-Dokumentation erstellen (die weitere Informationen darüber enthält, was diese Funktion tatsächlich tut), und zur [`nothing`](@ref)-Dokumentation. Es ist gut, Querverweise auf mutierende/nicht mutierende Versionen einer Funktion einzufügen oder einen Unterschied zwischen zwei ähnlich aussehenden Funktionen hervorzuheben.

!!! note
    Die obige Querverweisung ist *kein* Markdown-Feature und basiert auf [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl), das verwendet wird, um die Basisdokumentation von Julia zu erstellen.


### Footnote references

Benannte und nummerierte Fußnotenverweise können mit der folgenden Syntax geschrieben werden. Ein Fußnotenname muss ein einzelnes alphanumerisches Wort ohne Interpunktion sein.

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    Der Text, der mit einer Fußnote verbunden ist, kann überall auf derselben Seite wie der Fußnotenverweis geschrieben werden. Die Syntax, die verwendet wird, um den Fußnotentext zu definieren, wird im Abschnitt [Footnotes](@ref) unten besprochen.


## Toplevel elements

Die folgenden Elemente können entweder auf der "obersten" Ebene eines Dokuments oder innerhalb eines anderen "obersten" Elements geschrieben werden.

### Paragraphs

Ein Absatz ist ein Block aus einfachem Text, der möglicherweise eine beliebige Anzahl von Inline-Elementen enthält, die im Abschnitt [Inline elements](@ref) oben definiert sind, mit einer oder mehreren Leerzeilen darüber und darunter.

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

Ein Dokument kann in verschiedene Abschnitte unter Verwendung von Überschriften unterteilt werden. Überschriften verwenden die folgende Syntax:

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

Eine Kopfzeile kann jede Inline-Syntax enthalten, genau wie ein Absatz.

!!! tip
    Versuchen Sie, innerhalb eines einzelnen Dokuments nicht zu viele Ebenen von Überschriften zu verwenden. Ein stark verschachteltes Dokument kann darauf hindeuten, dass es notwendig ist, es umzugestalten oder in mehrere Seiten zu unterteilen, die separate Themen behandeln.


### Code blocks

Quellcode kann als literaler Block angezeigt werden, indem man vier Leerzeichen oder einen Tabulator einfügt, wie im folgenden Beispiel gezeigt.

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

Zusätzlich können Codeblöcke mit dreifachen Backticks umschlossen werden, wobei eine optionale "Sprache" angegeben werden kann, um zu spezifizieren, wie ein Codeblock hervorgehoben werden soll.

````
A code block without a "language":

```
function func(x)
    # ...
end
```

and another one with the "language" specified as `julia`:

```julia
function func(x)
    # ...
end
```
````

!!! note
    "Umzäunte" Codeblöcke, wie im letzten Beispiel gezeigt, sollten gegenüber eingerückten Codeblöcken bevorzugt werden, da es keine Möglichkeit gibt, anzugeben, in welcher Sprache ein eingerückter Codeblock geschrieben ist.


### Block quotes

Text von externen Quellen, wie Zitate aus Büchern oder Websites, kann mit `>` Zeichen, die jeder Zeile des Zitats vorangestellt sind, zitiert werden, wie folgt.

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

Hinweis: Nach dem `>`-Zeichen muss auf jeder Zeile ein einzelner Leerraum erscheinen. Zitatblöcke können selbst andere Top-Level- oder Inline-Elemente enthalten.

### Images

Die Syntax für Bilder ist ähnlich der oben erwähnten Link-Syntax. Das Voranstellen eines `!`-Zeichens zu einem Link zeigt ein Bild von der angegebenen URL an, anstatt einen Link dazu.

```julia
![alternative text](link/to/image.png)
```

### Lists

Ungeordnete Listen können erstellt werden, indem jedem Element in einer Liste entweder `*`, `+` oder `-` vorangestellt wird.

```
A list of items:

  * item one
  * item two
  * item three
```

Beachte die zwei Leerzeichen vor jedem `*` und das einzelne Leerzeichen danach.

Listen können andere geschachtelte Hauptelemente wie Listen, Codeblöcke oder Zitatblöcke enthalten. Zwischen jedem Listenpunkt sollte eine Leerzeile gelassen werden, wenn Hauptelemente innerhalb einer Liste enthalten sind.

```
Another list:

  * item one

  * item two

    ```
    f(x) = x
    ```

  * And a sublist:

      + sub-item one
      + sub-item two
```

!!! note
    Der Inhalt jedes Elements in der Liste muss mit der ersten Zeile des Elements ausgerichtet sein. Im obigen Beispiel muss der eingezäunte Codeblock um vier Leerzeichen eingerückt werden, um mit dem `i` in `item two` auszurichten.


Nummerierte Listen werden erstellt, indem das "Aufzählungszeichen", entweder `*`, `+` oder `-`, durch eine positive ganze Zahl gefolgt von entweder `.` oder `)` ersetzt wird.

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

Eine geordnete Liste kann mit einer anderen Zahl als eins beginnen, wie in der zweiten Liste des obigen Beispiels, wo sie mit fünf nummeriert ist. Wie bei ungeordneten Listen können geordnete Listen geschachtelte Hauptelemente enthalten.

### Display equations

Große $\LaTeX$-Gleichungen, die nicht inline in einen Absatz passen, können als Anzeige-Gleichungen mit einem eingezäunten Codeblock mit der "Sprache" `math` geschrieben werden, wie im folgenden Beispiel.

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

Diese Syntax ist mit der Inline-Syntax für [Footnote references](@ref) gekoppelt. Stellen Sie sicher, dass Sie auch diesen Abschnitt lesen.

Fußnotentext wird mit der folgenden Syntax definiert, die der Syntax für Fußnotenzeichen ähnlich ist, abgesehen von dem `:`-Zeichen, das dem Fußnotensymbol angehängt wird.

```
[^1]: Numbered footnote text.

[^note]:

    Named footnote text containing several toplevel elements
    indented by 4 spaces or one tab.

      * item one
      * item two
      * item three

    ```julia
    function func(x)
        # ...
    end
    ```
```

!!! note
    Es werden keine Überprüfungen während des Parsings durchgeführt, um sicherzustellen, dass alle Fußnotenverweise passende Fußnoten haben.


### Horizontal rules

Der Äquivalent eines `<hr>` HTML-Tags kann mit drei Bindestrichen (`---`) erreicht werden. Zum Beispiel:

```
Text above the line.

---

And text below the line.
```

### Tables

Einfache Tabellen können mit der unten beschriebenen Syntax geschrieben werden. Beachten Sie, dass Markdown-Tabellen eingeschränkte Funktionen haben und keine geschachtelten Hauptelemente enthalten können, im Gegensatz zu anderen oben besprochenen Elementen – nur Inline-Elemente sind erlaubt. Tabellen müssen immer eine Kopfzeile mit Spaltennamen enthalten. Zellen dürfen nicht mehrere Zeilen oder Spalten der Tabelle überspannen.

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    Wie im obigen Beispiel dargestellt, muss jede Spalte von `|`-Zeichen vertikal ausgerichtet sein.

    Ein `:`-Zeichen an einem Ende des Spaltenüberschrift-Trenners (der Zeile mit `-`-Zeichen) gibt an, ob die Zeile linksbündig, rechtsbündig oder (wenn `:` an beiden Enden erscheint) zentriert ist. Das Weglassen von `:`-Zeichen führt standardmäßig zu einer rechtsbündigen Ausrichtung der Spalte.


### Admonitions

Besonders formatierte Blöcke, die als Hinweise bekannt sind, können verwendet werden, um bestimmte Bemerkungen hervorzuheben. Sie können mit der folgenden `!!!` Syntax definiert werden:

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

Das erste Wort nach `!!!` erklärt die Art der Warnung. Es gibt standardisierte Warnungstypen, die eine spezielle Formatierung erzeugen sollten. Nämlich (in absteigender Reihenfolge der Schwere): `danger`, `warning`, `info`/`note` und `tip`.

Sie können auch Ihre eigenen Hinweistypen verwenden, solange der Typname nur aus Kleinbuchstaben (a-z) besteht. Zum Beispiel könnten Sie einen `terminology`-Block wie diesen haben:

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

Es sei denn, der Code, der das Markdown rendert, behandelt diesen speziellen Hinweistyp besonders, erhält er das Standardstyling.

Ein benutzerdefinierter Titel für das Feld kann als Zeichenfolge (in doppelten Anführungszeichen) nach dem Typ der Anmerkung angegeben werden. Wenn kein Titeltext nach dem Typ der Anmerkung angegeben ist, wird der Typname als Titel verwendet (z. B. `"Hinweis"` für die `note`-Anmerkung).

Ermahnungen können, wie die meisten anderen Hauptelemente, andere Hauptelemente enthalten (z. B. Listen, Bilder).

## [Markdown String Literals](@id stdlib-markdown-literals)

Das `md""`-Makro ermöglicht es Ihnen, Markdown-Strings direkt in Ihren Julia-Code einzufügen. Dieses Makro wurde entwickelt, um die Einbindung von Markdown-formatiertem Text in Ihre Julia-Quelltexte zu vereinfachen.

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

Julias Markdown unterstützt die Interpolation auf eine sehr ähnliche Weise wie grundlegende Zeichenfolgenliterale, mit dem Unterschied, dass das Objekt selbst im Markdown-Baum gespeichert wird (anstatt es in eine Zeichenfolge umzuwandeln). Wenn der Markdown-Inhalt gerendert wird, werden die üblichen `show`-Methoden aufgerufen, und diese können wie gewohnt überschrieben werden. Dieses Design ermöglicht es, den Markdown mit beliebig komplexen Funktionen (wie Referenzen) zu erweitern, ohne die grundlegende Syntax zu überladen.

Im Prinzip kann der Markdown-Parser selbst auch beliebig durch Pakete erweitert werden, oder es kann eine völlig benutzerdefinierte Variante von Markdown verwendet werden, aber dies sollte im Allgemeinen unnötig sein.

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```

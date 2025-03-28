```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

Cette section décrit la syntaxe Markdown de Julia, qui est activée par la bibliothèque standard Markdown. Les éléments Markdown suivants sont pris en charge :

## Inline elements

Ici, "inline" fait référence aux éléments qui peuvent être trouvés dans des blocs de texte, c'est-à-dire des paragraphes. Cela inclut les éléments suivants.

### Bold

Entourez les mots avec deux astérisques, `**`, pour afficher le texte contenu en gras.

```
A paragraph containing a **bold** word.
```

### Italics

Entourez les mots d'un astérisque, `*`, pour afficher le texte contenu en italique.

```
A paragraph containing an *italicized* word.
```

### Literals

Entourez le texte qui doit être affiché exactement comme écrit avec des accents graves simples, ``` ` ```.

```
A paragraph containing a `literal` word.
```

Les littéraux doivent être utilisés lors de l'écriture de texte qui fait référence aux noms de variables, de fonctions ou d'autres parties d'un programme Julia.

!!! tip
    Pour inclure un caractère de backtick dans un texte littéral, utilisez trois backticks plutôt qu'un pour entourer le texte.

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    Par extension, tout nombre impair de backticks peut être utilisé pour encadrer un nombre inférieur de backticks.


### $\LaTeX$

Entourez le texte qui doit être affiché comme des mathématiques en utilisant la syntaxe $\LaTeX$ avec des doubles barres obliques inverses, ``` `` ```.

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    Comme pour les littéraux dans la section précédente, si des backticks littéraux doivent être écrits dans des doubles backticks, utilisez un nombre pair supérieur à deux. Notez que si un seul backtick littéral doit être inclus dans le balisage $\LaTeX$, alors deux backticks englobants suffisent.


!!! note
    Le caractère `\` doit être échappé de manière appropriée si le texte est intégré dans un code source Julia, par exemple, ```"``\\LaTeX`` syntaxe dans une docstring."```, car il est interprété comme un littéral de chaîne. Alternativement, afin d'éviter l'échappement, il est possible d'utiliser la macro de chaîne `raw` avec la macro `@doc` :

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

Les liens vers des cibles externes ou internes peuvent être écrits en utilisant la syntaxe suivante, où le texte encadré par des crochets, `[ ]`, est le nom du lien et le texte encadré par des parenthèses, `( )`, est l'URL.

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

Il est également possible d'ajouter des références croisées à d'autres fonctions/méthodes/variables documentées dans la documentation Julia elle-même. Par exemple :

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

Cela créera un lien dans la documentation générée vers la documentation [`parse`](@ref) (qui contient plus d'informations sur ce que cette fonction fait réellement), et vers la documentation [`nothing`](@ref). Il est bon d'inclure des références croisées aux versions mutantes/non mutantes d'une fonction, ou de mettre en évidence une différence entre deux fonctions semblant similaires.

!!! note
    Le renvoi croisé ci-dessus n'est *pas* une fonctionnalité Markdown et repose sur [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl), qui est utilisé pour construire la documentation de base de Julia.


### Footnote references

Les références de notes de bas de page nommées et numérotées peuvent être écrites en utilisant la syntaxe suivante. Un nom de note de bas de page doit être un mot alphanumérique unique ne contenant aucune ponctuation.

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    Le texte associé à une note de bas de page peut être écrit n'importe où dans la même page que la référence de la note de bas de page. La syntaxe utilisée pour définir le texte de la note de bas de page est discutée dans la section [Footnotes](@ref) ci-dessous.


## Toplevel elements

Les éléments suivants peuvent être écrits soit au "niveau supérieur" d'un document, soit à l'intérieur d'un autre élément "niveau supérieur".

### Paragraphs

Un paragraphe est un bloc de texte brut, pouvant contenir un nombre quelconque d'éléments en ligne définis dans la section [Inline elements](@ref) ci-dessus, avec une ou plusieurs lignes vides au-dessus et en dessous.

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

Un document peut être divisé en différentes sections à l'aide de titres. Les titres utilisent la syntaxe suivante :

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

Une ligne d'en-tête peut contenir n'importe quelle syntaxe en ligne de la même manière qu'un paragraphe peut.

!!! tip
    Essayez d'éviter d'utiliser trop de niveaux de titres dans un seul document. Un document fortement imbriqué peut indiquer un besoin de le restructurer ou de le diviser en plusieurs pages couvrant des sujets distincts.


### Code blocks

Le code source peut être affiché sous forme de bloc littéral en utilisant une indentation de quatre espaces ou d'une tabulation comme montré dans l'exemple suivant.

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

De plus, les blocs de code peuvent être encadrés à l'aide de triples accents graves avec un "langage" optionnel pour spécifier comment un bloc de code doit être mis en évidence.

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
    Les blocs de code "encadrés", comme montré dans le dernier exemple, doivent être préférés aux blocs de code indentés car il n'est pas possible de spécifier dans quel langage un bloc de code indenté est écrit.


### Block quotes

Le texte provenant de sources externes, telles que des citations de livres ou de sites Web, peut être cité en utilisant des caractères `>` ajoutés au début de chaque ligne de la citation comme suit.

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

Notez qu'un seul espace doit apparaître après le caractère `>` sur chaque ligne. Les blocs cités peuvent eux-mêmes contenir d'autres éléments de niveau supérieur ou des éléments en ligne.

### Images

La syntaxe pour les images est similaire à la syntaxe des liens mentionnée ci-dessus. En ajoutant un caractère `!` devant un lien, une image sera affichée à partir de l'URL spécifiée plutôt qu'un lien vers celle-ci.

```julia
![alternative text](link/to/image.png)
```

### Lists

Les listes non ordonnées peuvent être écrites en préfixant chaque élément d'une liste avec soit `*`, `+`, ou `-`.

```
A list of items:

  * item one
  * item two
  * item three
```

Notez les deux espaces avant chaque `*` et l'espace simple après chacun d'eux.

Les listes peuvent contenir d'autres éléments de niveau supérieur imbriqués tels que des listes, des blocs de code ou des blocs de citation. Une ligne vide doit être laissée entre chaque élément de la liste lors de l'inclusion de tout élément de niveau supérieur dans une liste.

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
    Le contenu de chaque élément de la liste doit s'aligner avec la première ligne de l'élément. Dans l'exemple ci-dessus, le bloc de code délimité doit être indenté de quatre espaces pour s'aligner avec le `i` dans `élément deux`.


Les listes ordonnées sont écrites en remplaçant le caractère "puce", soit `*`, `+` ou `-`, par un entier positif suivi soit de `.` soit de `)`.

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

Une liste ordonnée peut commencer par un numéro autre que un, comme dans la deuxième liste de l'exemple ci-dessus, où elle est numérotée à partir de cinq. Comme avec les listes non ordonnées, les listes ordonnées peuvent contenir des éléments de niveau supérieur imbriqués.

### Display equations

De grandes équations $\LaTeX$ qui ne s'intègrent pas en ligne dans un paragraphe peuvent être écrites sous forme d'équations affichées en utilisant un bloc de code délimité avec le "langage" `math` comme dans l'exemple ci-dessous.

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

Cette syntaxe est associée à la syntaxe en ligne pour [Footnote references](@ref). Assurez-vous de lire également cette section.

Le texte de la note de bas de page est défini en utilisant la syntaxe suivante, qui est similaire à la syntaxe de référence de note de bas de page, à l'exception du caractère `:` qui est ajouté à l'étiquette de la note de bas de page.

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
    Aucun contrôle n'est effectué lors de l'analyse pour s'assurer que toutes les références de notes de bas de page ont des notes de bas de page correspondantes.


### Horizontal rules

L'équivalent d'une balise HTML `<hr>` peut être obtenu en utilisant trois tirets (`---`). Par exemple :

```
Text above the line.

---

And text below the line.
```

### Tables

Les tables de base peuvent être écrites en utilisant la syntaxe décrite ci-dessous. Notez que les tables markdown ont des fonctionnalités limitées et ne peuvent pas contenir d'éléments de niveau supérieur imbriqués contrairement aux autres éléments discutés ci-dessus – seuls les éléments en ligne sont autorisés. Les tables doivent toujours contenir une ligne d'en-tête avec des noms de colonnes. Les cellules ne peuvent pas s'étendre sur plusieurs lignes ou colonnes de la table.

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    Comme illustré dans l'exemple ci-dessus, chaque colonne de caractères `|` doit être alignée verticalement.

    Un caractère `:` de chaque côté du séparateur d'en-tête d'une colonne (la ligne contenant des caractères `-`) spécifie si la ligne est alignée à gauche, à droite, ou (lorsque `:` apparaît des deux côtés) centrée. Ne pas fournir de caractères `:` par défaut alignera la colonne à droite.


### Admonitions

Des blocs spécialement formatés, connus sous le nom d'admonitions, peuvent être utilisés pour mettre en évidence des remarques particulières. Ils peuvent être définis en utilisant la syntaxe suivante `!!!` :

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

Le premier mot après `!!!` déclare le type de l'avertissement. Il existe des types d'avertissement standard qui devraient produire un style spécial. À savoir (par ordre de gravité décroissante) : `danger`, `warning`, `info`/`note`, et `tip`.

Vous pouvez également utiliser vos propres types d'admonition, tant que le nom du type ne contient que des caractères latins minuscules (a-z). Par exemple, vous pourriez avoir un bloc `terminology` comme ceci :

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

Cependant, à moins que le code rendant le Markdown ne traite ce type d'admonition de manière spéciale, il obtiendra le style par défaut.

Un titre personnalisé pour la boîte peut être fourni sous forme de chaîne (entre guillemets) après le type d'admonition. Si aucun texte de titre n'est spécifié après le type d'admonition, alors le nom du type sera utilisé comme titre (par exemple, `"Note"` pour l'admonition `note`).

Les admonitions, comme la plupart des autres éléments de premier niveau, peuvent contenir d'autres éléments de premier niveau (par exemple, des listes, des images).

## [Markdown String Literals](@id stdlib-markdown-literals)

Le macro `md""` vous permet d'incorporer des chaînes Markdown directement dans votre code Julia. Ce macro est conçu pour simplifier l'inclusion de texte formaté en Markdown dans vos fichiers source Julia.

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

Le markdown de Julia prend en charge l'interpolation de manière très similaire aux littéraux de chaîne de base, avec la différence qu'il stockera l'objet lui-même dans l'arbre Markdown (au lieu de le convertir en chaîne). Lorsque le contenu Markdown est rendu, les méthodes `show` habituelles seront appelées, et celles-ci peuvent être remplacées comme d'habitude. Ce design permet d'étendre le Markdown avec des fonctionnalités arbitrairement complexes (comme les références) sans encombrer la syntaxe de base.

En principe, le parseur Markdown lui-même peut également être étendu de manière arbitraire par des paquets, ou une variante entièrement personnalisée de Markdown peut être utilisée, mais cela devrait généralement être inutile.

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```

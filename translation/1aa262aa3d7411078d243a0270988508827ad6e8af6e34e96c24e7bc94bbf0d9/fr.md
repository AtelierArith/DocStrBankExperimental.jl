# [Strings](@id man-strings)

Les chaînes de caractères sont des séquences finies de caractères. Bien sûr, le véritable problème survient lorsque l'on se demande ce qu'est un caractère. Les caractères avec lesquels les anglophones sont familiers sont les lettres `A`, `B`, `C`, etc., ainsi que les chiffres et les symboles de ponctuation courants. Ces caractères sont standardisés avec un mappage vers des valeurs entières comprises entre 0 et 127 par la norme [ASCII](https://en.wikipedia.org/wiki/ASCII). Il existe, bien sûr, de nombreux autres caractères utilisés dans les langues non anglaises, y compris des variantes des caractères ASCII avec des accents et d'autres modifications, des scripts connexes tels que le cyrillique et le grec, et des scripts complètement non liés à l'ASCII et à l'anglais, y compris l'arabe, le chinois, l'hébreu, l'hindi, le japonais et le coréen. La norme [Unicode](https://en.wikipedia.org/wiki/Unicode) aborde les complexités de ce qu'est exactement un caractère et est généralement acceptée comme la norme définitive traitant de ce problème. Selon vos besoins, vous pouvez soit ignorer complètement ces complexités et prétendre que seuls les caractères ASCII existent, soit écrire du code capable de gérer n'importe quels caractères ou encodages que l'on peut rencontrer lors du traitement de texte non ASCII. Julia rend le traitement de texte ASCII simple et efficace, et la gestion de l'Unicode est aussi simple et efficace que possible. En particulier, vous pouvez écrire du code de chaîne de style C pour traiter des chaînes ASCII, et elles fonctionneront comme prévu, tant en termes de performance que de sémantique. Si un tel code rencontre du texte non ASCII, il échouera gracieusement avec un message d'erreur clair, plutôt que d'introduire silencieusement des résultats corrompus. Lorsque cela se produit, modifier le code pour gérer des données non ASCII est simple.

Il y a quelques caractéristiques notables au niveau élevé concernant les chaînes de caractères de Julia :

  * Le type concret intégré utilisé pour les chaînes (et les littéraux de chaîne) dans Julia est [`String`](@ref). Cela prend en charge l'ensemble complet des caractères [Unicode](https://en.wikipedia.org/wiki/Unicode) via l'encodage [UTF-8](https://en.wikipedia.org/wiki/UTF-8). (Une fonction [`transcode`](@ref) est fournie pour convertir vers/depuis d'autres encodages Unicode.)
  * Tous les types de chaînes sont des sous-types du type abstrait `AbstractString`, et des packages externes définissent des sous-types supplémentaires de `AbstractString` (par exemple pour d'autres encodages). Si vous définissez une fonction attendue avec un argument de type chaîne, vous devez déclarer le type comme `AbstractString` afin d'accepter tout type de chaîne.
  * Comme C et Java, mais contrairement à la plupart des langages dynamiques, Julia a un type de première classe pour représenter un seul caractère, appelé [`AbstractChar`](@ref). Le sous-type intégré [`Char`](@ref) de `AbstractChar` est un type primitif de 32 bits qui peut représenter n'importe quel caractère Unicode (et qui est basé sur l'encodage UTF-8).
  * Comme en Java, les chaînes de caractères sont immuables : la valeur d'un objet `AbstractString` ne peut pas être modifiée. Pour construire une valeur de chaîne différente, vous construisez une nouvelle chaîne à partir de parties d'autres chaînes.
  * Conceptuellement, une chaîne est une *fonction partielle* des indices vers des caractères : pour certaines valeurs d'index, aucune valeur de caractère n'est renvoyée, et à la place, une exception est levée. Cela permet un indexage efficace dans les chaînes par l'index d'octet d'une représentation encodée plutôt que par un index de caractère, ce qui ne peut pas être mis en œuvre à la fois de manière efficace et simple pour les encodages à largeur variable des chaînes Unicode.

## [Characters](@id man-characters)

Une valeur `Char` représente un seul caractère : c'est simplement un type primitif de 32 bits avec une représentation littérale spéciale et des comportements arithmétiques appropriés, et qui peut être converti en une valeur numérique représentant un [Unicode code point](https://en.wikipedia.org/wiki/Code_point). (Les packages Julia peuvent définir d'autres sous-types de `AbstractChar`, par exemple pour optimiser les opérations pour d'autres [text encodings](https://en.wikipedia.org/wiki/Character_encoding).) Voici comment les valeurs `Char` sont saisies et affichées (notez que les littéraux de caractères sont délimités par des guillemets simples, et non des guillemets doubles) :

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

Vous pouvez facilement convertir un `Char` en sa valeur entière, c'est-à-dire le point de code :

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

Sur les architectures 32 bits, [`typeof(c)`](@ref) sera [`Int32`](@ref). Vous pouvez convertir une valeur entière en `Char` tout aussi facilement :

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

Tous les valeurs entières ne sont pas des points de code Unicode valides, mais pour des raisons de performance, la conversion `Char` ne vérifie pas que chaque valeur de caractère est valide. Si vous souhaitez vérifier que chaque valeur convertie est un point de code valide, utilisez la fonction [`isvalid`](@ref) :

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

Au moment de la rédaction de ce document, les points de code Unicode valides sont `U+0000` à `U+D7FF` et `U+E000` à `U+10FFFF`. Tous n'ont pas encore été assignés à des significations intelligibles, ni ne sont nécessairement interprétables par les applications, mais toutes ces valeurs sont considérées comme des caractères Unicode valides.

Vous pouvez saisir n'importe quel caractère Unicode entre guillemets simples en utilisant `\u` suivi de jusqu'à quatre chiffres hexadécimaux ou `\U` suivi de jusqu'à huit chiffres hexadécimaux (la valeur valide la plus longue nécessite seulement six) :

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

Julia utilise les paramètres de langue et de région de votre système pour déterminer quels caractères peuvent être imprimés tels quels et lesquels doivent être affichés à l'aide des formes d'entrée génériques échappées `\u` ou `\U`. En plus de ces formes d'échappement Unicode, tout [C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes) peut également être utilisé :

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

Vous pouvez faire des comparaisons et une quantité limitée d'arithmétique avec des valeurs `Char` :

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

Les littéraux de chaîne sont délimités par des guillemets doubles ou des triples guillemets doubles (pas des guillemets simples) :

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

Les longues lignes dans les chaînes peuvent être interrompues en précédant la nouvelle ligne d'un antislash (`\`) :

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

Si vous souhaitez extraire un caractère d'une chaîne, vous l'indexez :

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

De nombreux objets Julia, y compris les chaînes de caractères, peuvent être indexés avec des entiers. L'index du premier élément (le premier caractère d'une chaîne) est renvoyé par [`firstindex(str)`](@ref), et l'index du dernier élément (caractère) avec [`lastindex(str)`](@ref). Les mots-clés `begin` et `end` peuvent être utilisés dans une opération d'indexation comme abréviation pour les premiers et derniers indices, respectivement, le long de la dimension donnée. L'indexation des chaînes, comme la plupart des indexations en Julia, est basée sur 1 : `firstindex` renvoie toujours `1` pour tout `AbstractString`. Comme nous le verrons ci-dessous, cependant, `lastindex(str)` n'est *pas* en général le même que `length(str)` pour une chaîne, car certains caractères Unicode peuvent occuper plusieurs "unités de code".

Vous pouvez effectuer des opérations arithmétiques et d'autres opérations avec [`end`](@ref), tout comme une valeur normale :

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

Utiliser un index inférieur à `begin` (`1`) ou supérieur à `end` déclenche une erreur :

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

Vous pouvez également extraire une sous-chaîne en utilisant l'indexation par plage :

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

Remarquez que les expressions `str[k]` et `str[k:k]` ne donnent pas le même résultat :

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

Le premier est une valeur de type `Char` composée d'un seul caractère, tandis que le second est une valeur de chaîne qui contient uniquement un seul caractère. En Julia, ce sont des choses très différentes.

L'indexation par plage crée une copie de la partie sélectionnée de la chaîne d'origine. Alternativement, il est possible de créer une vue dans une chaîne en utilisant le type [`SubString`](@ref). Plus simplement, en utilisant la macro [`@views`](@ref) sur un bloc de code, toutes les tranches de chaînes sont converties en sous-chaînes. Par exemple :

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

Plusieurs fonctions standard comme [`chop`](@ref), [`chomp`](@ref) ou [`strip`](@ref) retournent un [`SubString`](@ref).

## Unicode and UTF-8

Julia prend entièrement en charge les caractères et chaînes Unicode. En tant que [discussed above](@ref man-characters), dans les littéraux de caractères, les points de code Unicode peuvent être représentés à l'aide des séquences d'échappement Unicode `\u` et `\U`, ainsi que de toutes les séquences d'échappement C standard. Celles-ci peuvent également être utilisées pour écrire des littéraux de chaîne :

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

Que ces caractères Unicode soient affichés sous forme d'échappements ou en tant que caractères spéciaux dépend des paramètres régionaux de votre terminal et de son support pour Unicode. Les littéraux de chaîne sont encodés en utilisant l'encodage UTF-8. L'UTF-8 est un encodage à largeur variable, ce qui signifie que tous les caractères ne sont pas encodés avec le même nombre d'octets ("unités de code"). En UTF-8, les caractères ASCII — c'est-à-dire ceux dont les points de code sont inférieurs à 0x80 (128) – sont encodés tels quels en ASCII, en utilisant un seul octet, tandis que les points de code 0x80 et supérieurs sont encodés en utilisant plusieurs octets — jusqu'à quatre par caractère.

Les indices de chaîne en Julia font référence à des unités de code (= octets pour UTF-8), les blocs de construction à largeur fixe qui sont utilisés pour encoder des caractères arbitraires (points de code). Cela signifie que chaque indice dans une `String` n'est pas nécessairement un indice valide pour un caractère. Si vous indexez une chaîne à un indice d'octet invalide, une erreur est levée :

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

Dans ce cas, le caractère `∀` est un caractère de trois octets, donc les indices 2 et 3 sont invalides et l'indice du caractère suivant est 4 ; cet indice valide suivant peut être calculé par [`nextind(s,1)`](@ref), et l'indice suivant après cela par `nextind(s,4)` et ainsi de suite.

Puisque `end` est toujours le dernier index valide dans une collection, `end-1` fait référence à un index d'octet invalide si le caractère avant-dernier est multioctet.

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

Le premier cas fonctionne, car le dernier caractère `y` et l'espace sont des caractères à un octet, tandis que `end-2` indexe dans le milieu de la représentation multioctet de `∃`. La bonne façon pour ce cas est d'utiliser `prevind(s, lastindex(s), 2)` ou, si vous utilisez cette valeur pour indexer dans `s`, vous pouvez écrire `s[prevind(s, end, 2)]` et `end` s'étend à `lastindex(s)`.

L'extraction d'une sous-chaîne à l'aide de l'indexation par plage attend également des indices d'octets valides, sinon une erreur est levée :

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

En raison des encodages de longueur variable, le nombre de caractères dans une chaîne (donné par [`length(s)`](@ref)) n'est pas toujours le même que le dernier index. Si vous itérez à travers les indices 1 à [`lastindex(s)`](@ref) et indexez dans `s`, la séquence de caractères renvoyée lorsque des erreurs ne sont pas déclenchées est la séquence de caractères composant la chaîne `s`. Ainsi, `length(s) <= lastindex(s)`, puisque chaque caractère dans une chaîne doit avoir son propre index. Ce qui suit est une manière inefficace et verbeuse d'itérer à travers les caractères de `s` :

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

Les lignes vides contiennent en fait des espaces. Heureusement, l'idiome maladroit ci-dessus n'est pas nécessaire pour itérer à travers les caractères d'une chaîne, car vous pouvez simplement utiliser la chaîne comme un objet itérable, sans gestion des exceptions requise :

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

Si vous devez obtenir des indices valides pour une chaîne, vous pouvez utiliser les fonctions [`nextind`](@ref) et [`prevind`](@ref) pour incrémenter/décrémenter vers l'indice valide suivant/précédent, comme mentionné ci-dessus. Vous pouvez également utiliser la fonction [`eachindex`](@ref) pour itérer sur les indices de caractères valides :

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

Pour accéder aux unités de code brutes (octets pour UTF-8) de l'encodage, vous pouvez utiliser la fonction [`codeunit(s,i)`](@ref), où l'index `i` s'exécute consécutivement de `1` à [`ncodeunits(s)`](@ref). La fonction [`codeunits(s)`](@ref) renvoie un wrapper `AbstractVector{UInt8}` qui vous permet d'accéder à ces unités de code brutes (octets) sous forme de tableau.

Les chaînes en Julia peuvent contenir des séquences d'unités de code UTF-8 invalides. Cette convention permet de traiter n'importe quelle séquence d'octets comme une `String`. Dans de telles situations, une règle stipule que lors de l'analyse d'une séquence d'unités de code de gauche à droite, les caractères sont formés par la plus longue séquence d'unités de code de 8 bits qui correspond au début de l'un des motifs de bits suivants (chaque `x` peut être `0` ou `1`) :

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

En particulier, cela signifie que les séquences de code trop longues et trop élevées, ainsi que leurs préfixes, sont considérées comme un seul caractère invalide plutôt que comme plusieurs caractères invalides. Cette règle peut être mieux expliquée par un exemple :

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

Nous pouvons voir que les deux premières unités de code dans la chaîne `s` forment un encodage surlong du caractère espace. C'est invalide, mais est accepté dans une chaîne comme un seul caractère. Les deux unités de code suivantes forment un début valide d'une séquence UTF-8 de trois octets. Cependant, la cinquième unité de code `\xe2` n'est pas sa continuation valide. Par conséquent, les unités de code 3 et 4 sont également interprétées comme des caractères malformés dans cette chaîne. De même, l'unité de code 5 forme un caractère malformé car `|` n'est pas une continuation valide pour cela. Enfin, la chaîne `s2` contient un point de code trop élevé.

Julia utilise par défaut l'encodage UTF-8, et le support de nouveaux encodages peut être ajouté par des paquets. Par exemple, le paquet [LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl) implémente les types `UTF16String` et `UTF32String`. Une discussion supplémentaire sur d'autres encodages et comment implémenter le support pour eux dépasse le cadre de ce document pour le moment. Pour une discussion plus approfondie sur les problèmes d'encodage UTF-8, voir la section ci-dessous sur [byte array literals](@ref man-byte-array-literals). La fonction [`transcode`](@ref) est fournie pour convertir des données entre les différents encodages UTF-xx, principalement pour travailler avec des données et des bibliothèques externes.

## [Concatenation](@id man-concatenation)

Une des opérations sur les chaînes les plus courantes et utiles est la concaténation :

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

Il est important d'être conscient des situations potentiellement dangereuses telles que la concaténation de chaînes UTF-8 invalides. La chaîne résultante peut contenir des caractères différents de ceux des chaînes d'entrée, et son nombre de caractères peut être inférieur à la somme des nombres de caractères des chaînes concaténées, par exemple :

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

Cette situation ne peut se produire que pour des chaînes invalides en UTF-8. Pour des chaînes valides en UTF-8, la concaténation préserve tous les caractères des chaînes et l'additivité des longueurs de chaînes.

Julia fournit également [`*`](@ref) pour la concaténation de chaînes :

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

Bien que `*` puisse sembler être un choix surprenant pour les utilisateurs de langages qui fournissent `+` pour la concaténation de chaînes, cet usage de `*` a un précédent en mathématiques, en particulier en algèbre abstraite.

En mathématiques, `+` désigne généralement une opération *commutative*, où l'ordre des opérandes n'a pas d'importance. Un exemple de cela est l'addition de matrices, où `A + B == B + A` pour toutes les matrices `A` et `B` ayant la même forme. En revanche, `*` désigne généralement une opération *non commutative*, où l'ordre des opérandes *a* de l'importance. Un exemple de cela est la multiplication de matrices, où en général `A * B != B * A`. Comme pour la multiplication de matrices, la concaténation de chaînes est non commutative : `greet * whom != whom * greet`. Ainsi, `*` est un choix plus naturel pour un opérateur de concaténation de chaînes infixe, conforme à l'utilisation mathématique courante.

Plus précisément, l'ensemble de toutes les chaînes de longueur finie *S* ainsi que l'opérateur de concaténation de chaînes `*` forme un [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`). L'élément d'identité de cet ensemble est la chaîne vide, `""`. Chaque fois qu'un monoïde libre n'est pas commutatif, l'opération est généralement représentée par `\cdot`, `*`, ou un symbole similaire, plutôt que `+`, qui, comme indiqué, implique généralement la commutativité.

## [Interpolation](@id string-interpolation)

Construire des chaînes en utilisant la concaténation peut devenir un peu fastidieux, cependant. Pour réduire le besoin de ces appels verbeux à [`string`](@ref) ou de multiplications répétées, Julia permet l'interpolation dans les littéraux de chaîne en utilisant `$`, comme en Perl :

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

C'est plus lisible et pratique et équivalent à la concaténation de chaînes ci-dessus – le système réécrit cette apparente chaîne littérale unique dans l'appel `string(greet, ", ", whom, ".\n")`.

L'expression complète la plus courte après le `$` est considérée comme l'expression dont la valeur doit être interpolée dans la chaîne. Ainsi, vous pouvez interpoler n'importe quelle expression dans une chaîne en utilisant des parenthèses :

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

La concaténation et l'interpolation de chaînes appellent [`string`](@ref) pour convertir des objets en forme de chaîne. Cependant, `string` renvoie en réalité simplement la sortie de [`print`](@ref), donc les nouveaux types devraient ajouter des méthodes à `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` ou [`show`](@ref) au lieu de `string`.

La plupart des objets non-`AbstractString` sont convertis en chaînes de caractères correspondant étroitement à la façon dont ils sont saisis en tant qu'expressions littérales :

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref) est l'identité pour les valeurs `AbstractString` et `AbstractChar`, donc celles-ci sont interpolées dans des chaînes en tant que telles, sans guillemets ni échappement :

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

Pour inclure un `$` littéral dans une chaîne littérale, échappez-le avec un antislash :

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

Lorsque des chaînes sont créées à l'aide de triples guillemets (`"""..."""`), elles ont un comportement spécial qui peut être utile pour créer de plus longs blocs de texte.

Tout d'abord, les chaînes de caractères entre triples guillemets sont également décalées au niveau de la ligne la moins indentée. Cela est utile pour définir des chaînes dans du code qui est indenté. Par exemple :

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

Dans ce cas, la dernière ligne (vide) avant la fermeture `"""` définit le niveau d'indentation.

Le niveau de déindentation est déterminé comme la plus longue séquence commune de départ d'espaces ou de tabulations dans toutes les lignes, en excluant la ligne suivant l'ouverture de `"""` et les lignes contenant uniquement des espaces ou des tabulations (la ligne contenant le `"""` de fermeture est toujours incluse). Ensuite, pour toutes les lignes, à l'exception du texte suivant l'ouverture de `"""`, la séquence de départ commune est supprimée (y compris les lignes contenant uniquement des espaces et des tabulations si elles commencent par cette séquence), par exemple :

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

Ensuite, si l'ouverture `"""` est suivie d'une nouvelle ligne, la nouvelle ligne est supprimée de la chaîne résultante.

```julia
"""hello"""
```

est équivalent à

```julia
"""
hello"""
```

mais

```julia
"""

hello"""
```

will contain a literal newline at the beginning.

La suppression de la nouvelle ligne est effectuée après la dé-indentation. Par exemple :

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

Si la nouvelle ligne est supprimée à l'aide d'un antislash, la déindention sera également respectée :

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

L'espace blanc à la fin est laissé inchangé.

Les chaînes de caractères littérales entre triples guillemets peuvent contenir des caractères `"` sans échappement.

Notez que les sauts de ligne dans les chaînes littérales, qu'elles soient entre guillemets simples ou triples, entraînent un caractère de nouvelle ligne (LF) `\n` dans la chaîne, même si votre éditeur utilise un retour chariot `\r` (CR) ou une combinaison CRLF pour terminer les lignes. Pour inclure un CR dans une chaîne, utilisez une échappement explicite `\r` ; par exemple, vous pouvez entrer la chaîne littérale `"a CRLF line ending\r\n"`.

## Common Operations

Vous pouvez comparer des chaînes de caractères lexicographiquement en utilisant les opérateurs de comparaison standard :

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

Vous pouvez rechercher l'index d'un caractère particulier en utilisant les fonctions [`findfirst`](@ref) et [`findlast`](@ref) :

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

Vous pouvez commencer la recherche d'un caractère à un décalage donné en utilisant les fonctions [`findnext`](@ref) et [`findprev`](@ref) :

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

Vous pouvez utiliser la fonction [`occursin`](@ref) pour vérifier si une sous-chaîne est trouvée dans une chaîne :

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

Le dernier exemple montre que [`occursin`](@ref) peut également rechercher un littéral de caractère.

Deux autres fonctions de chaîne pratiques sont [`repeat`](@ref) et [`join`](@ref) :

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

D'autres fonctions utiles incluent :

  * [`firstindex(str)`](@ref) donne l'index minimal (octet) qui peut être utilisé pour indexer dans `str` (toujours 1 pour les chaînes, pas nécessairement vrai pour d'autres conteneurs).
  * [`lastindex(str)`](@ref) donne l'index maximal (octet) qui peut être utilisé pour indexer dans `str`.
  * [`length(str)`](@ref) le nombre de caractères dans `str`.
  * [`length(str, i, j)`](@ref) le nombre d'indices de caractères valides dans `str` de `i` à `j`.
  * [`ncodeunits(str)`](@ref) nombre de [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) dans une chaîne.
  * [`codeunit(str, i)`](@ref) donne la valeur de l'unité de code dans la chaîne `str` à l'index `i`.
  * [`thisind(str, i)`](@ref) donné un index arbitraire dans une chaîne, trouvez le premier index du caractère vers lequel l'index pointe.
  * [`nextind(str, i, n=1)`](@ref) trouver le début du `n`ième caractère commençant après l'index `i`.
  * [`prevind(str, i, n=1)`](@ref) trouver le début du `n`-ième caractère commençant avant l'index `i`.

## [Non-Standard String Literals](@id non-standard-string-literals)

Il existe des situations où vous souhaitez construire une chaîne ou utiliser la sémantique des chaînes, mais le comportement de la construction de chaîne standard n'est pas tout à fait ce qui est nécessaire. Pour ce genre de situations, Julia fournit des littéraux de chaîne non standard. Un littéral de chaîne non standard ressemble à un littéral de chaîne entre guillemets doubles ordinaire, mais est immédiatement précédé d'un identifiant et peut se comporter différemment d'un littéral de chaîne normal.

[Regular expressions](@ref man-regex-literals), [byte array literals](@ref man-byte-array-literals), et [version number literals](@ref man-version-number-literals), comme décrit ci-dessous, sont quelques exemples de littéraux de chaîne non standard. Les utilisateurs et les packages peuvent également définir de nouveaux littéraux de chaîne non standard. Une documentation supplémentaire est donnée dans la section [Metaprogramming](@ref meta-non-standard-string-literals).

## [Regular Expressions](@id man-regex-literals)

Parfois, vous ne recherchez pas une chaîne exacte, mais un *modèle* particulier. Par exemple, supposons que vous essayez d'extraire une seule date d'un grand fichier texte. Vous ne savez pas quelle est cette date (c'est pourquoi vous la recherchez), mais vous savez qu'elle ressemblera à quelque chose comme `YYYY-MM-DD`. Les expressions régulières vous permettent de spécifier ces modèles et de les rechercher.

Julia utilise la version 2 des expressions régulières compatibles avec Perl (regex), comme fourni par la bibliothèque [PCRE](https://www.pcre.org/) (voir le [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html) pour plus de détails). Les expressions régulières sont liées aux chaînes de deux manières : la connexion évidente est que les expressions régulières sont utilisées pour trouver des motifs réguliers dans les chaînes ; l'autre connexion est que les expressions régulières sont elles-mêmes saisies sous forme de chaînes, qui sont analysées en une machine d'état pouvant être utilisée pour rechercher efficacement des motifs dans les chaînes. En Julia, les expressions régulières sont saisies à l'aide de littéraux de chaîne non standard préfixés par divers identifiants commençant par `r`. Le littéral d'expression régulière le plus basique sans aucune option activée utilise simplement `r"..."` :

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

Pour vérifier si une expression régulière correspond à une chaîne, utilisez [`occursin`](@ref) :

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

Comme on peut le voir ici, [`occursin`](@ref) renvoie simplement vrai ou faux, indiquant si une correspondance pour l'expression régulière donnée se produit dans la chaîne. Cependant, communément, on veut savoir non seulement si une chaîne correspond, mais aussi *comment* elle correspond. Pour capturer cette information sur une correspondance, utilisez plutôt la fonction [`match`](@ref) :

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

Si l'expression régulière ne correspond pas à la chaîne donnée, [`match`](@ref) renvoie [`nothing`](@ref) – une valeur spéciale qui ne s'affiche pas à l'invite interactive. En dehors du fait qu'elle ne s'affiche pas, c'est une valeur complètement normale et vous pouvez la tester de manière programmatique :

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

Si une expression régulière correspond, la valeur retournée par [`match`](@ref) est un objet [`RegexMatch`](@ref). Ces objets enregistrent comment l'expression correspond, y compris la sous-chaîne que le motif correspond et toutes les sous-chaînes capturées, s'il y en a. Cet exemple ne capture que la portion de la sous-chaîne qui correspond, mais peut-être voulons-nous capturer tout texte non vide après le caractère de commentaire. Nous pourrions faire ce qui suit :

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

Lorsque vous appelez [`match`](@ref), vous avez la possibilité de spécifier un index à partir duquel commencer la recherche. Par exemple :

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

Vous pouvez extraire les informations suivantes d'un objet `RegexMatch` :

  * la sous-chaîne entière correspondante : `m.match`
  * les sous-chaînes capturées sous forme de tableau de chaînes : `m.captures`
  * le décalage auquel commence l'ensemble du match : `m.offset`
  * les décalages des sous-chaînes capturées sous forme de vecteur : `m.offsets`

Pour quand une capture ne correspond pas, au lieu d'une sous-chaîne, `m.captures` contient `nothing` à cette position, et `m.offsets` a un décalage de zéro (rappelez-vous que les indices en Julia sont basés sur 1, donc un décalage de zéro dans une chaîne est invalide). Voici une paire d'exemples quelque peu artificiels :

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

Il est pratique d'avoir les captures renvoyées sous forme de tableau afin de pouvoir utiliser la syntaxe de déstructuration pour les lier à des variables locales. Par commodité, l'objet `RegexMatch` implémente des méthodes d'itérateur qui passent par le champ `captures`, vous permettant ainsi de déstructurer directement l'objet de correspondance :

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

Les captures peuvent également être accessibles en indexant l'objet `RegexMatch` avec le numéro ou le nom du groupe de capture :

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

Les captures peuvent être référencées dans une chaîne de substitution lors de l'utilisation de [`replace`](@ref) en utilisant `\n` pour faire référence au nième groupe de capture et en préfixant la chaîne de substitution avec `s`. Le groupe de capture 0 fait référence à l'objet de correspondance entier. Les groupes de capture nommés peuvent être référencés dans la substitution avec `\g<nomdugroupe>`. Par exemple :

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

Les groupes de capture numérotés peuvent également être référencés sous la forme `\g<n>` pour éviter toute ambiguïté, comme dans :

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

Vous pouvez modifier le comportement des expressions régulières par une combinaison des drapeaux `i`, `m`, `s` et `x` après le guillemet double de fermeture. Ces drapeaux ont la même signification qu'en Perl, comme expliqué dans cet extrait de [perlre manpage](https://perldoc.perl.org/perlre#Modifiers) :

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

Par exemple, l'expression régulière suivante a les trois indicateurs activés :

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Le littéral `r"..."` est construit sans interpolation et désévasion (sauf pour le guillemet `"` qui doit toujours être échappé). Voici un exemple montrant la différence par rapport aux littéraux de chaîne standard :

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

Les chaînes regex entre triples guillemets, sous la forme `r"""..."""`, sont également prises en charge (et peuvent être pratiques pour les expressions régulières contenant des guillemets ou des sauts de ligne).

Le constructeur `Regex()` peut être utilisé pour créer une chaîne regex valide de manière programmatique. Cela permet d'utiliser le contenu des variables de chaîne et d'autres opérations sur les chaînes lors de la construction de la chaîne regex. N'importe quel code regex ci-dessus peut être utilisé dans l'argument de chaîne unique de `Regex()`. Voici quelques exemples :

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

Notez l'utilisation de la séquence d'échappement `\Q...\E`. Tous les caractères entre `\Q` et `\E` sont interprétés comme des caractères littéraux. Cela est pratique pour faire correspondre des caractères qui seraient autrement des métacaractères regex. Cependant, il faut faire preuve de prudence lors de l'utilisation de cette fonctionnalité avec l'interpolation de chaînes, car la chaîne interpolée pourrait elle-même contenir la séquence `\E`, terminant de manière inattendue la correspondance littérale. Les entrées utilisateur doivent être assainies avant d'être incluses dans une regex.

## [Byte Array Literals](@id man-byte-array-literals)

Un autre littéral de chaîne non standard utile est le littéral de tableau d'octets : `b"..."`. Cette forme vous permet d'utiliser la notation de chaîne pour exprimer des tableaux d'octets littéraux en lecture seule – c'est-à-dire des tableaux de valeurs [`UInt8`](@ref). Le type de ces objets est `CodeUnits{UInt8, String}`. Les règles pour les littéraux de tableau d'octets sont les suivantes :

  * Les caractères ASCII et les échappements ASCII produisent un seul octet.
  * `\x` et les séquences d'échappement octales produisent le *octet* correspondant à la valeur d'échappement.
  * Les séquences d'échappement Unicode produisent une séquence d'octets encodant ce point de code en UTF-8.

Il y a un certain chevauchement entre ces règles puisque le comportement de `\x` et des échappements octaux inférieurs à 0x80 (128) est couvert par les deux premières règles, mais ici ces règles s'accordent. Ensemble, ces règles permettent d'utiliser facilement des caractères ASCII, des valeurs d'octets arbitraires et des séquences UTF-8 pour produire des tableaux d'octets. Voici un exemple utilisant les trois :

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

La chaîne ASCII "DATA" correspond aux octets 68, 65, 84, 65. `\xff` produit l'octet unique 255. L'échappement Unicode `\u2200` est encodé en UTF-8 sous la forme des trois octets 226, 136, 128. Notez que le tableau d'octets résultant ne correspond pas à une chaîne UTF-8 valide :

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

Comme il a été mentionné, le type `CodeUnits{UInt8, String}` se comporte comme un tableau en lecture seule de `UInt8` et si vous avez besoin d'un vecteur standard, vous pouvez le convertir en utilisant `Vector{UInt8}` :

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

Observez également la distinction significative entre `\xff` et `\uff` : la première séquence d'échappement encode le *byte 255*, tandis que la dernière séquence d'échappement représente le *point de code 255*, qui est encodé en deux octets en UTF-8 :

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

Les littéraux de caractères utilisent le même comportement.

Pour les points de code inférieurs à `\u80`, il se trouve que l'encodage UTF-8 de chaque point de code est simplement le seul octet produit par l'échappement correspondant `\x`, donc la distinction peut être ignorée en toute sécurité. Pour les échappements `\x80` à `\xff` par rapport à `\u80` à `\uff`, cependant, il y a une différence majeure : les premiers échappements encodent tous des octets uniques, qui – à moins d'être suivis de très spécifiques octets de continuation – ne forment pas de données UTF-8 valides, tandis que les derniers échappements représentent tous des points de code Unicode avec des encodages sur deux octets.

Si tout cela est extrêmement déroutant, essayez de lire ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/). C'est une excellente introduction à Unicode et UTF-8, et cela peut aider à atténuer certaines confusions concernant le sujet.

## [Version Number Literals](@id man-version-number-literals)

Les numéros de version peuvent facilement être exprimés avec des littéraux de chaîne non standard de la forme [`v"..."`](@ref @v_str). Les littéraux de numéro de version créent des objets [`VersionNumber`](@ref) qui suivent les spécifications de [semantic versioning](https://semver.org/), et sont donc composés de valeurs numériques majeures, mineures et de correctif, suivies d'annotations alphanumériques de pré-version et de construction. Par exemple, `v"0.2.1-rc1+win64"` est décomposé en version majeure `0`, version mineure `2`, version de correctif `1`, pré-version `rc1` et construction `win64`. Lors de l'entrée d'un littéral de version, tout sauf le numéro de version majeur est optionnel, donc par exemple `v"0.2"` est équivalent à `v"0.2.0"` (avec des annotations de pré-version/construction vides), `v"2"` est équivalent à `v"2.0.0"`, et ainsi de suite.

`VersionNumber` objets sont principalement utiles pour comparer facilement et correctement deux (ou plusieurs) versions. Par exemple, la constante [`VERSION`](@ref) contient le numéro de version de Julia sous forme d'objet `VersionNumber`, et par conséquent, on peut définir un comportement spécifique à la version en utilisant des déclarations simples comme :

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

Notez que dans l'exemple ci-dessus, le numéro de version non standard `v"0.3-"` est utilisé, avec un `-` final : cette notation est une extension de Julia de la norme, et elle est utilisée pour indiquer une version qui est inférieure à toute version `0.3`, y compris toutes ses pré-releases. Ainsi, dans l'exemple ci-dessus, le code ne fonctionnerait qu'avec des versions stables `0.2`, et exclurait des versions telles que `v"0.3.0-rc1"`. Afin de permettre également des versions `0.2` instables (c'est-à-dire des pré-releases), la vérification de la limite inférieure devrait être modifiée comme suit : `v"0.2-" <= VERSION`.

Une autre extension de spécification de version non standard permet d'utiliser un `+` final pour exprimer une limite supérieure sur les versions de construction, par exemple `VERSION > v"0.2-rc1+"` peut être utilisé pour signifier toute version supérieure à `0.2-rc1` et l'une de ses constructions : cela renverra `false` pour la version `v"0.2-rc1+win64"` et `true` pour `v"0.2-rc2"`.

Il est bon de pratiquer l'utilisation de telles versions spéciales dans les comparaisons (en particulier, le `-` final doit toujours être utilisé sur les limites supérieures à moins qu'il n'y ait une bonne raison de ne pas le faire), mais elles ne doivent pas être utilisées comme le numéro de version réel de quoi que ce soit, car elles sont invalides dans le schéma de versionnement sémantique.

En plus d'être utilisé pour le constant [`VERSION`](@ref), les objets `VersionNumber` sont largement utilisés dans le module `Pkg`, pour spécifier les versions des packages et leurs dépendances.

## [Raw String Literals](@id man-raw-string-literals)

Les chaînes brutes sans interpolation ni désévasion peuvent être exprimées avec des littéraux de chaîne non standard de la forme `raw"..."`. Les littéraux de chaîne bruts créent des objets `String` ordinaires qui contiennent le contenu enfermé exactement tel qu'il a été saisi, sans interpolation ni désévasion. Cela est utile pour les chaînes qui contiennent du code ou du balisage dans d'autres langages qui utilisent `$` ou `\` comme caractères spéciaux.

L'exception est que les guillemets doivent toujours être échappés, par exemple `raw"\""` est équivalent à `"\""`. Pour rendre possible l'expression de toutes les chaînes, les barres obliques inverses doivent également être échappées, mais seulement lorsqu'elles apparaissent juste avant un caractère de citation :

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

Remarquez que les deux premiers barres obliques inverses apparaissent telles quelles dans la sortie, car elles ne précèdent pas un caractère de citation. Cependant, le prochain caractère de barre oblique inverse échappe la barre oblique inverse qui le suit, et la dernière barre oblique inverse échappe une citation, puisque ces barres obliques inverses apparaissent avant une citation.

## [Annotated Strings](@id man-annotated-strings)

!!! note
    L'API pour les AnnotatedStrings est considérée comme expérimentale et est sujette à des modifications entre les versions de Julia.


Il est parfois utile de pouvoir conserver des métadonnées relatives à des régions d'une chaîne de caractères. Un [`AnnotatedString`](@ref Base.AnnotatedString) enveloppe une autre chaîne et permet d'annoter des régions avec des valeurs étiquetées (`:label => value`). Toutes les opérations de chaîne génériques sont appliquées à la chaîne sous-jacente. Cependant, lorsque cela est possible, les informations de style sont préservées. Cela signifie que vous pouvez manipuler un `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` — en prenant des sous-chaînes, en les remplissant, en les concaténant avec d'autres chaînes — et les annotations de métadonnées "viendront avec".

Ce type de chaîne est fondamental pour le [StyledStrings stdlib](@ref stdlib-styledstrings), qui utilise des annotations étiquetées `:face` pour contenir des informations de style.

Lors de la concaténation d'un [`AnnotatedString`](@ref Base.AnnotatedString), veillez à utiliser [`annotatedstring`](@ref Base.annotatedstring) au lieu de [`string`](@ref) si vous souhaitez conserver les annotations de chaîne.

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

Les annotations d'un [`AnnotatedString`](@ref Base.AnnotatedString) peuvent être accessibles et modifiées via les fonctions [`annotations`](@ref Base.annotations) et [`annotate!`](@ref Base.annotate!).

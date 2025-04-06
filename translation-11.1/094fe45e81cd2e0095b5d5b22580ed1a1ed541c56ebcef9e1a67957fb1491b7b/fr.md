```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

Normalisez la chaîne `s`. Par défaut, la composition canonique (`compose=true`) est effectuée sans garantir la stabilité de la version Unicode (`compat=false`), ce qui produit la chaîne équivalente la plus courte possible mais peut introduire des caractères de composition non présents dans les versions Unicode antérieures.

Alternativement, l'une des quatre "formes normales" de la norme Unicode peut être spécifiée : `normalform` peut être `:NFC`, `:NFD`, `:NFKC` ou `:NFKD`. Les formes normales C (composition canonique) et D (décomposition canonique) convertissent différentes représentations visuellement identiques de la même chaîne abstraite en une seule forme canonique, la forme C étant plus compacte. Les formes normales KC et KD canonisent également les "équivalents de compatibilité" : elles convertissent des caractères qui sont abstraitement similaires mais visuellement distincts en un choix canonique unique (par exemple, elles développent les ligatures en caractères individuels), la forme KC étant plus compacte.

Alternativement, un contrôle plus fin et des transformations supplémentaires peuvent être obtenus en appelant `Unicode.normalize(s; keywords...)`, où un nombre quelconque des options de mots-clés booléens suivants (qui sont tous par défaut à `false` sauf pour `compose`) sont spécifiés :

  * `compose=false` : ne pas effectuer de composition canonique
  * `decompose=true` : effectuer une décomposition canonique au lieu d'une composition canonique (`compose=true` est ignoré si présent)
  * `compat=true` : les équivalents de compatibilité sont canonisés
  * `casefold=true` : effectuer un pliage de casse Unicode, par exemple pour une comparaison de chaînes insensible à la casse
  * `newline2lf=true`, `newline2ls=true`, ou `newline2ps=true` : convertir diverses séquences de nouvelle ligne (LF, CRLF, CR, NEL) en un caractère de saut de ligne (LF), de séparation de ligne (LS) ou de séparation de paragraphe (PS), respectivement
  * `stripmark=true` : supprimer les marques diacritiques (par exemple, les accents)
  * `stripignore=true` : supprimer les caractères "ignorables par défaut" d'Unicode (par exemple, le trait d'union souple ou le marqueur de gauche à droite)
  * `stripcc=true` : supprimer les caractères de contrôle ; les tabulations horizontales et les sauts de page sont convertis en espaces ; les nouvelles lignes sont également converties en espaces à moins qu'un drapeau de conversion de nouvelle ligne ne soit spécifié
  * `rejectna=true` : lancer une erreur si des points de code non attribués sont trouvés
  * `stable=true` : imposer la stabilité de la version Unicode (ne jamais introduire de caractères manquants dans les versions Unicode antérieures)

Vous pouvez également utiliser le mot-clé `chartransform` (qui par défaut est `identity`) pour passer une *fonction* arbitraire mappant des points de code `Integer` à des points de code, qui est appelée sur chaque caractère de `s` au fur et à mesure qu'il est traité, afin d'effectuer des normalisations supplémentaires arbitraires. Par exemple, en passant `chartransform=Unicode.julia_chartransform`, vous pouvez appliquer quelques normalisations de caractères spécifiques à Julia qui sont effectuées par Julia lors de l'analyse des identifiants (en plus de la normalisation NFC : `compose=true, stable=true`).

Par exemple, NFKC correspond aux options `compose=true, compat=true, stable=true`.

# Exemples

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    L'argument de mot-clé `chartransform` nécessite Julia 1.8.


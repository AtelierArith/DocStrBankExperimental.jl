Le type `AbstractString` est le supertype de toutes les implémentations de chaînes en Julia. Les chaînes sont des encodages de séquences de points de code [Unicode](https://unicode.org/) tels que représentés par le type `AbstractChar`. Julia fait quelques hypothèses sur les chaînes :

  * Les chaînes sont encodées en termes d'« unités de code » de taille fixe

      * Les unités de code peuvent être extraites avec `codeunit(s, i)`
      * La première unité de code a l'index `1`
      * La dernière unité de code a l'index `ncodeunits(s)`
      * Tout index `i` tel que `1 ≤ i ≤ ncodeunits(s)` est dans les limites
  * L'indexation des chaînes se fait en termes de ces unités de code :

      * Les caractères sont extraits par `s[i]` avec un index de chaîne valide `i`
      * Chaque `AbstractChar` dans une chaîne est encodé par une ou plusieurs unités de code
      * Seul l'index de la première unité de code d'un `AbstractChar` est un index valide
      * L'encodage d'un `AbstractChar` est indépendant de ce qui le précède ou le suit
      * Les encodages de chaînes sont [auto-synchronisants](https://en.wikipedia.org/wiki/Self-synchronizing_code) – c'est-à-dire que `isvalid(s, i)` est O(1)

Certaines fonctions de chaîne qui extraient des unités de code, des caractères ou des sous-chaînes des chaînes renvoient une erreur si vous leur passez des indices de chaîne hors limites ou invalides. Cela inclut `codeunit(s, i)` et `s[i]`. Les fonctions qui effectuent des calculs d'index de chaîne adoptent une approche plus détendue de l'indexation et vous donnent l'index de chaîne valide le plus proche lorsqu'il est dans les limites, ou lorsqu'il est hors limites, se comportent comme s'il y avait un nombre infini de caractères remplissant chaque côté de la chaîne. En général, ces caractères de remplissage imaginaires ont une longueur d'unité de code de `1`, mais les types de chaînes peuvent choisir différentes tailles de caractères « imaginaires » selon ce qui a du sens pour leurs implémentations (par exemple, les sous-chaînes peuvent transmettre les calculs d'index à la chaîne sous-jacente à laquelle elles fournissent une vue). Les fonctions d'indexation détendues incluent celles destinées aux calculs d'index : `thisind`, `nextind` et `prevind`. Ce modèle permet aux calculs d'index de fonctionner avec des indices hors limites en tant que valeurs intermédiaires tant que l'on ne les utilise jamais pour récupérer un caractère, ce qui aide souvent à éviter d'avoir besoin de coder autour des cas limites.

Voir aussi [`codeunit`](@ref), [`ncodeunits`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

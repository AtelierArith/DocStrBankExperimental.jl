```
x::EscapeInfo
```

Une structure pour les informations d'évasion, qui possède les propriétés suivantes :

  * `x.Analyzed::Bool` : pas formellement partie de la structure, indique seulement si `x` a été analysé
  * `x.ReturnEscape::Bool` : indique que `x` peut s'échapper vers l'appelant via le retour
  * `x.ThrownEscape::BitSet` : enregistre les numéros d'instruction SSA où `x` peut être lancé comme exception :

      * `isempty(x.ThrownEscape)` : `x` ne sera jamais lancé dans ce cadre d'appel (le bas)
      * `pc ∈ x.ThrownEscape` : `x` peut être lancé à l'instruction SSA à `pc`
      * `-1 ∈ x.ThrownEscape` : `x` peut être lancé à des points arbitraires de ce cadre d'appel (le haut)

    Cette information sera utilisée par `escape_exception!` pour propager les évasions potentielles via exception.
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}` : maintient toutes les valeurs possibles qui peuvent être aliasées aux champs ou éléments de tableau de `x` :

      * `x.AliasInfo === false` indique que les champs/éléments de `x` n'ont pas encore été analysés
      * `x.AliasInfo === true` indique que les champs/éléments de `x` ne peuvent pas être analysés, par exemple, le type de `x` n'est pas connu ou n'est pas concret et donc ses champs/éléments ne peuvent pas être connus précisément
      * `x.AliasInfo::IndexableFields` enregistre toutes les valeurs possibles qui peuvent être aliasées aux champs de l'objet `x` avec des informations d'index précises
      * `x.AliasInfo::IndexableElements` enregistre toutes les valeurs possibles qui peuvent être aliasées aux éléments du tableau `x` avec des informations d'index précises
      * `x.AliasInfo::Unindexable` enregistre toutes les valeurs possibles qui peuvent être aliasées aux champs/éléments de `x` sans informations d'index précises
  * `x.Liveness::BitSet` : enregistre les numéros d'instruction SSA où `x` devrait être vivant, par exemple, pour être utilisé comme argument d'appel, pour être retourné à un appelant, ou préservé pour `:foreigncall` :

      * `isempty(x.Liveness)` : `x` n'est jamais utilisé dans ce cadre d'appel (le bas)
      * `0 ∈ x.Liveness` a également la signification spéciale qu'il s'agit d'un argument d'appel du cadre d'appel actuellement analysé (et donc il est visible de l'appelant immédiatement).
      * `pc ∈ x.Liveness` : `x` peut être utilisé à l'instruction SSA à `pc`
      * `-1 ∈ x.Liveness` : `x` peut être utilisé à des points arbitraires de ce cadre d'appel (le haut)

Il existe des constructeurs utilitaires pour créer des `EscapeInfo` communs, par exemple :

  * `NoEscape()` : l'élément du bas (comme) de cette structure, signifiant qu'il ne s'échappera nulle part
  * `AllEscape()` : l'élément le plus haut de cette structure, signifiant qu'il s'échappera partout

`analyze_escapes` fera passer ces éléments du bas vers le haut, dans la même direction que la routine d'inférence de type native de Julia. Un état abstrait sera initialisé avec les éléments du bas (comme) :

  * les arguments d'appel sont initialisés comme `ArgEscape()`, dont la propriété `Liveness` inclut `0` pour indiquer qu'il est passé comme argument d'appel et visible immédiatement d'un appelant
  * les autres états sont initialisés comme `NotAnalyzed()`, qui est un élément de structure spécial qui est légèrement inférieur à `NoEscape`, mais en même temps ne représente aucune signification autre que le fait qu'il n'a pas encore été analysé (donc il ne fait pas formellement partie de la structure)

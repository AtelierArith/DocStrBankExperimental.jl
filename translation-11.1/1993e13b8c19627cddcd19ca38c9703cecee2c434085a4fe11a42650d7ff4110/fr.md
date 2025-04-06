```
SamplerTrivial(x)
```

Créez un échantillonneur qui enveloppe simplement la valeur donnée `x`. C'est le recours par défaut pour les valeurs. Le `eltype` de cet échantillonneur est égal à `eltype(x)`.

Le cas d'utilisation recommandé est l'échantillonnage à partir de valeurs sans données pré-calculées.

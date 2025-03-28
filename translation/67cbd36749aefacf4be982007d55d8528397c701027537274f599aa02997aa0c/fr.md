```
CompoundPeriod
```

Un `CompoundPeriod` est utile pour exprimer des périodes de temps qui ne sont pas un multiple fixe de périodes plus petites. Par exemple, "une année et un jour" n'est pas un nombre fixe de jours, mais peut être exprimé à l'aide d'un `CompoundPeriod`. En fait, un `CompoundPeriod` est automatiquement généré par l'addition de différents types de périodes, par exemple `Year(1) + Day(1)` produit un résultat de type `CompoundPeriod`.

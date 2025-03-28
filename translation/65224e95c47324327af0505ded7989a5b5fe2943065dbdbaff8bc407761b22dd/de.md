```
Date(period::Period...) -> Date
```

Konstruiere einen `Date`-Typ aus `Period`-Typteilen. Die Argumente können in beliebiger Reihenfolge angegeben werden. `Date`-Teile, die nicht bereitgestellt werden, haben den Standardwert von `Dates.default(period)`.

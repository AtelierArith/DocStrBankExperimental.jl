```
Time(period::TimePeriod...) -> Time
```

Konstruiere einen `Time`-Typ aus `Period`-Typteilen. Die Argumente können in beliebiger Reihenfolge angegeben werden. `Time`-Teile, die nicht bereitgestellt werden, haben den Standardwert von `Dates.default(period)`.

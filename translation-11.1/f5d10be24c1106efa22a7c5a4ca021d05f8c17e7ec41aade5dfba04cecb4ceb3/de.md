```
toprev(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

Passt `dt` auf den vorherigen Wochentag entsprechend `dow` an, wobei `1 = Montag, 2 = Dienstag, usw.` Die Einstellung `same=true` ermöglicht es, dass das aktuelle `dt` als der vorherige `dow` betrachtet wird, sodass keine Anpassung erfolgt.

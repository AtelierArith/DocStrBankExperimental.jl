```
tonext(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

Passt `dt` auf den nächsten Wochentag entsprechend `dow` an, wobei `1 = Montag, 2 = Dienstag, usw.` Das Setzen von `same=true` ermöglicht es, dass das aktuelle `dt` als der nächste `dow` betrachtet wird, sodass keine Anpassung erfolgt.

```
floorceil(dt::TimeType, p::Period) -> (TimeType, TimeType)
```

Retourne simultanément le `floor` et le `ceil` d'une `Date` ou `DateTime` à la résolution `p`. Plus efficace que d'appeler `floor` et `ceil` individuellement.

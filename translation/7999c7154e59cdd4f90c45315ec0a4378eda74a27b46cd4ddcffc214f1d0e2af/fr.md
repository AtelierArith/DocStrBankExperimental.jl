```
isready(rr::RemoteChannel, args...)
```

Déterminez si un [`RemoteChannel`](@ref) a une valeur stockée. Notez que cette fonction peut provoquer des conditions de concurrence, car au moment où vous recevez son résultat, cela peut ne plus être vrai. Cependant, elle peut être utilisée en toute sécurité sur un [`Future`](@ref) car ils ne sont assignés qu'une seule fois.

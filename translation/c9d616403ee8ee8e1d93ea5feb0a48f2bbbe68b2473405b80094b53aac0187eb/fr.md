```
fetch(x::Future)
```

Attendez et obtenez la valeur d'un [`Future`](@ref). La valeur récupérée est mise en cache localement. Les appels ultérieurs à `fetch` sur la même référence renvoient la valeur mise en cache. Si la valeur distante est une exception, cela lance une [`RemoteException`](@ref) qui capture l'exception distante et la trace de la pile.

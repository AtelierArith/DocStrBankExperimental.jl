```
fetch(c::RemoteChannel)
```

Attendez et obtenez une valeur d'un [`RemoteChannel`](@ref). Les exceptions levées sont les mêmes que pour un [`Future`](@ref). Ne supprime pas l'élément récupéré.

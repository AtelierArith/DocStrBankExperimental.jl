```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

Por defecto, las funciones `redisplay` simplemente llaman a [`display`](@ref). Sin embargo, algunos backends de visualización pueden anular `redisplay` para modificar una visualización existente de `x` (si la hay). Usar `redisplay` también es una pista para el backend de que `x` puede ser visualizado varias veces, y el backend puede optar por diferir la visualización hasta (por ejemplo) el siguiente aviso interactivo.

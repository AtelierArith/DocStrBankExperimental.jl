```
displayable(mime) -> Bool
displayable(d::AbstractDisplay, mime) -> Bool
```

Devuelve un valor booleano que indica si el tipo `mime` dado (cadena) es mostrable por cualquiera de los displays en la pila de displays actual, o específicamente por el display `d` en la segunda variante.

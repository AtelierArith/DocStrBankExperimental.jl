```
errno([código])
```

Obtiene el valor de `errno` de la biblioteca C. Si se especifica un argumento, se utiliza para establecer el valor de `errno`.

El valor de `errno` solo es válido inmediatamente después de un `ccall` a una rutina de la biblioteca C que lo establece. Específicamente, no puedes llamar a `errno` en el siguiente aviso en un REPL, porque se ejecuta mucho código entre avisos.

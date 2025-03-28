```
MultiSelectMenu
```

Un menú que permite a un usuario seleccionar múltiples opciones de una lista.

# Salida de Ejemplo

```julia-repl
julia> request(MultiSelectMenu(options))
Selecciona las frutas que te gustan:
[presiona: Enter=alternar, a=todas, n=ninguna, d=hecho, q=abortar]
   [ ] manzana
 > [X] naranja
   [X] uva
   [ ] fresa
   [ ] arándano
   [X] durazno
   [ ] limón
   [ ] lima
Te gustan las siguientes frutas:
  - naranja
  - uva
  - durazno
```

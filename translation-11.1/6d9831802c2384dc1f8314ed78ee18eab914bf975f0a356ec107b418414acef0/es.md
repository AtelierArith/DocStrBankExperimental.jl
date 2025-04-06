```
var
```

La sintaxis `var"#example#"` se refiere a una variable llamada `Symbol("#example#")`, aunque `#example#` no sea un nombre de identificador válido en Julia.

Esto puede ser útil para la interoperabilidad con lenguajes de programación que tienen diferentes reglas para la construcción de identificadores válidos. Por ejemplo, para referirse a la variable `R` `draw.segments`, puedes usar `var"draw.segments"` en tu código Julia.

También se utiliza para `show` el código fuente de Julia que ha pasado por la higiene de macros o que de otro modo contiene nombres de variables que no se pueden analizar normalmente.

Ten en cuenta que esta sintaxis requiere soporte del analizador, por lo que se expande directamente por el analizador en lugar de implementarse como una macro de cadena normal `@var_str`.

!!! compat "Julia 1.3"
    Esta sintaxis requiere al menos Julia 1.3.


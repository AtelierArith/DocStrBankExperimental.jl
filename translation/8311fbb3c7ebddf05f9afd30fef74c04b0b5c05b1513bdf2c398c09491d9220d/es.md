```
@r_str -> Regex
```

Construya una expresión regular, como `r"^[a-z]*$"`, sin interpolación y sin desescapar (excepto por la comilla `"` que aún debe ser escapada). La expresión regular también acepta una o más banderas, listadas después de la comilla final, para cambiar su comportamiento:

  * `i` habilita la coincidencia sin distinción entre mayúsculas y minúsculas
  * `m` trata los tokens `^` y `$` como coincidiendo con el inicio y el final de líneas individuales, en lugar de toda la cadena.
  * `s` permite que el modificador `.` coincida con nuevas líneas.
  * `x` habilita el "modo de espacio libre": los espacios en blanco entre los tokens de la expresión regular se ignoran, excepto cuando están escapados con `\`, y `#` en la expresión regular se trata como el inicio de un comentario (que se ignora hasta el final de la línea).
  * `a` habilita el modo ASCII (desactiva los modos `UTF` y `UCP`). Por defecto, `\B`, `\b`, `\D`, `\d`, `\S`, `\s`, `\W`, `\w`, etc. coinciden según las propiedades de los caracteres Unicode. Con esta opción, estas secuencias solo coinciden con caracteres ASCII. Esto incluye `\u` también, que emitirá el valor de carácter especificado directamente como un solo byte, y no intentará codificarlo en UTF-8. Importante, esta opción permite coincidir con cadenas UTF-8 no válidas, tratando tanto el coincididor como el objetivo como bytes simples (como si fueran bytes ISO/IEC 8859-1 / Latin-1) en lugar de como codificaciones de caracteres. En este caso, esta opción a menudo se combina con `s`. Esta opción se puede refinar aún más comenzando el patrón con (*UCP) o (*UTF).

Consulte [`Regex`](@ref) si se necesita interpolación.

# Ejemplos

```jldoctest
julia> match(r"a+.*b+.*?d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Esta expresión regular tiene habilitadas las tres primeras banderas.

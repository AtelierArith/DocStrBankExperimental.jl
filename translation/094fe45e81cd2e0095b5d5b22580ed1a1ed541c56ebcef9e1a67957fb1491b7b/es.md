```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

Normaliza la cadena `s`. Por defecto, se realiza la composición canónica (`compose=true`) sin garantizar la estabilidad de la versión de Unicode (`compat=false`), lo que produce la cadena equivalente más corta posible, pero puede introducir caracteres de composición que no están presentes en versiones anteriores de Unicode.

Alternativamente, se puede especificar una de las cuatro "formas normales" del estándar Unicode: `normalform` puede ser `:NFC`, `:NFD`, `:NFKC` o `:NFKD`. Las formas normales C (composición canónica) y D (decomposición canónica) convierten diferentes representaciones visualmente idénticas de la misma cadena abstracta en una única forma canónica, siendo la forma C más compacta. Las formas normales KC y KD además canonizan "equivalentes de compatibilidad": convierten caracteres que son abstractamente similares pero visualmente distintos en una única elección canónica (por ejemplo, expanden ligaduras en los caracteres individuales), siendo la forma KC más compacta.

Alternativamente, se puede obtener un control más fino y transformaciones adicionales llamando a `Unicode.normalize(s; keywords...)`, donde se especifica cualquier número de las siguientes opciones booleanas de palabras clave (que todas tienen un valor predeterminado de `false` excepto `compose`):

  * `compose=false`: no realizar composición canónica
  * `decompose=true`: realizar decomposición canónica en lugar de composición canónica (`compose=true` se ignora si está presente)
  * `compat=true`: los equivalentes de compatibilidad son canonizados
  * `casefold=true`: realizar plegado de mayúsculas de Unicode, por ejemplo, para comparación de cadenas sin distinción de mayúsculas
  * `newline2lf=true`, `newline2ls=true` o `newline2ps=true`: convertir varias secuencias de nueva línea (LF, CRLF, CR, NEL) en un carácter de salto de línea (LF), separación de líneas (LS) o separación de párrafos (PS), respectivamente
  * `stripmark=true`: eliminar marcas diacríticas (por ejemplo, acentos)
  * `stripignore=true`: eliminar los caracteres "ignorables por defecto" de Unicode (por ejemplo, el guion suave o el marcador de izquierda a derecha)
  * `stripcc=true`: eliminar caracteres de control; los tabuladores horizontales y los avances de formulario se convierten en espacios; las nuevas líneas también se convierten en espacios a menos que se haya especificado una bandera de conversión de nueva línea
  * `rejectna=true`: lanzar un error si se encuentran puntos de código no asignados
  * `stable=true`: hacer cumplir la estabilidad de la versión de Unicode (nunca introducir caracteres que falten en versiones anteriores de Unicode)

También puedes usar la palabra clave `chartransform` (que tiene un valor predeterminado de `identity`) para pasar una *función* arbitraria que mapea puntos de código `Integer` a puntos de código, que se llama en cada carácter de `s` a medida que se procesa, con el fin de realizar normalizaciones adicionales arbitrarias. Por ejemplo, al pasar `chartransform=Unicode.julia_chartransform`, puedes aplicar algunas normalizaciones de caracteres específicas de Julia que se realizan al analizar identificadores (además de la normalización NFC: `compose=true, stable=true`).

Por ejemplo, NFKC corresponde a las opciones `compose=true, compat=true, stable=true`.

# Ejemplos

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    El argumento de palabra clave `chartransform` requiere Julia 1.8.


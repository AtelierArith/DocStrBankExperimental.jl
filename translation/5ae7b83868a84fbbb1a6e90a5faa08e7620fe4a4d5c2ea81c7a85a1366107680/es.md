El tipo `AbstractString` es el supertipo de todas las implementaciones de cadenas en Julia. Las cadenas son codificaciones de secuencias de puntos de código de [Unicode](https://unicode.org/) tal como se representan mediante el tipo `AbstractChar`. Julia hace algunas suposiciones sobre las cadenas:

  * Las cadenas están codificadas en términos de "unidades de código" de tamaño fijo.

      * Las unidades de código se pueden extraer con `codeunit(s, i)`
      * La primera unidad de código tiene índice `1`
      * La última unidad de código tiene índice `ncodeunits(s)`
      * Cualquier índice `i` tal que `1 ≤ i ≤ ncodeunits(s)` está dentro de los límites
  * La indexación de cadenas se realiza en términos de estas unidades de código:

      * Los caracteres se extraen mediante `s[i]` con un índice de cadena válido `i`
      * Cada `AbstractChar` en una cadena está codificado por una o más unidades de código
      * Solo el índice de la primera unidad de código de un `AbstractChar` es un índice válido
      * La codificación de un `AbstractChar` es independiente de lo que lo precede o lo sigue
      * Las codificaciones de cadenas son [auto-sincronizadoras](https://es.wikipedia.org/wiki/C%C3%B3digo_auto-sincronizador) – es decir, `isvalid(s, i)` es O(1)

Algunas funciones de cadena que extraen unidades de código, caracteres o subcadenas de cadenas generan un error si les pasas índices de cadena fuera de los límites o inválidos. Esto incluye `codeunit(s, i)` y `s[i]`. Las funciones que realizan aritmética de índices de cadena adoptan un enfoque más relajado para la indexación y te dan el índice de cadena válido más cercano cuando está dentro de los límites, o cuando está fuera de los límites, se comportan como si hubiera un número infinito de caracteres que rellenan cada lado de la cadena. Por lo general, estos caracteres de relleno imaginarios tienen una longitud de unidad de código de `1`, pero los tipos de cadena pueden elegir diferentes tamaños de "caracteres" "imaginarios" según lo que tenga sentido para sus implementaciones (por ejemplo, las subcadenas pueden pasar la aritmética de índices a la cadena subyacente a la que proporcionan una vista). Las funciones de indexación relajada incluyen aquellas destinadas a la aritmética de índices: `thisind`, `nextind` y `prevind`. Este modelo permite que la aritmética de índices funcione con índices fuera de los límites como valores intermedios siempre que nunca se usen para recuperar un carácter, lo que a menudo ayuda a evitar la necesidad de codificar alrededor de casos límite.

Consulta también [`codeunit`](@ref), [`ncodeunits`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

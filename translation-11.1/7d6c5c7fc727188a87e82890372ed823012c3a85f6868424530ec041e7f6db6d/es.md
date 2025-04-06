Una [`Face`](@ref) es una colección de atributos gráficos para mostrar texto. Las caras controlan cómo se muestra el texto en la terminal, y posiblemente en otros lugares también.

La mayoría de las veces, una [`Face`](@ref) se almacenará en los diccionarios globales de caras como una asociación única con un *nombre de cara* Symbol, y se referirá a menudo por este nombre en lugar del objeto [`Face`](@ref) en sí.

# Atributos

Todos los atributos se pueden establecer a través del constructor de palabras clave y por defecto son `nothing`.

  * `height` (un `Int` o `Float64`): La altura en deci-pt (cuando es un `Int`), o como un factor del tamaño base (cuando es un `Float64`).
  * `weight` (un `Symbol`): Uno de los símbolos (de más tenue a más denso) `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold`, o `:black`. En las terminales, cualquier peso mayor que `:normal` se muestra como negrita, y en las terminales que soportan texto de brillo variable, cualquier peso menor que `:normal` se muestra como tenue.
  * `slant` (un `Symbol`): Uno de los símbolos `:italic`, `:oblique`, o `:normal`.
  * `foreground` (un `SimpleColor`): El color del primer plano del texto.
  * `background` (un `SimpleColor`): El color de fondo del texto.
  * `underline`, el subrayado del texto, que toma una de las siguientes formas:

      * un `Bool`: Si el texto debe estar subrayado o no.
      * un `SimpleColor`: El texto debe estar subrayado con este color.
      * un `Tuple{Nothing, Symbol}`: El texto debe estar subrayado utilizando el estilo establecido por el Symbol, uno de `:straight`, `:double`, `:curly`, `:dotted`, o `:dashed`.
      * un `Tuple{SimpleColor, Symbol}`: El texto debe estar subrayado en el SimpleColor especificado, y utilizando el estilo especificado por el Symbol, como antes.
  * `strikethrough` (un `Bool`): Si el texto debe estar tachado.
  * `inverse` (un `Bool`): Si los colores de primer plano y fondo deben ser invertidos.
  * `inherit` (un `Vector{Symbol}`): Nombres de caras de las que heredar, con las caras anteriores tomando prioridad. Todas las caras heredan de la cara `:default`.

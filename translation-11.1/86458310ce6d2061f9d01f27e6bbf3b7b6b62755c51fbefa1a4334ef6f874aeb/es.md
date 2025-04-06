```
==(x, y)
```

Operador de igualdad genérico. Recurre a [`===`](@ref). Debe ser implementado para todos los tipos con una noción de igualdad, basada en el valor abstracto que representa una instancia. Por ejemplo, todos los tipos numéricos se comparan por valor numérico, ignorando el tipo. Las cadenas se comparan como secuencias de caracteres, ignorando la codificación. Las colecciones del mismo tipo generalmente comparan sus conjuntos de claves, y si esos son `==`, entonces comparan los valores para cada una de esas claves, devolviendo verdadero si todos esos pares son `==`. Otras propiedades generalmente no se tienen en cuenta (como el tipo exacto).

Este operador sigue la semántica IEEE para números de punto flotante: `0.0 == -0.0` y `NaN != NaN`.

El resultado es de tipo `Bool`, excepto cuando uno de los operandos es [`missing`](@ref), en cuyo caso se devuelve `missing` ([lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores)). Las colecciones generalmente implementan lógica de tres valores similar a [`all`](@ref), devolviendo missing si alguno de los operandos contiene valores missing y todos los demás pares son iguales. Usa [`isequal`](@ref) o [`===`](@ref) para obtener siempre un resultado de tipo `Bool`.

# Implementación

Los nuevos tipos numéricos deben implementar esta función para dos argumentos del nuevo tipo, y manejar la comparación con otros tipos a través de reglas de promoción cuando sea posible.

[`isequal`](@ref) recurre a `==`, por lo que los nuevos métodos de `==` serán utilizados por el tipo [`Dict`](@ref) para comparar claves. Si tu tipo se utilizará como clave de diccionario, también debe implementar [`hash`](@ref).

Si algún tipo define `==`, [`isequal`](@ref) y [`isless`](@ref), entonces también debe implementar [`<`](@ref) para asegurar la consistencia de las comparaciones.

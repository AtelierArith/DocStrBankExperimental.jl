```
x::EscapeInfo
```

Una red para información de escape, que tiene las siguientes propiedades:

  * `x.Analyzed::Bool`: no es parte formal de la red, solo indica si `x` ha sido analizado
  * `x.ReturnEscape::Bool`: indica que `x` puede escapar al llamador a través de un retorno
  * `x.ThrownEscape::BitSet`: registra los números de declaración SSA donde `x` puede ser lanzado como excepción:

      * `isempty(x.ThrownEscape)`: `x` nunca será lanzado en este marco de llamada (el fondo)
      * `pc ∈ x.ThrownEscape`: `x` puede ser lanzado en la declaración SSA en `pc`
      * `-1 ∈ x.ThrownEscape`: `x` puede ser lanzado en puntos arbitrarios de este marco de llamada (la parte superior)

    Esta información será utilizada por `escape_exception!` para propagar escapes potenciales a través de excepciones.
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`: mantiene todos los posibles valores que pueden ser referenciados a campos o elementos de arreglo de `x`:

      * `x.AliasInfo === false` indica que los campos/elementos de `x` aún no han sido analizados
      * `x.AliasInfo === true` indica que los campos/elementos de `x` no pueden ser analizados, por ejemplo, el tipo de `x` no es conocido o no es concreto y, por lo tanto, sus campos/elementos no pueden ser conocidos con precisión
      * `x.AliasInfo::IndexableFields` registra todos los posibles valores que pueden ser referenciados a campos del objeto `x` con información de índice precisa
      * `x.AliasInfo::IndexableElements` registra todos los posibles valores que pueden ser referenciados a elementos del arreglo `x` con información de índice precisa
      * `x.AliasInfo::Unindexable` registra todos los posibles valores que pueden ser referenciados a campos/elementos de `x` sin información de índice precisa
  * `x.Liveness::BitSet`: registra los números de declaración SSA donde `x` debería estar vivo, por ejemplo, para ser utilizado como argumento de llamada, para ser devuelto a un llamador, o preservado para `:foreigncall`:

      * `isempty(x.Liveness)`: `x` nunca será utilizado en este marco de llamada (el fondo)
      * `0 ∈ x.Liveness` también tiene el significado especial de que es un argumento de llamada del marco de llamada actualmente analizado (y por lo tanto es visible desde el llamador inmediatamente).
      * `pc ∈ x.Liveness`: `x` puede ser utilizado en la declaración SSA en `pc`
      * `-1 ∈ x.Liveness`: `x` puede ser utilizado en puntos arbitrarios de este marco de llamada (la parte superior)

Hay constructores utilitarios para crear `EscapeInfo`s comunes, por ejemplo,

  * `NoEscape()`: el elemento inferior (similar) de esta red, lo que significa que no escapará a ningún lugar
  * `AllEscape()`: el elemento más alto de esta red, lo que significa que escapará a todas partes

`analyze_escapes` hará la transición de estos elementos del fondo a la parte superior, en la misma dirección que la rutina de inferencia de tipos nativa de Julia. Un estado abstracto será inicializado con los elementos inferiores (similares):

  * los argumentos de llamada se inicializan como `ArgEscape()`, cuya propiedad `Liveness` incluye `0` para indicar que se pasa como un argumento de llamada y es visible desde un llamador inmediatamente
  * los otros estados se inicializan como `NotAnalyzed()`, que es un elemento de red especial que es ligeramente inferior a `NoEscape`, pero al mismo tiempo no representa ningún significado más allá de que aún no ha sido analizado (por lo tanto, no es parte formal de la red)

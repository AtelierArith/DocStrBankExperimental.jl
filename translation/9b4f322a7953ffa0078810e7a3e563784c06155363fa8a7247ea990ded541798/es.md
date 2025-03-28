# High-level Overview of the Native-Code Generation Process

## Representation of Pointers

Al emitir código a un archivo objeto, los punteros se emitirán como reubicaciones. El código de deserialización se asegurará de que cualquier objeto que apuntara a una de estas constantes se recree y contenga el puntero de tiempo de ejecución correcto.

De lo contrario, se emitirán como constantes literales.

Para emitir uno de estos objetos, llama a `literal_pointer_val`. Se encargará de rastrear el valor de Julia y el global de LLVM, asegurando que sean válidos tanto para el tiempo de ejecución actual como después de la deserialización.

Cuando se emiten en el archivo objeto, estos globales se almacenan como referencias en una gran tabla `gvals`. Esto permite que el deserializador se refiera a ellos por índice e implemente un mecanismo manual personalizado similar a una Tabla de Desplazamiento Global (GOT) para restaurarlos.

Los punteros a funciones se manejan de manera similar. Se almacenan como valores en una gran tabla `fvals`. Al igual que las variables globales, esto permite que el deserializador se refiera a ellos por índice.

Tenga en cuenta que las funciones `extern` se manejan por separado, con nombres, a través del mecanismo habitual de resolución de símbolos en el enlazador.

Nota también que las funciones `ccall` se manejan por separado, a través de una tabla de símbolos manual y una tabla de enlace de procedimientos (PLT).

## Representation of Intermediate Values

Los valores se pasan en una estructura `jl_cgval_t`. Esto representa un valor R y contiene suficiente información para determinar cómo asignarlo o pasarlo a algún lugar.

Se crean a través de uno de los constructores auxiliares, generalmente: `mark_julia_type` (para valores inmediatos) y `mark_julia_slot` (para punteros a valores).

La función `convert_julia_type` puede transformar entre cualquier par de tipos. Devuelve un valor R con `cgval.typ` establecido en `typ`. Convertirá el objeto a la representación solicitada, creando cajas en el heap, asignando copias en la pila y computando uniones etiquetadas según sea necesario para cambiar la representación.

Por el contrario, `update_julia_type` cambiará `cgval.typ` a `typ`, solo si se puede hacer sin costo (es decir, sin emitir ningún código).

## Union representation

Los tipos de unión inferidos pueden ser asignados en la pila a través de una representación de tipo etiquetado.

Las rutinas primitivas que deben ser capaces de manejar uniones etiquetadas son:

  * tipo-de-marca
  * cargar-local
  * almacenar-local
  * isa
  * es
  * emit_typeof
  * emit_sizeof
  * cajado
  * desempaquetar
  * especializado cc-ret

Todo lo demás debería ser posible de manejar en la inferencia utilizando estos primitivos para implementar la división de uniones.

La representación de la unión etiquetada es como un par de `< void* unión, byte selector >`. El selector tiene un tamaño fijo de `byte & 0x7f`, y etiquetará la unión de los primeros 126 isbits. Registra el conteo en profundidad basado en uno dentro de la unión de tipos de los objetos isbits dentro. Un índice de cero indica que el `union*` es en realidad un `jl_value_t*` asignado en el montón con etiqueta, y debe ser tratado como un objeto empaquetado normal en lugar de como una unión etiquetada.

El bit alto del selector (`byte & 0x80`) se puede probar para determinar si el `void*` es en realidad una caja asignada en el montón (`jl_value_t*`), evitando así el costo de reasignar una caja, mientras se mantiene la capacidad de manejar de manera eficiente la división de uniones basada en los bits bajos.

Se garantiza que `byte & 0x7f` es una prueba exacta para el tipo, si el valor puede ser representado por una etiqueta; nunca estará marcado `byte = 0x80`. No es necesario probar también la etiqueta de tipo al probar `isa`.

La región de memoria `union*` puede ser asignada a *cualquier* tamaño. La única restricción es que sea lo suficientemente grande para contener los datos actualmente especificados por `selector`. Puede que no sea lo suficientemente grande para contener la unión de todos los tipos que podrían almacenarse allí según el campo de tipo Union asociado. Use el cuidado apropiado al copiar.

## Specialized Calling Convention Signature Representation

Un objeto `jl_returninfo_t` describe los detalles de la convención de llamada de cualquier función callable.

Si alguno de los argumentos o el tipo de retorno de un método puede ser representado sin caja, y el método no es varargs, se le dará una firma de convención de llamada optimizada basada en sus campos `specTypes` y `rettype`.

Los principios generales son que:

  * Los tipos primitivos se pasan en registros de int/float.
  * Las tuplas de tipos VecElement se pasan en registros de vector.
  * Las estructuras se pasan en la pila.
  * Los valores de retorno se manejan de manera similar a los argumentos, con un límite de tamaño a partir del cual se devolverán a través de un argumento sret oculto.

La lógica total para esto está implementada por `get_specsig_function` y `deserves_sret`.

Además, si el tipo de retorno es una unión, puede ser devuelto como un par de valores (un puntero y una etiqueta). Si los valores de la unión se pueden asignar en la pila, entonces se pasará suficiente espacio para almacenarlos como un primer argumento oculto. Dependerá del llamado si el puntero devuelto apuntará a este espacio, a un objeto empaquetado o incluso a otra memoria constante.

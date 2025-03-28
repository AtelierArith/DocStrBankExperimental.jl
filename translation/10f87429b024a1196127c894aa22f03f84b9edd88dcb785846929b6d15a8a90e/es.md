# Calling Conventions

Julia utiliza tres convenciones de llamada para cuatro propósitos distintos:

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

La convención de llamada nativa está diseñada para llamadas rápidas no genéricas. Generalmente utiliza una firma especializada.

  * Los fantasmas de LLVM (tipos de longitud cero) se omiten.
  * Los escalares y vectores de LLVM se pasan por valor.
  * Los agregados de LLVM (arreglos y estructuras) se pasan por referencia.

Un pequeño valor de retorno se devuelve como valores de retorno de LLVM. Un valor de retorno grande se devuelve a través de la convención de "retorno de estructura" (`sret`), donde el llamador proporciona un puntero a un espacio de retorno.

Un argumento o valores de retorno que son una tupla homogénea a veces se representan como un vector de LLVM en lugar de un arreglo de LLVM.

## JL Call Convention

La convención JL Call es para funciones integradas y despacho genérico. Las funciones escritas a mano que utilizan esta convención se declaran a través de la macro `JL_CALLABLE`. La convención utiliza exactamente 3 parámetros:

  * `F`  - Representación de Julia de la función que se está aplicando
  * `args` - puntero a un arreglo de punteros a cajas
  * `nargs` - longitud del arreglo

El valor de retorno es un puntero a una caja.

## C ABI

Los envoltorios de C ABI permiten llamar a Julia desde C. El envoltorio llama a una función utilizando la convención de llamada nativa.

Las tuplas siempre se representan como arreglos de C.

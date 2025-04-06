# Julia ASTs

Julia tiene dos representaciones de código. Primero hay un AST de sintaxis superficial devuelto por el analizador (por ejemplo, la función [`Meta.parse`](@ref)), y manipulado por macros. Es una representación estructurada del código tal como está escrito, construida por `julia-parser.scm` a partir de un flujo de caracteres. A continuación, hay una forma reducida, o IR (representación intermedia), que es utilizada por la inferencia de tipos y la generación de código. En la forma reducida hay menos tipos de nodos, todas las macros están expandidas, y todo el flujo de control se convierte en ramas explícitas y secuencias de declaraciones. La forma reducida es construida por `julia-syntax.scm`.

Primero nos centraremos en el AST, ya que se necesita para escribir macros.

## Surface syntax AST

Los ASTs de front end consisten casi en su totalidad de [`Expr`](@ref)s y átomos (por ejemplo, símbolos, números). Generalmente hay una cabeza de expresión diferente para cada forma sintáctica visualmente distinta. Se darán ejemplos en la sintaxis de s-expresión. Cada lista entre paréntesis corresponde a un Expr, donde el primer elemento es la cabeza. Por ejemplo, `(call f x)` corresponde a `Expr(:call, :f, :x)` en Julia.

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` sintaxis:

```julia
f(x) do a,b
    body
end
```

parses como `(do (call f x) (-> (tuple a b) (block body)))`.

### Operators

La mayoría de los usos de los operadores son simplemente llamadas a funciones, por lo que se analizan con la cabeza `call`. Sin embargo, algunos operadores son formas especiales (no necesariamente llamadas a funciones), y en esos casos el operador en sí es la cabeza de la expresión. En julia-parser.scm, estos se denominan "operadores sintácticos". Algunos operadores (`+` y `*`) utilizan análisis N-ario; las llamadas encadenadas se analizan como una única llamada con N argumentos. Finalmente, las cadenas de comparaciones tienen su propia estructura de expresión especial.

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

Sintaxis de docstring:

```julia
"some docs"
f(x) = x
```

parses como `(macrocall (|.| Core '@doc) (line) "some docs" (= (call f x) (block x)))`.

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using` tiene la misma representación que `import`, pero con el encabezado de expresión `:using` en lugar de `:import`.

### Numbers

Julia admite más tipos de números que muchas implementaciones de Scheme, por lo que no todos los números se representan directamente como números de Scheme en el AST.

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

Un bloque de declaraciones se analiza como `(bloque stmt1 stmt2 ...)`.

Si declaración:

```julia
if a
    b
elseif c
    d
else
    e
end
```

parses como:

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

Un bucle `while` se analiza como `(while condición cuerpo)`.

Un bucle `for` se analiza como `(for (= var iter) body)`. Si hay más de una especificación de iteración, se analizan como un bloque: `(for (block (= v1 iter1) (= v2 iter2)) body)`.

`break` y `continue` se analizan como expresiones de 0 argumentos `(break)` y `(continue)`.

`let` se analiza como `(let (= var val) body)` o `(let (block (= var1 val1) (= var2 val2) ...) body)`, al igual que los bucles `for`.

Una definición de función básica se analiza como `(function (call f x) body)`. Un ejemplo más complejo:

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

parses como:

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

Definición de tipo:

```julia
mutable struct Foo{T<:S}
    x::T
end
```

parses como:

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

El primer argumento es un booleano que indica si el tipo es mutable.

`try` bloques se analizan como `(try try_block var catch_block finally_block)`. Si no hay una variable presente después de `catch`, `var` es `#f`. Si no hay una cláusula `finally`, entonces el último argumento no está presente.

### Quote expressions

Las formas de sintaxis de código de Julia para la cita de código (`quote` y `:( )`) admiten la interpolación con `$`. En la terminología de Lisp, esto significa que en realidad son formas de "backquote" o "quasiquote". Internamente, también existe la necesidad de citar código sin interpolación. En el esquema de código de Julia, la cita no interpolante se representa con la cabeza de expresión `inert`.

Las expresiones `inert` se convierten en objetos `QuoteNode` de Julia. Estos objetos envuelven un solo valor de cualquier tipo y, cuando se evalúan, simplemente devuelven ese valor.

Una expresión de `quote` cuyo argumento es un átomo también se convierte en un `QuoteNode`.

### Line numbers

La información de ubicación de origen se representa como `(línea line_num nombre_archivo)` donde el tercer componente es opcional (y se omite cuando el número de línea actual, pero no el nombre del archivo, cambia).

Estas expresiones se representan como `LineNumberNode`s en Julia.

### Macros

La higiene de macros se representa a través de la expresión de par de encabezado `escape` y `hygienic-scope`. El resultado de una expansión de macro se envuelve automáticamente en `(hygienic-scope block module)`, para representar el resultado del nuevo alcance. El usuario puede insertar `(escape block)` dentro para interpolar código del llamador.

## Lowered form

La forma reducida (IR) es más importante para el compilador, ya que se utiliza para la inferencia de tipos, optimizaciones como la inserción en línea y la generación de código. También es menos obvia para el ser humano, ya que resulta de un reordenamiento significativo de la sintaxis de entrada.

Además de los `Symbol`s y algunos tipos de números, existen los siguientes tipos de datos en forma reducida:

  * `Expr`

    Tiene un tipo de nodo indicado por el campo `head`, y un campo `args` que es un `Vector{Any}` de subexpresiones. Mientras que casi cada parte de un AST superficial está representada por un `Expr`, el IR utiliza solo un número limitado de `Expr`s, principalmente para llamadas y algunas formas que solo están en el nivel superior.
  * `NúmeroDeSlot`

    Identifica argumentos y variables locales mediante numeración consecutiva. Tiene un campo `id` de tipo entero que indica el índice de la ranura. Los tipos de estas ranuras se pueden encontrar en el campo `slottypes` de su objeto `CodeInfo`.
  * `Argumento`

    Lo mismo que `SlotNumber`, pero aparece solo después de la optimización. Indica que el slot referenciado es un argumento de la función que lo contiene.
  * `InformaciónDelCódigo`

    Envuelve el IR de un grupo de declaraciones. Su campo `code` es un array de expresiones a ejecutar.
  * `IrAElNodo`

    Rama incondicional. El argumento es el objetivo de la rama, representado como un índice en el array de código al que saltar.
  * `GotoIfNot`

    Rama condicional. Si el campo `cond` evalúa a falso, va al índice identificado por el campo `dest`.
  * `ReturnNode`

    Devuelve su argumento (el campo `val`) como el valor de la función envolvente. Si el campo `val` es indefinido, entonces esto representa una declaración inalcanzable.
  * `QuoteNode`

    Envuelve un valor arbitrario para referenciarlo como datos. Por ejemplo, la función `f() = :a` contiene un `QuoteNode` cuyo campo `value` es el símbolo `a`, con el fin de devolver el símbolo en sí en lugar de evaluarlo.
  * `GlobalRef`

    Se refiere a la variable global `name` en el módulo `mod`.
  * `SSAValue`

    Se refiere a una variable de asignación única estática (SSA) numerada de forma consecutiva (comenzando en 1) insertada por el compilador. El número (`id`) de un `SSAValue` es el índice del arreglo de código de la expresión cuyo valor representa.
  * `NewvarNode`

    Marca un punto donde se crea una variable (slot). Esto tiene el efecto de restablecer una variable a indefinido.

### `Expr` types

Estos símbolos aparecen en el campo `head` de [`Expr`](@ref) en forma minúscula.

  * `llamar`

    Llamada a función (despacho dinámico). `args[1]` es la función a llamar, `args[2:end]` son los argumentos.
  * `invocar`

    Llamada a función (despacho estático). `args[1]` es la instancia del método a llamar, `args[2:end]` son los argumentos (incluyendo la función que se está llamando, en `args[2]`).
  * `static_parameter`

    Referencia un parámetro estático por índice.
  * `=`

    Asignación. En el IR, el primer argumento es siempre un `SlotNumber` o un `GlobalRef`.
  * `método`

    Agrega un método a una función genérica y asigna el resultado si es necesario.

    Tiene una forma de 1 argumento y una forma de 3 argumentos. La forma de 1 argumento surge de la sintaxis `function foo end`. En la forma de 1 argumento, el argumento es un símbolo. Si este símbolo ya nombra una función en el ámbito actual, no sucede nada. Si el símbolo está indefinido, se crea una nueva función y se asigna al identificador especificado por el símbolo. Si el símbolo está definido pero nombra algo que no es una función, se genera un error. La definición de "nombra una función" es que la vinculación es constante y se refiere a un objeto de tipo singleton. La razón de esto es que una instancia de un tipo singleton identifica de manera única el tipo al que se debe agregar el método. Cuando el tipo tiene campos, no estaría claro si el método se está agregando a la instancia o a su tipo.

    La forma de 3 argumentos tiene los siguientes argumentos:

      * `args[1]`

        Un nombre de función, o `nada` si es desconocido o innecesario. Si es un símbolo, entonces la expresión se comporta primero como la forma de 1 argumento mencionada anteriormente. Este argumento se ignora a partir de ese momento. Puede ser `nada` cuando se añaden métodos estrictamente por tipo, `(::T)(x) = x`, o cuando se está añadiendo un método a una función existente, `MyModule.f(x) = x`.
      * `args[2]`

        Un `SimpleVector` del tipo de argumento de datos. `args[2][1]` es un `SimpleVector` de los tipos de argumento, y `args[2][2]` es un `SimpleVector` de variables de tipo correspondientes a los parámetros estáticos del método.
      * `args[3]`

        Un `CodeInfo` del método en sí. Para definiciones de métodos "fuera de alcance" (agregar un método a una función que también tiene métodos definidos en diferentes ámbitos) esta es una expresión que se evalúa a una expresión `:lambda`.
  * `tipo_de_estructura`

    Una expresión de 7 argumentos que define una nueva `struct`:

      * `args[1]`

        El nombre del `struct`
      * `args[2]`

        Una expresión `call` que crea un `SimpleVector` especificando sus parámetros
      * `args[3]`

        Una expresión `call` que crea un `SimpleVector` especificando sus nombres de campo.
      * `args[4]`

        Un `Symbol`, `GlobalRef` o `Expr` que especifica el supertipo (por ejemplo, `:Integer`, `GlobalRef(Core, :Any)` o `:(Core.apply_type(AbstractArray, T, N))`)
      * `args[5]`

        Una expresión `call` que crea un `SimpleVector` especificando sus tipos de campo.
      * `args[6]`

        Un Bool, verdadero si `mutable`
      * `args[7]`

        El número de argumentos para inicializar. Este será el número de campos, o el número mínimo de campos llamados por la declaración `new` de un constructor interno.
  * `tipo_abstracto`

    Una expresión de 3 argumentos que define un nuevo tipo abstracto. Los argumentos son los mismos que los argumentos 1, 2 y 4 de las expresiones `struct_type`.
  * `tipo_primitivo`

    Una expresión de 4 argumentos que define un nuevo tipo primitivo. Los argumentos 1, 2 y 4 son los mismos que `struct_type`. El argumento 3 es el número de bits.

    !!! compat "Julia 1.5"
        `struct_type`, `abstract_type` y `primitive_type` fueron eliminados en Julia 1.5 y reemplazados por llamadas a nuevos elementos incorporados.
  * `global`

    Declara un enlace global.
  * `const`

    Declara una variable (global) como constante.
  * `nuevo`

    Asigna un nuevo objeto similar a una estructura. El primer argumento es el tipo. La pseudo-función [`new`](@ref) se reduce a esto, y el tipo siempre es insertado por el compilador. Esta es una característica que es muy interna y no realiza ninguna verificación. Evaluar expresiones `new` arbitrarias puede causar fácilmente un fallo de segmentación.
  * `splatnew`

    Similar a `new`, excepto que los valores de los campos se pasan como una única tupla. Funciona de manera similar a `splat(new)` si `new` fuera una función de primera clase, de ahí el nombre.
  * `está definido`

    `Expr(:isdefined, :x)` devuelve un Bool que indica si `x` ya ha sido definido en el ámbito actual.
  * `la_excepción`

    Devuelve la excepción capturada dentro de un bloque `catch`, tal como lo devuelve `jl_current_exception(ct)`.
  * `entrar`

    Entra en un manejador de excepciones (`setjmp`). `args[1]` es la etiqueta del bloque catch al que saltar en caso de error. Produce un token que es consumido por `pop_exception`.
  * `dejar`

    Pop excepciones manejadoras. `args[1]` es el número de manejadoras a eliminar.
  * `pop_exception`

    Restablecer la pila de excepciones actuales al estado en el `enter` asociado al salir de un bloque catch. `args[1]` contiene el token del `enter` asociado.

    !!! compat "Julia 1.1"
        `pop_exception` es nuevo en Julia 1.1.
  * `entrantes`

    Controles para activar o desactivar las comprobaciones de límites. Se mantiene una pila; si el primer argumento de esta expresión es verdadero o falso (`true` significa que las comprobaciones de límites están desactivadas), se empuja en la pila. Si el primer argumento es `:pop`, se saca de la pila.
  * `boundscheck`

    Tiene el valor `false` si se inserta en una sección de código marcada con `@inbounds`, de lo contrario tiene el valor `true`.
  * `loopinfo`

    Marca el final de un bucle. Contiene metadatos que se pasan a `LowerSimdLoop` para marcar el bucle interno de una expresión `@simd`, o para propagar información a las pasadas de bucle de LLVM.
  * `copyast`

    Parte de la implementación de cuasi-cita. El argumento es un AST de sintaxis superficial que se copia simplemente de forma recursiva y se devuelve en tiempo de ejecución.
  * `meta`

    Metadatos. `args[1]` es típicamente un símbolo que especifica el tipo de metadatos, y el resto de los argumentos son de formato libre. Los siguientes tipos de metadatos son comúnmente utilizados:

      * `:inline` y `:noinline`: Sugerencias de inlining.
  * `llamadaexterior`

    Contenedor computado estáticamente para la información de `ccall`. Los campos son:

      * `args[1]` : nombre

        La expresión que se analizará para la función externa.
      * `args[2]::Type` : RT

        El tipo de retorno (literal), calculado estáticamente cuando se definió el método que lo contiene.
      * `args[3]::SimpleVector` (de Tipos) : AT

        El vector (literal) de tipos de argumento, calculado estáticamente cuando se definió el método que lo contiene.
      * `args[4]::Int` : nreq

        El número de argumentos requeridos para una definición de función varargs.
      * `args[5]::QuoteNode{Symbol}` : convención de llamada

        La convención de llamada para la llamada.
      * `args[6:5+length(args[3])]` : argumentos

        Los valores para todos los argumentos (con los tipos de cada uno dados en args[3]).
      * `args[6+length(args[3])+1:end]` : raíces-gc

        Los objetos adicionales que pueden necesitar ser gc-rooted durante la duración de la llamada. Consulte [Working with LLVM](@ref Working-with-LLVM) para ver de dónde se derivan y cómo se manejan.
  * `nuevo_cierre_opaco`

    Construye un nuevo cierre opaco. Los campos son:

      * `args[1]` : firma

        La firma de función del cierre opaco. Los cierres opacos no participan en la distribución, pero los tipos de entrada pueden ser restringidos.
      * `args[2]` : isva

        Indica si el cierre acepta varargs.
      * `args[3]` : lb

        Límite inferior en el tipo de salida. (Por defecto `Union{}`)
      * `args[4]` : ub

        Límite superior en el tipo de salida. (Por defecto es `Any`)
      * `args[5]` : método

        El método real como una expresión `opaque_closure_method`.
      * `args[6:end]` : captura

        Los valores capturados por el cierre opaco.

    !!! compat "Julia 1.7"
        Las cierres opacos se añadieron en Julia 1.7

### [Method](@id ast-lowered-method)

Un contenedor único que describe los metadatos compartidos para un único método.

  * `nombre`, `módulo`, `archivo`, `línea`, `firma`

    Metadatos para identificar de manera única el método para la computadora y el humano.
  * `ambig`

    Cache de otros métodos que pueden ser ambiguos con este.
  * `especializaciones`

    Cache de todas las instancias de método creadas para este método, utilizado para garantizar la unicidad. La unicidad es necesaria para la eficiencia, especialmente para la precompilación incremental y el seguimiento de la invalidación del método.
  * `fuente`

    El código fuente original (si está disponible, generalmente comprimido).
  * `generador`

    Un objeto llamable que se puede ejecutar para obtener una fuente especializada para una firma de método específica.
  * `raíces`

    Punteros a cosas que no son AST que han sido interpoladas en el AST, requeridas por la compresión del AST, la inferencia de tipos o la generación de código nativo.
  * `nargs`, `isva`, `called`, `is_for_opaque_closure`,

    Campos de bits descriptivos para el código fuente de este método.
  * `mundo_principal`

    La era del mundo que "posee" este Método.

### MethodInstance

Un contenedor único que describe una única firma llamable para un Método. Vea especialmente [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks) para detalles importantes sobre cómo modificar estos campos de manera segura.

  * `tiposDeEspecificación`

    La clave primaria para esta MethodInstance. La unicidad está garantizada a través de una búsqueda `def.specializations`.
  * `def`

    El `Método` que esta función describe es una especialización de. O un `Módulo`, si se trata de un Lambda de nivel superior expandido en un Módulo, y que no forma parte de un Método.
  * `sparam_vals`

    Los valores de los parámetros estáticos en `specTypes`. Para el `MethodInstance` en `Method.unspecialized`, este es el `SimpleVector` vacío. Pero para un `MethodInstance` en tiempo de ejecución de la caché de `MethodTable`, esto siempre estará definido y será indexable.
  * `no inferido`

    El código fuente descomprimido para un thunk de nivel superior. Además, para una función generada, este es uno de los muchos lugares donde se puede encontrar el código fuente.
  * `aristas de retroceso`

    Almacenamos la lista inversa de dependencias de caché para un seguimiento eficiente del trabajo de reanálisis/recompilación incremental que puede ser necesario después de nuevas definiciones de métodos. Esto funciona manteniendo una lista de los otros `MethodInstance` que se han inferido u optimizado para contener una posible llamada a este `MethodInstance`. Esos resultados de optimización pueden estar almacenados en algún lugar de la `cache`, o pueden haber sido el resultado de algo que no queríamos almacenar en caché, como la propagación de constantes. Por lo tanto, fusionamos todos esos backedges a varias entradas de caché aquí (casi siempre hay solo la única entrada de caché aplicable con un valor centinela para max_world de todos modos).
  * `caché`

    Caché de objetos `CodeInstance` que comparten esta instancia de plantilla.

### CodeInstance

  * `def`

    La `MethodInstance` de la que se deriva esta entrada de caché.
  * `propietario`

    Un token que representa al propietario de esta `CodeInstance`. Se utilizará `jl_egal` para hacer coincidir.

  * `rettype`/`rettype_const`

    El tipo de retorno inferido para el campo `specFunctionObject`, que (en la mayoría de los casos) también es el tipo de retorno computado para la función en general.
  * `inferido`

    Puede contener una caché de la fuente inferida para esta función, o podría estar configurado como `nada` para simplemente indicar que `rettype` es inferido.
  * `ftpr`

    El punto de entrada genérico jlcall.
  * `jlcall_api`

    El ABI a utilizar al llamar a `fptr`. Algunos significativos incluyen:

      * 0 - No compilado aún
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - Constante (valor almacenado en `rettype_const`)
      * 3 - Con parámetros estáticos enviados `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - Ejecutar en el intérprete `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_world` / `max_world`

    El rango de edades del mundo para el cual esta instancia de método es válida para ser llamada. Si max_world es el valor de token especial `-1`, el valor aún no se conoce. Puede seguir utilizándose hasta que encontremos un retroceso que requiera que reconsideremos.

### CodeInfo

Un contenedor (generalmente temporal) para contener código fuente reducido.

  * `código`

    Un array `Any` de declaraciones
  * `nombresdeslot`

    Un array de símbolos que da nombres a cada espacio (argumento o variable local).
  * `slotflags`

    Un array `UInt8` de propiedades de ranura, representado como banderas de bits:

      * 0x02 - asignado (solo falso si *no* hay declaraciones de asignación con esta variable a la izquierda)
      * 0x08 - utilizado (si hay alguna lectura o escritura del slot)
      * 0x10 - asignado estáticamente una vez
      * 0x20 - podría usarse antes de ser asignado. Esta bandera solo es válida después de la inferencia de tipos.
  * `ssavaluetypes`

    Ya sea un array o un `Int`.

    Si es un `Int`, da el número de ubicaciones temporales insertadas por el compilador en la función (la longitud del array `code`). Si es un array, especifica un tipo para cada ubicación.
  * `ssaflags`

    Banderas de 32 bits a nivel de declaración para cada expresión en la función. Consulte la definición de `jl_code_info_t` en julia.h para más detalles.
  * `linetable`

    Un array de objetos de ubicación de origen
  * `codelocs`

    Un array de índices enteros en la `linetable`, que da la ubicación asociada con cada declaración.

Campos opcionales:

  * `tiposdeslot`

    Un array de tipos para los slots.
  * `rettype`

    El tipo de retorno inferido de la forma reducida (IR). El valor predeterminado es `Any`.
  * `método_para_heurísticas_de_límite_de_inferencia`

    El `method_for_inference_heuristics` expandirá el generador del método dado si es necesario durante la inferencia.
  * `padre`

    El `MethodInstance` que "posee" este objeto (si aplica).
  * `bordes`

    Reenvía los bordes a las instancias de método que deben ser invalidadas.
  * `min_world`/`max_world`

    El rango de edades del mundo para el cual este código era válido en el momento en que se había inferido.

Propiedades booleanas:

  * `inferido`

    Si esto ha sido producido por inferencia de tipos.
  * `inlineable`

    Si esto debería ser elegible para la inclusión.
  * `propagar_entrantes`

    Si esto debería propagar `@inbounds` cuando se inyecta con el propósito de elidir bloques `@boundscheck`.

`UInt8` configuraciones:

  * `constprop`

      * 0 = usar heurística
      * 1 = agresivo
      * 2 = ninguno
  * `pureza` Construido a partir de 5 banderas de bits:

      * 0x01 << 0 = este método está garantizado para devolver o terminar de manera consistente (`:consistent`)
      * 0x01 << 1 = este método está libre de efectos secundarios semánticamente visibles externamente (`:effect_free`)
      * 0x01 << 2 = este método está garantizado para no lanzar una excepción (`:nothrow`)
      * 0x01 << 3 = este método está garantizado para terminar (`:terminates_globally`)
      * 0x01 << 4 = el flujo de control sintáctico dentro de este método está garantizado para terminar (`:terminates_locally`)

    Consulta la documentación de `Base.@assume_effects` para más detalles.

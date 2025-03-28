# Noteworthy Differences from other Languages

## Noteworthy differences from MATLAB

Aunque los usuarios de MATLAB pueden encontrar la sintaxis de Julia familiar, Julia no es un clon de MATLAB. Existen diferencias sintácticas y funcionales importantes. Las siguientes son algunas diferencias notables que pueden confundir a los usuarios de Julia acostumbrados a MATLAB:

  * Los arreglos de Julia se indexan con corchetes cuadrados, `A[i,j]`.
  * Los arreglos de Julia no se copian cuando se asignan a otra variable. Después de `A = B`, cambiar los elementos de `B` también modificará `A`. Para evitar esto, usa `A = copy(B)`.
  * Los valores de Julia no se copian cuando se pasan a una función. Si una función modifica un arreglo, los cambios serán visibles en el llamador.
  * Julia no crece automáticamente los arreglos en una declaración de asignación. Mientras que en MATLAB `a(4) = 3.2` puede crear el arreglo `a = [0 0 0 3.2]` y `a(5) = 7` puede hacerlo crecer a `a = [0 0 0 3.2 7]`, la declaración correspondiente en Julia `a[5] = 7` genera un error si la longitud de `a` es menor que 5 o si esta declaración es el primer uso del identificador `a`. Julia tiene [`push!`](@ref) y [`append!`](@ref), que crecen `Vector`s de manera mucho más eficiente que el `a(end+1) = val` de MATLAB.
  * La unidad imaginaria `sqrt(-1)` se representa en Julia como [`im`](@ref), no como `i` o `j` como en MATLAB.
  * En Julia, los números literales sin un punto decimal (como `42`) crean enteros en lugar de números de punto flotante. Como resultado, algunas operaciones pueden lanzar un error de dominio si esperan un flotante; por ejemplo, `julia> a = -1; 2^a` lanza un error de dominio, ya que el resultado no es un entero (consulta [the FAQ entry on domain errors](@ref faq-domain-errors) para más detalles).
  * En Julia, se devuelven múltiples valores y se asignan como tuplas, por ejemplo, `(a, b) = (1, 2)` o `a, b = 1, 2`. `nargout` de MATLAB, que a menudo se utiliza en MATLAB para realizar trabajos opcionales según el número de valores devueltos, no existe en Julia. En su lugar, los usuarios pueden utilizar argumentos opcionales y de palabra clave para lograr capacidades similares.
  * Julia tiene arreglos verdaderamente unidimensionales. Los vectores columna son de tamaño `N`, no `Nx1`. Por ejemplo, [`rand(N)`](@ref) crea un arreglo unidimensional.
  * En Julia, `[x,y,z]` siempre construirá un arreglo de 3 elementos que contiene `x`, `y` y `z`.

      * Para concatenar en la primera dimensión ("vertical") utiliza ya sea [`vcat(x,y,z)`](@ref) o sepáralo con punto y coma (`[x; y; z]`).
      * Para concatenar en la segunda dimensión ("horizontal") usa ya sea [`hcat(x,y,z)`](@ref) o separa con espacios (`[x y z]`).
      * Para construir matrices en bloque (concatenando en las dos primeras dimensiones), utiliza [`hvcat`](@ref) o combina espacios y puntos y comas (`[a b; c d]`).
  * En Julia, `a:b` y `a:b:c` construyen objetos `AbstractRange`. Para construir un vector completo como en MATLAB, usa [`collect(a:b)`](@ref). Generalmente, no es necesario llamar a `collect`. Un objeto `AbstractRange` actuará como un arreglo normal en la mayoría de los casos, pero es más eficiente porque calcula sus valores de manera perezosa. Este patrón de crear objetos especializados en lugar de arreglos completos se utiliza con frecuencia, y también se ve en funciones como [`range`](@ref), o con iteradores como `enumerate` y `zip`. Los objetos especiales se pueden usar en su mayoría como si fueran arreglos normales.
  * Las funciones en Julia devuelven valores de su última expresión o de la palabra clave `return` en lugar de listar los nombres de las variables a devolver en la definición de la función (ver [The return Keyword](@ref) para más detalles).
  * Un script de Julia puede contener cualquier número de funciones, y todas las definiciones serán visibles externamente cuando se cargue el archivo. Las definiciones de funciones se pueden cargar desde archivos fuera del directorio de trabajo actual.
  * En Julia, las reducciones como [`sum`](@ref), [`prod`](@ref), y [`maximum`](@ref) se realizan sobre cada elemento de un arreglo cuando se llaman con un solo argumento, como en `sum(A)`, incluso si `A` tiene más de una dimensión.
  * En Julia, se deben usar paréntesis para llamar a una función sin argumentos, como en [`rand()`](@ref).
  * Julia desaconseja el uso de punto y coma para finalizar declaraciones. Los resultados de las declaraciones no se imprimen automáticamente (excepto en el aviso interactivo), y las líneas de código no necesitan terminar con punto y coma. [`println`](@ref) o [`@printf`](@ref) se pueden usar para imprimir una salida específica.
  * En Julia, si `A` y `B` son arreglos, las operaciones de comparación lógica como `A == B` no devuelven un arreglo de booleanos. En su lugar, usa `A .== B`, y de manera similar para los otros operadores booleanos como [`<`](@ref), [`>`](@ref).
  * En Julia, los operadores [`&`](@ref), [`|`](@ref), y [`⊻`](@ref xor) ([`xor`](@ref)) realizan las operaciones a nivel de bits equivalentes a `and`, `or`, y `xor` respectivamente en MATLAB, y tienen una precedencia similar a los operadores a nivel de bits de Python (a diferencia de C). Pueden operar sobre escalares o de manera elemento a elemento en arreglos y pueden ser utilizados para combinar arreglos lógicos, pero ten en cuenta la diferencia en el orden de las operaciones: pueden ser necesarios paréntesis (por ejemplo, para seleccionar elementos de `A` iguales a 1 o 2 usa `(A .== 1) .| (A .== 2)`).
  * En Julia, los elementos de una colección se pueden pasar como argumentos a una función utilizando el operador splat `...`, como en `xs=[1,2]; f(xs...)`.
  * El [`svd`](@ref) de Julia devuelve los valores singulares como un vector en lugar de como una matriz diagonal densa.
  * En Julia, `...` no se utiliza para continuar líneas de código. En su lugar, las expresiones incompletas se continúan automáticamente en la siguiente línea.
  * En Julia y MATLAB, la variable `ans` se establece en el valor de la última expresión emitida en una sesión interactiva. En Julia, a diferencia de MATLAB, `ans` no se establece cuando el código de Julia se ejecuta en modo no interactivo.
  * Los `struct`s de Julia no admiten la adición dinámica de campos en tiempo de ejecución, a diferencia de las `class`es de MATLAB. En su lugar, utiliza un [`Dict`](@ref). El Dict en Julia no es ordenado.
  * En Julia, cada módulo tiene su propio ámbito/espacio de nombres global, mientras que en MATLAB solo hay un ámbito global.
  * En MATLAB, una forma idiomática de eliminar valores no deseados es usar indexación lógica, como en la expresión `x(x>3)` o en la declaración `x(x>3) = []` para modificar `x` en su lugar. En contraste, Julia proporciona las funciones de orden superior [`filter`](@ref) y [`filter!`](@ref), lo que permite a los usuarios escribir `filter(z->z>3, x)` y `filter!(z->z>3, x)` como alternativas a las transliteraciones correspondientes `x[x.>3]` y `x = x[x.>3]`. Usar `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` reduce el uso de arreglos temporales.
  * El análogo de extraer (o "desreferenciar") todos los elementos de un arreglo de celdas, por ejemplo, en `vertcat(A{:})` en MATLAB, se escribe utilizando el operador splat en Julia, por ejemplo, como `vcat(A...)`.
  * En Julia, la función `adjoint` realiza la transposición conjugada; en MATLAB, `adjoint` proporciona el "adjunto" o adjunto clásico, que es la transposición de la matriz de cofactores.
  * En Julia, a^b^c se evalúa como a^(b^c) mientras que en MATLAB es (a^b)^c.

## Noteworthy differences from R

Uno de los objetivos de Julia es proporcionar un lenguaje efectivo para el análisis de datos y la programación estadística. Para los usuarios que vienen a Julia desde R, estas son algunas diferencias notables:

  * Las comillas simples de Julia encierran caracteres, no cadenas.
  * Julia puede crear subcadenas indexando en cadenas. En R, las cadenas deben convertirse en vectores de caracteres antes de crear subcadenas.
  * En Julia, al igual que en Python pero a diferencia de R, las cadenas se pueden crear con comillas triples `""" ... """`. Esta sintaxis es conveniente para construir cadenas que contienen saltos de línea.
  * En Julia, los varargs se especifican utilizando el operador splat `...`, que siempre sigue el nombre de una variable específica, a diferencia de R, donde `...` puede aparecer de forma aislada.
  * En Julia, el módulo es `mod(a, b)`, no `a %% b`. `%` en Julia es el operador de resto.
  * Julia construye vectores usando corchetes. El `[1, 2, 3]` de Julia es equivalente al `c(1, 2, 3)` de R.
  * En Julia, no todas las estructuras de datos admiten la indexación lógica. Además, la indexación lógica en Julia solo se admite con vectores de longitud igual al objeto que se está indexando. Por ejemplo:

      * En R, `c(1, 2, 3, 4)[c(TRUE, FALSE)]` es equivalente a `c(1, 3)`.
      * En R, `c(1, 2, 3, 4)[c(TRUE, FALSE, TRUE, FALSE)]` es equivalente a `c(1, 3)`.
      * En Julia, `[1, 2, 3, 4][[true, false]]` lanza un [`BoundsError`](@ref).
      * En Julia, `[1, 2, 3, 4][[true, false, true, false]]` produce `[1, 3]`.
  * Como muchos lenguajes, Julia no siempre permite operaciones en vectores de diferentes longitudes, a diferencia de R, donde los vectores solo necesitan compartir un rango de índices común. Por ejemplo, `c(1, 2, 3, 4) + c(1, 2)` es válido en R, pero el equivalente `[1, 2, 3, 4] + [1, 2]` generará un error en Julia.
  * Julia permite una coma final opcional cuando esa coma no cambia el significado del código. Esto puede causar confusión entre los usuarios de R al indexar en arreglos. Por ejemplo, `x[1,]` en R devolvería la primera fila de una matriz; sin embargo, en Julia, la coma se ignora, por lo que `x[1,] == x[1]`, y devolverá el primer elemento. Para extraer una fila, asegúrate de usar `:`, como en `x[1,:]`.
  * El [`map`](@ref) de Julia toma la función primero, luego sus argumentos, a diferencia de `lapply(<estructura>, función, ...)` en R. De manera similar, el equivalente de Julia de `apply(X, MARGIN, FUN, ...)` en R es [`mapslices`](@ref) donde la función es el primer argumento.
  * La aplicación multivariante en R, por ejemplo, `mapply(choose, 11:13, 1:3)`, se puede escribir como `broadcast(binomial, 11:13, 1:3)` en Julia. De manera equivalente, Julia ofrece una sintaxis de punto más corta para vectorizar funciones `binomial.(11:13, 1:3)`.
  * Julia utiliza `end` para denotar el final de bloques condicionales, como `if`, bloques de bucle, como `while`/ `for`, y funciones. En lugar de la sintaxis de una línea `if ( cond ) statement`, Julia permite declaraciones de la forma `if cond; statement; end`, `cond && statement` y `!cond || statement`. Las declaraciones de asignación en las dos últimas sintaxis deben estar explícitamente envueltas en paréntesis, por ejemplo, `cond && (x = value)`.
  * En Julia, `<-`, `<<-` y `->` no son operadores de asignación.
  * La `->` de Julia crea una función anónima.
  * El operador [`*`](@ref) de Julia puede realizar multiplicación de matrices, a diferencia de R. Si `A` y `B` son matrices, entonces `A * B` denota una multiplicación de matrices en Julia, equivalente a `A %*% B` en R. En R, esta misma notación realizaría un producto elemento a elemento (Hadamard). Para obtener la operación de multiplicación elemento a elemento, necesitas escribir `A .* B` en Julia.
  * Julia realiza la transposición de matrices utilizando la función `transpose` y la transposición conjugada utilizando el operador `'` o la función `adjoint`. Por lo tanto, `transpose(A)` de Julia es equivalente a `t(A)` de R. Además, una transposición no recursiva en Julia se proporciona mediante la función `permutedims`.
  * Julia no requiere paréntesis al escribir declaraciones `if` o bucles `for`/`while`: usa `for i in [1, 2, 3]` en lugar de `for (i in c(1, 2, 3))` y `if i == 1` en lugar de `if (i == 1)`.
  * Julia no trata los números `0` y `1` como booleanos. No puedes escribir `if (1)` en Julia, porque las declaraciones `if` aceptan solo booleanos. En su lugar, puedes escribir `if true`, `if Bool(1)` o `if 1==1`.
  * Julia no proporciona `nrow` y `ncol`. En su lugar, utiliza `size(M, 1)` para `nrow(M)` y `size(M, 2)` para `ncol(M)`.
  * Julia es cuidadosa al distinguir escalares, vectores y matrices. En R, `1` y `c(1)` son lo mismo. En Julia, no se pueden usar de manera intercambiable.
  * Los [`diag`](@ref) y [`diagm`](@ref) de Julia no son como los de R.
  * Julia no puede asignar a los resultados de las llamadas a funciones en el lado izquierdo de una operación de asignación: no puedes escribir `diag(M) = fill(1, n)`.
  * Julia desaconseja poblar el espacio de nombres principal con funciones. La mayor parte de la funcionalidad estadística para Julia se encuentra en [packages](https://pkg.julialang.org/) bajo [JuliaStats organization](https://github.com/JuliaStats). Por ejemplo:

      * Las funciones relacionadas con las distribuciones de probabilidad son proporcionadas por el [Distributions package](https://github.com/JuliaStats/Distributions.jl).
      * El [DataFrames package](https://github.com/JuliaData/DataFrames.jl) proporciona marcos de datos.
      * Los modelos lineales generalizados son proporcionados por el [GLM package](https://github.com/JuliaStats/GLM.jl).
  * Julia proporciona tuplas y tablas hash reales, pero no listas al estilo R. Al devolver múltiples elementos, deberías utilizar típicamente una tupla o una tupla nombrada: en lugar de `list(a = 1, b = 2)`, utiliza `(1, 2)` o `(a=1, b=2)`.
  * Julia anima a los usuarios a escribir sus propios tipos, que son más fáciles de usar que los objetos S3 o S4 en R. El sistema de despacho múltiple de Julia significa que `table(x::TypeA)` y `table(x::TypeB)` actúan como `table.TypeA(x)` y `table.TypeB(x)` en R.
  * En Julia, los valores no se copian cuando se asignan o se pasan a una función. Si una función modifica un arreglo, los cambios serán visibles en el llamador. Esto es muy diferente de R y permite que nuevas funciones operen en estructuras de datos grandes de manera mucho más eficiente.
  * En Julia, los vectores y matrices se concatenan usando [`hcat`](@ref), [`vcat`](@ref) y [`hvcat`](@ref), no `c`, `rbind` y `cbind` como en R.
  * En Julia, un rango como `a:b` no es una abreviatura para un vector como en R, sino un objeto especializado `AbstractRange` que se utiliza para la iteración. Para convertir un rango en un vector, usa [`collect(a:b)`](@ref).
  * El operador `:` tiene una precedencia diferente en R y Julia. En particular, en Julia los operadores aritméticos tienen una precedencia más alta que el operador `:`, mientras que lo contrario es cierto en R. Por ejemplo, `1:n-1` en Julia es equivalente a `1:(n-1)` en R.
  * El [`max`](@ref) y el [`min`](@ref) de Julia son equivalentes a `pmax` y `pmin` respectivamente en R, pero ambos argumentos deben tener las mismas dimensiones. Mientras que [`maximum`](@ref) y [`minimum`](@ref) reemplazan `max` y `min` en R, hay diferencias importantes.
  * Los [`sum`](@ref), [`prod`](@ref), [`maximum`](@ref), y [`minimum`](@ref) son diferentes de sus contrapartes en R. Todos aceptan un argumento de palabra clave opcional `dims`, que indica las dimensiones sobre las cuales se lleva a cabo la operación. Por ejemplo, sea `A = [1 2; 3 4]` en Julia y `B <- rbind(c(1,2),c(3,4))` sea la misma matriz en R. Entonces `sum(A)` da el mismo resultado que `sum(B)`, pero `sum(A, dims=1)` es un vector fila que contiene la suma sobre cada columna y `sum(A, dims=2)` es un vector columna que contiene la suma sobre cada fila. Esto contrasta con el comportamiento de R, donde funciones separadas `colSums(B)` y `rowSums(B)` proporcionan estas funcionalidades. Si el argumento de palabra clave `dims` es un vector, entonces especifica todas las dimensiones sobre las cuales se realiza la suma, mientras se mantienen las dimensiones del array sumado, por ejemplo, `sum(A, dims=(1,2)) == hcat(10)`. Cabe señalar que no hay verificación de errores respecto al segundo argumento.
  * Julia tiene varias funciones que pueden mutar sus argumentos. Por ejemplo, tiene tanto [`sort`](@ref) como [`sort!`](@ref).
  * En R, el rendimiento requiere vectorización. En Julia, casi lo opuesto es cierto: el código de mejor rendimiento a menudo se logra utilizando bucles devectorizados.
  * Julia se evalúa de manera ansiosa y no admite la evaluación perezosa al estilo R. Para la mayoría de los usuarios, esto significa que hay muy pocas expresiones o nombres de columnas sin comillas.
  * Julia no soporta el tipo `NULL`. El equivalente más cercano es [`nothing`](@ref), pero se comporta como un valor escalar en lugar de como una lista. Usa `x === nothing` en lugar de `is.null(x)`.
  * En Julia, los valores faltantes se representan mediante el objeto [`missing`](@ref) en lugar de `NA`. Utiliza [`ismissing(x)`](@ref) (o `ismissing.(x)` para operaciones elemento a elemento en vectores) en lugar de `is.na(x)`. La función [`skipmissing`](@ref) se utiliza generalmente en lugar de `na.rm=TRUE` (aunque en algunos casos particulares las funciones aceptan un argumento `skipmissing`).
  * Julia carece del equivalente de `assign` o `get` de R.
  * En Julia, `return` no requiere paréntesis.
  * En R, una forma idiomática de eliminar valores no deseados es usar indexación lógica, como en la expresión `x[x>3]` o en la declaración `x = x[x>3]` para modificar `x` en su lugar. En contraste, Julia proporciona las funciones de orden superior [`filter`](@ref) y [`filter!`](@ref), lo que permite a los usuarios escribir `filter(z->z>3, x)` y `filter!(z->z>3, x)` como alternativas a las transliteraciones correspondientes `x[x.>3]` y `x = x[x.>3]`. Usar `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` reduce el uso de arreglos temporales.

## Noteworthy differences from Python

  * Los bloques `for`, `if`, `while`, etc. de Julia se terminan con la palabra clave `end`. El nivel de indentación no es significativo como lo es en Python. A diferencia de Python, Julia no tiene la palabra clave `pass`.
  * Las cadenas se denotan con comillas dobles (`"texto"`) en Julia (con tres comillas dobles para cadenas de varias líneas), mientras que en Python se pueden denotar ya sea con comillas simples (`'texto'`) o comillas dobles (`"texto"`). Las comillas simples se utilizan para caracteres en Julia (`'c'`).
  * La concatenación de cadenas se realiza con `*` en Julia, no con `+` como en Python. De manera análoga, la repetición de cadenas se realiza con `^`, no con `*`. La concatenación implícita de literales de cadena como en Python (por ejemplo, `'ab' 'cd' == 'abcd'`) no se realiza en Julia.
  * Listas de Python—flexibles pero lentas—corresponden al tipo `Vector{Any}` de Julia o más generalmente `Vector{T}` donde `T` es algún tipo de elemento no concreto. Los arreglos "rápidos" como los arreglos de NumPy que almacenan elementos en su lugar (es decir, `dtype` es `np.float64`, `[('f1', np.uint64), ('f2', np.int32)]`, etc.) pueden ser representados por `Array{T}` donde `T` es un tipo de elemento concreto e inmutable. Esto incluye tipos incorporados como `Float64`, `Int32`, `Int64`, pero también tipos más complejos como `Tuple{UInt64,Float64}` y muchos tipos definidos por el usuario también.
  * En Julia, la indexación de arreglos, cadenas, etc. es basada en 1 y no en 0.
  * El indexado de segmentos en Julia incluye el último elemento, a diferencia de Python. `a[2:3]` en Julia es `a[1:3]` en Python.
  * A diferencia de Python, Julia permite [AbstractArrays with arbitrary indexes](https://julialang.org/blog/2017/04/offset-arrays/). La interpretación especial de Python sobre la indexación negativa, `a[-1]` y `a[-2]`, debe escribirse como `a[end]` y `a[end-1]` en Julia.
  * Julia requiere `end` para indexar hasta el último elemento. `x[1:]` en Python es equivalente a `x[2:end]` en Julia.
  * En Julia, `:` antes de cualquier objeto crea un [`Symbol`](@ref) o *cita* una expresión; así, `x[:5]` es lo mismo que `x[5]`. Si deseas obtener los primeros `n` elementos de un arreglo, entonces usa la indexación de rango.
  * El indexado de rango en Julia tiene el formato `x[start:step:stop]`, mientras que el formato de Python es `x[start:(stop+1):step]`. Por lo tanto, `x[0:10:2]` en Python es equivalente a `x[1:2:10]` en Julia. De manera similar, `x[::-1]` en Python, que se refiere al arreglo invertido, es equivalente a `x[end:-1:1]` en Julia.
  * En Julia, los rangos se pueden construir de forma independiente como `inicio:paso:fin`, la misma sintaxis que se utiliza en la indexación de arreglos. También se admite la función `range`.
  * En Julia, indexar una matriz con arreglos como `X[[1,2], [1,3]]` se refiere a una sub-matriz que contiene las intersecciones de las primeras y segundas filas con las primeras y terceras columnas. En Python, `X[[1,2], [1,3]]` se refiere a un vector que contiene los valores de la celda `[1,1]` y `[2,3]` en la matriz. `X[[1,2], [1,3]]` en Julia es equivalente a `X[np.ix_([0,1],[0,2])]` en Python. `X[[0,1], [0,2]]` en Python es equivalente a `X[[CartesianIndex(1,1), CartesianIndex(2,3)]]` en Julia.
  * Julia no tiene una sintaxis de continuación de línea: si, al final de una línea, la entrada hasta ahora es una expresión completa, se considera terminada; de lo contrario, la entrada continúa. Una forma de forzar a que una expresión continúe es envolverla en paréntesis.
  * Los arreglos de Julia son por columnas (ordenados por Fortran), mientras que los arreglos de NumPy son por filas (ordenados por C) de forma predeterminada. Para obtener un rendimiento óptimo al iterar sobre arreglos, el orden de los bucles debe invertirse en Julia en relación con NumPy (ver [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Los operadores de actualización de Julia (por ejemplo, `+=`, `-=`, ...) *no son in situ*, mientras que los de NumPy sí lo son. Esto significa que `A = [1, 1]; B = A; B += [3, 3]` no cambia los valores en `A`, sino que vuelve a enlazar el nombre `B` al resultado del lado derecho `B = B + 3`, que es un nuevo arreglo. Para operaciones in situ, usa `B .+= 3` (ver también [dot operators](@ref man-dot-operators)), bucles explícitos o `InplaceOps.jl`.
  * Julia evalúa los valores predeterminados de los argumentos de función cada vez que se invoca el método, a diferencia de Python, donde los valores predeterminados se evalúan solo una vez cuando se define la función. Por ejemplo, la función `f(x=rand()) = x` devuelve un nuevo número aleatorio cada vez que se invoca sin argumento. Por otro lado, la función `g(x=[1,2]) = push!(x,3)` devuelve `[1,2,3]` cada vez que se llama como `g()`.
  * En Julia, los argumentos de palabra clave deben ser pasados usando palabras clave, a diferencia de Python, en el que generalmente es posible pasarlos de manera posicional. Intentar pasar un argumento de palabra clave de manera posicional altera la firma del método, lo que lleva a un `MethodError` o a la llamada del método incorrecto.
  * En Julia `%` es el operador de resto, mientras que en Python es el módulo.
  * En Julia, el tipo `Int` comúnmente utilizado corresponde al tipo de entero de máquina (`Int32` o `Int64`), a diferencia de Python, donde `int` es un entero de longitud arbitraria. Esto significa que en Julia el tipo `Int` se desbordará, de modo que `2^64 == 0`. Si necesitas valores más grandes, utiliza otro tipo apropiado, como `Int128`, [`BigInt`](@ref) o un tipo de punto flotante como `Float64`.
  * La unidad imaginaria `sqrt(-1)` se representa en Julia como `im`, no `j` como en Python.
  * En Julia, el operador de exponenciación es `^`, no `**` como en Python.
  * Julia usa `nothing` de tipo `Nothing` para representar un valor nulo, mientras que Python usa `None` de tipo `NoneType`.
  * En Julia, los operadores estándar sobre un tipo de matriz son operaciones de matriz, mientras que en Python, los operadores estándar son operaciones elemento por elemento. Cuando tanto `A` como `B` son matrices, `A * B` en Julia realiza multiplicación de matrices, no multiplicación elemento por elemento como en Python. `A * B` en Julia es equivalente a `A @ B` en Python, mientras que `A * B` en Python es equivalente a `A .* B` en Julia.
  * El operador adjunto `'` en Julia devuelve un adjunto de un vector (una representación perezosa de un vector fila), mientras que el operador de transposición `.T` sobre un vector en Python devuelve el vector original (sin operación).
  * En Julia, una función puede contener múltiples implementaciones concretas (llamadas *métodos*), que se seleccionan a través de la dispatch múltiple basada en los tipos de todos los argumentos de la llamada, en comparación con las funciones en Python, que tienen una única implementación y no polimorfismo (a diferencia de las llamadas a métodos en Python que utilizan una sintaxis diferente y permiten la dispatch en el receptor del método).
  * No hay clases en Julia. En su lugar, hay estructuras (mutables o inmutables), que contienen datos pero no métodos.
  * Llamar a un método de una instancia de clase en Python (`x = MyClass(*args); x.f(y)`) corresponde a una llamada de función en Julia, por ejemplo, `x = MyType(args...); f(x, y)`. En general, el despacho múltiple es más flexible y poderoso que el sistema de clases de Python.
  * Las estructuras de Julia pueden tener exactamente un supertipo abstracto, mientras que las clases de Python pueden heredar de una o más superclases (abstractas o concretas).
  * La estructura lógica del programa Julia (Paquetes y Módulos) es independiente de la estructura de archivos, mientras que la estructura del código Python está definida por directorios (Paquetes) y archivos (Módulos).
  * En Julia, es idiomático dividir el texto de grandes módulos en múltiples archivos, sin introducir un nuevo módulo por archivo. El código se reensambla dentro de un solo módulo en un archivo principal a través de `include`. Mientras que el equivalente en Python (`exec`) no es típico para este uso (silenciosamente sobrescribirá definiciones anteriores), los programas de Julia se definen como una unidad a nivel de `module` con `using` o `import`, que solo se ejecutarán una vez cuando se necesiten por primera vez, como `include` en Python. Dentro de esos módulos, los archivos individuales que componen ese módulo se cargan con `include` enumerándolos una vez en el orden deseado.
  * El operador ternario `x > 0 ? 1 : -1` en Julia corresponde a una expresión condicional en Python `1 if x > 0 else -1`.
  * En Julia, el símbolo `@` se refiere a un macro, mientras que en Python se refiere a un decorador.
  * El manejo de excepciones en Julia se realiza utilizando `try` — `catch` — `finally`, en lugar de `try` — `except` — `finally`. A diferencia de Python, no se recomienda utilizar el manejo de excepciones como parte del flujo de trabajo normal en Julia (en comparación con Python, Julia es más rápida en el flujo de control ordinario pero más lenta en la captura de excepciones).
  * En Julia, los bucles son rápidos, no hay necesidad de escribir código "vectorizado" por razones de rendimiento.
  * Ten cuidado con las variables globales no constantes en Julia, especialmente en bucles ajustados. Dado que puedes escribir código cercano al metal en Julia (a diferencia de Python), el efecto de las variables globales puede ser drástico (ver [Performance Tips](@ref man-performance-tips)).
  * En Julia, el redondeo y la truncación son explícitos. El `int(3.7)` de Python debería ser `floor(Int, 3.7)` o `Int(floor(3.7))` y se distingue de `round(Int, 3.7)`. `floor(x)` y `round(x)` por sí solos devuelven un valor entero del mismo tipo que `x` en lugar de siempre devolver `Int`.
  * En Julia, el análisis es explícito. El `float("3.7")` de Python sería `parse(Float64, "3.7")` en Julia.
  * En Python, la mayoría de los valores se pueden usar en contextos lógicos (por ejemplo, `if "a":` significa que se ejecuta el siguiente bloque, y `if "":` significa que no se ejecuta). En Julia, necesitas una conversión explícita a `Bool` (por ejemplo, `if "a"` lanza una excepción). Si deseas probar una cadena no vacía en Julia, escribirías explícitamente `if !isempty("")`. Quizás sorprendentemente, en Python `if "False"` y `bool("False")` ambos evalúan a `True` (porque `"False"` es una cadena no vacía); en Julia, `parse(Bool, "false")` devuelve `false`.
  * En Julia, un nuevo ámbito local se introduce por la mayoría de los bloques de código, incluidos los bucles y `try` — `catch` — `finally`. Ten en cuenta que las comprensiones (lista, generador, etc.) introducen un nuevo ámbito local tanto en Python como en Julia, mientras que los bloques `if` no introducen un nuevo ámbito local en ninguno de los dos lenguajes.

## Noteworthy differences from C/C++

  * Los arreglos de Julia se indexan con corchetes cuadrados y pueden tener más de una dimensión `A[i,j]`. Esta sintaxis no es solo un azúcar sintáctico para una referencia a un puntero o dirección como en C/C++. Ver [the manual entry about array construction](@ref man-multi-dim-arrays).
  * En Julia, la indexación de arreglos, cadenas, etc. es basada en 1 y no en 0.
  * Los arreglos de Julia no se copian cuando se asignan a otra variable. Después de `A = B`, cambiar los elementos de `B` también modificará `A`. Los operadores de actualización como `+=` no operan en su lugar, son equivalentes a `A = A + B`, lo que vuelve a enlazar el lado izquierdo al resultado de la expresión del lado derecho.
  * Los arreglos de Julia son de orden por columnas (ordenados por Fortran), mientras que los arreglos de C/C++ son de orden por filas de forma predeterminada. Para obtener un rendimiento óptimo al iterar sobre arreglos, el orden de los bucles debe invertirse en Julia en relación con C/C++ (ver [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Los valores de Julia no se copian cuando se asignan o se pasan a una función. Si una función modifica un arreglo, los cambios serán visibles en el llamador.
  * En Julia, el espacio en blanco es significativo, a diferencia de C/C++, por lo que se debe tener cuidado al agregar o eliminar espacios en blanco de un programa de Julia.
  * En Julia, los números literales sin un punto decimal (como `42`) crean enteros con signo, de tipo `Int`, pero los literales que son demasiado grandes para caber en el tamaño de palabra de la máquina se promocionan automáticamente a un tipo de mayor tamaño, como `Int64` (si `Int` es `Int32`), `Int128` o el tipo arbitrariamente grande `BigInt`. No hay sufijos literales numéricos, como `L`, `LL`, `U`, `UL`, `ULL` para indicar si son sin signo y/o con signo frente a sin signo. Los literales decimales son siempre con signo, y los literales hexadecimales (que comienzan con `0x` como en C/C++), son sin signo, a menos que codifiquen más de 128 bits, en cuyo caso son de tipo `BigInt`. Los literales hexadecimales también, a diferencia de C/C++/Java y a diferencia de los literales decimales en Julia, tienen un tipo basado en la *longitud* del literal, incluyendo ceros a la izquierda. Por ejemplo, `0x0` y `0x00` tienen tipo [`UInt8`](@ref), `0x000` y `0x0000` tienen tipo [`UInt16`](@ref), luego los literales con 5 a 8 dígitos hexadecimales tienen tipo `UInt32`, de 9 a 16 dígitos hexadecimales tipo `UInt64`, de 17 a 32 dígitos hexadecimales tipo `UInt128`, y más de 32 dígitos hexadecimales tipo `BigInt`. Esto debe tenerse en cuenta al definir máscaras hexadecimales, por ejemplo `~0xf == 0xf0` es muy diferente de `~0x000f == 0xfff0`. Los literales de 64 bits `Float64` y de 32 bits [`Float32`](@ref) se expresan como `1.0` y `1.0f0` respectivamente. Los literales de punto flotante se redondean (y no se promocionan al tipo `BigFloat`) si no pueden ser representados exactamente. Los literales de punto flotante se comportan de manera más cercana a C/C++. Los literales octales (prefijados con `0o`) y binarios (prefijados con `0b`) también se tratan como sin signo (o `BigInt` para más de 128 bits).
  * En Julia, el operador de división [`/`](@ref) devuelve un número de punto flotante cuando ambos operandos son de tipo entero. Para realizar una división entera, utiliza [`div`](@ref) o [`÷`](@ref div).
  * Indexar un `Array` con tipos de punto flotante es generalmente un error en Julia. La expresión equivalente en Julia de la expresión en C `a[i / 2]` es `a[i ÷ 2 + 1]`, donde `i` es de tipo entero.
  * Los literales de cadena pueden estar delimitados con `"` o `"""`, los literales delimitados por `"""` pueden contener caracteres `"` sin necesidad de comillas como `"\""`. Los literales de cadena pueden tener valores de otras variables o expresiones interpoladas en ellos, indicados por `$nombreDeVariable` o `$(expresión)`, que evalúa el nombre de la variable o la expresión en el contexto de la función.
  * `//` indica un número [`Rational`](@ref), y no un comentario de una sola línea (que es `#` en Julia)
  * `#=` indica el inicio de un comentario de varias líneas, y `=#` lo finaliza.
  * Las funciones en Julia devuelven valores de su última expresión o de la palabra clave `return`. Se pueden devolver múltiples valores de las funciones y asignarlos como tuplas, por ejemplo, `(a, b) = myfunction()` o `a, b = myfunction()`, en lugar de tener que pasar punteros a valores como se haría en C/C++ (es decir, `a = myfunction(&b)`).
  * Julia no requiere el uso de punto y coma para finalizar las declaraciones. Los resultados de las expresiones no se imprimen automáticamente (excepto en el aviso interactivo, es decir, el REPL), y las líneas de código no necesitan terminar con punto y coma. [`println`](@ref) o [`@printf`](@ref) se pueden usar para imprimir una salida específica. En el REPL, `;` se puede usar para suprimir la salida. `;` también tiene un significado diferente dentro de `[ ]`, algo a tener en cuenta. `;` se puede usar para separar expresiones en una sola línea, pero no son estrictamente necesarias en muchos casos, y son más una ayuda para la legibilidad.
  * En Julia, el operador [`⊻`](@ref xor) ([`xor`](@ref)) realiza la operación XOR a nivel de bits, es decir, [`^`](@ref) en C/C++. Además, los operadores a nivel de bits no tienen la misma precedencia que en C/C++, por lo que pueden ser necesarios paréntesis.
  * La [`^`](@ref) de Julia es exponenciación (pow), no XOR a nivel de bits como en C/C++ (usa [`⊻`](@ref xor), o [`xor`](@ref), en Julia)
  * Julia tiene dos operadores de desplazamiento a la derecha, `>>` y `>>>`. `>>` realiza un desplazamiento aritmético, `>>>` siempre realiza un desplazamiento lógico, a diferencia de C/C++, donde el significado de `>>` depende del tipo del valor que se está desplazando.
  * El `->` de Julia crea una función anónima, no accede a un miembro a través de un puntero.
  * Julia no requiere paréntesis al escribir declaraciones `if` o bucles `for`/`while`: usa `for i in [1, 2, 3]` en lugar de `for (int i=1; i <= 3; i++)` y `if i == 1` en lugar de `if (i == 1)`.
  * Julia no trata los números `0` y `1` como booleanos. No puedes escribir `if (1)` en Julia, porque las declaraciones `if` aceptan solo booleanos. En su lugar, puedes escribir `if true`, `if Bool(1)`, o `if 1==1`.
  * Julia utiliza `end` para denotar el final de bloques condicionales, como `if`, bloques de bucle, como `while`/ `for`, y funciones. En lugar de la sintaxis de una línea `if ( cond ) statement`, Julia permite declaraciones de la forma `if cond; statement; end`, `cond && statement` y `!cond || statement`. Las declaraciones de asignación en las dos últimas sintaxis deben estar explícitamente envueltas en paréntesis, por ejemplo, `cond && (x = value)`, debido a la precedencia de los operadores.
  * Julia no tiene una sintaxis de continuación de línea: si, al final de una línea, la entrada hasta ahora es una expresión completa, se considera terminada; de lo contrario, la entrada continúa. Una forma de forzar a que una expresión continúe es envolverla en paréntesis.
  * Los macros de Julia operan sobre expresiones analizadas, en lugar del texto del programa, lo que les permite realizar transformaciones sofisticadas del código de Julia. Los nombres de los macros comienzan con el carácter `@` y tienen tanto una sintaxis similar a funciones, `@mymacro(arg1, arg2, arg3)`, como una sintaxis similar a declaraciones, `@mymacro arg1 arg2 arg3`. Las formas son intercambiables; la forma similar a funciones es particularmente útil si el macro aparece dentro de otra expresión, y a menudo es más clara. La forma similar a declaraciones se utiliza a menudo para anotar bloques, como en el constructo `for` distribuido: `@distributed for i in 1:n; #= body =#; end`. Donde el final de la construcción del macro puede no estar claro, utiliza la forma similar a funciones.
  * Julia tiene un tipo de enumeración, expresado utilizando el macro `@enum(nombre, valor1, valor2, ...)` Por ejemplo: `@enum(Fruit, banana=1, apple, pear)`
  * Por convención, las funciones que modifican sus argumentos tienen un `!` al final del nombre, por ejemplo `push!`.
  * En C++, por defecto, tienes despacho estático, es decir, necesitas anotar una función como virtual para tener despacho dinámico. Por otro lado, en Julia, cada método es "virtual" (aunque es más general que eso, ya que los métodos se despachan en cada tipo de argumento, no solo en `this`, utilizando la regla de la declaración más específica).

### Julia ⇔ C/C++: Namespaces

  * Los `namespace`s de C/C++ corresponden aproximadamente a los `module`s de Julia.
  * No hay globals o campos privados en Julia. Todo es accesible públicamente a través de rutas completamente calificadas (o rutas relativas, si se desea).
  * `using MyNamespace::myfun` (C++) corresponde aproximadamente a `import MyModule: myfun` (Julia).
  * `using namespace MyNamespace` (C++) corresponde aproximadamente a `using MyModule` (Julia)

      * En Julia, solo los símbolos `export`ados están disponibles para el módulo que llama.
      * En C++, solo los elementos que se encuentran en los archivos de encabezado (públicos) incluidos están disponibles.
  * Advertencia: las palabras clave `import`/`using` (Julia) también *cargan* módulos (ver más abajo).
  * Advertencia: `import`/`using` (Julia) solo funciona a nivel de ámbito global (`módulos`)

      * En C++, `using namespace X` funciona dentro de ámbitos arbitrarios (por ejemplo: ámbito de función).

### Julia ⇔ C/C++: Module loading

  * Cuando piensas en una "**biblioteca**" de C/C++, es probable que estés buscando un "**paquete**" de Julia.

      * Advertencia: Las bibliotecas de C/C++ a menudo albergan múltiples "módulos de software", mientras que los "paquetes" de Julia suelen albergar uno.
      * Recordatorio: los `módulos` de Julia son ámbitos globales (no necesariamente "módulos de software").
  * **En lugar de scripts de construcción/`make`**, Julia utiliza "Entornos de Proyecto" (a veces llamados "Proyecto" o "Entorno").

      * Los scripts de construcción solo son necesarios para aplicaciones más complejas (como aquellas que necesitan compilar o descargar ejecutables de C/C++).
      * Para desarrollar una aplicación o proyecto en Julia, puedes inicializar su directorio raíz como un "Entorno de Proyecto" y albergar allí el código/paquetes específicos de la aplicación. Esto proporciona un buen control sobre las dependencias del proyecto y la reproducibilidad futura.
      * Los paquetes disponibles se añaden a un "Entorno del Proyecto" con la función `Pkg.add()` o en modo REPL de Pkg. (Sin embargo, esto no **carga** dicho paquete).
      * La lista de paquetes disponibles (dependencias directas) para un "Entorno de Proyecto" se guarda en su archivo `Project.toml`.
      * La *información* completa de dependencias para un "Entorno de Proyecto" se genera automáticamente y se guarda en su archivo `Manifest.toml` mediante `Pkg.resolve()`.
  * Los paquetes ("módulos de software") disponibles en el "Entorno del Proyecto" se cargan con `import` o `using`.

      * En C/C++, utilizas `#include <moduleheader>` para obtener declaraciones de objetos/funciones, y enlazas en bibliotecas cuando construyes el ejecutable.
      * En Julia, llamar a using/import nuevamente solo trae el módulo existente al alcance, pero no lo carga de nuevo (similar a agregar el no estándar `#pragma once` en C/C++).
  * **Repositorios de paquetes basados en directorios** (Julia) se pueden hacer disponibles agregando rutas de repositorio al arreglo `Base.LOAD_PATH`.

      * Los paquetes de repositorios basados en directorios no requieren la herramienta `Pkg.add()` antes de ser cargados con `import` o `using`. Simplemente están disponibles para el proyecto.
      * Los repositorios de paquetes basados en directorios son la **solución más rápida** para desarrollar bibliotecas locales de "módulos de software".

### Julia ⇔ C/C++: Assembling modules

  * En C/C++, los archivos `.c`/`.cpp` se compilan y se añaden a una biblioteca con scripts de construcción/`make`.

      * En Julia, las declaraciones `import [PkgName]`/`using [PkgName]` cargan `[PkgName].jl` ubicado en el subdirectorio `[PkgName]/src/` de un paquete.
      * A su vez, `[PkgName].jl` típicamente carga archivos fuente asociados con llamadas a `include "[someotherfile].jl"`.
  * `include "./path/to/somefile.jl"` (Julia) es muy similar a `#include "./path/to/somefile.jl"` (C/C++).

      * Sin embargo, `include "..."` (Julia) no se utiliza para incluir archivos de encabezado (no es necesario).
      * **No utilices** `include "..."` (Julia) para cargar código de otros "módulos de software" (utiliza `import`/`using` en su lugar).
      * `include "path/to/some/module.jl"` (Julia) instanciaría múltiples versiones del mismo código en diferentes módulos (creando tipos *distintos* (etc.) con los *mismos* nombres).
      * `include "somefile.jl"` se utiliza típicamente para ensamblar múltiples archivos *dentro del mismo paquete de Julia* ("módulo de software"). Por lo tanto, es relativamente sencillo asegurarse de que los archivos se `include`n solo una vez (sin confusión de `#ifdef`).

### Julia ⇔ C/C++: Module interface

  * C++ expone interfaces utilizando archivos ".h"/".hpp" "públicos", mientras que los `módulos` de Julia marcan símbolos específicos que están destinados a sus usuarios como `públicos` o `exportados`.

      * A menudo, los `módulos` de Julia simplemente añaden funcionalidad generando nuevos "métodos" a funciones existentes (por ejemplo: `Base.push!`).
      * Los desarrolladores de paquetes de Julia, por lo tanto, no pueden confiar en los archivos de encabezado para la documentación de la interfaz.
      * Las interfaces para los paquetes de Julia se describen típicamente utilizando cadenas de documentación, README.md, páginas web estáticas, ...
  * Algunos desarrolladores eligen no `exportar` todos los símbolos necesarios para usar su paquete/módulo, pero aún así deberían marcar los símbolos no exportados que son visibles para el usuario como `públicos`.

      * Los usuarios podrían esperar acceder a estos componentes calificando funciones/estructuras/... con el nombre del paquete/módulo (por ejemplo: `MyModule.run_this_task(...)`).

### Julia ⇔ C/C++: Quick reference

| Software Concept               | Julia                                                                          | C/C++                                                     |
|:------------------------------ |:------------------------------------------------------------------------------ |:--------------------------------------------------------- |
| unnamed scope                  | `begin` ... `end`                                                              | `{` ... `}`                                               |
| function scope                 | `function x()` ... `end`                                                       | `int x() {` ... `}`                                       |
| global scope                   | `module MyMod` ... `end`                                                       | `namespace MyNS {` ... `}`                                |
| software module                | A Julia "package"                                                              | `.h`/`.hpp` files<br>+compiled `somelib.a`                |
| assembling<br>software modules | `SomePkg.jl`: ...<br>`import("subfile1.jl")`<br>`import("subfile2.jl")`<br>... | `$(AR) *.o` &rArr; `somelib.a`                            |
| import<br>software module      | `import SomePkg`                                                               | `#include <somelib>`<br>+link in `somelib.a`              |
| module library                 | `LOAD_PATH[]`, *Git repository,<br>**custom package registry                   | more `.h`/`.hpp` files<br>+bigger compiled `somebiglib.a` |

* The Julia package manager supports registering multiple packages from a single Git repository.<br> * This allows users to house a library of related packages in a single repository.<br> ** Julia registries are primarily designed to provide versioning \& distribution of packages.<br> ** Custom package registries can be used to create a type of module library.

## Noteworthy differences from Common Lisp

  * Julia utiliza la indexación basada en 1 para arreglos por defecto, y también puede manejar [index offsets](@ref man-custom-indices) arbitrariamente.
  * Las funciones y las variables comparten el mismo espacio de nombres (“Lisp-1”).
  * Hay un tipo [`Pair`](@ref), pero no está destinado a ser utilizado como un `COMMON-LISP:CONS`. Se pueden usar varias colecciones iterables de manera intercambiable en la mayoría de las partes del lenguaje (por ejemplo, splatting, tuplas, etc.). Las `Tuple`s son las más cercanas a las listas de Common Lisp para colecciones *cortas* de elementos heterogéneos. Usa `NamedTuple`s en lugar de alists. Para colecciones más grandes de tipos homogéneos, se deben usar `Array`s y `Dict`s.
  * El flujo de trabajo típico de Julia para la creación de prototipos también utiliza la manipulación continua de la imagen, implementada con el paquete [Revise.jl](https://github.com/timholy/Revise.jl).
  * Para el rendimiento, Julia prefiere que las operaciones tengan [type stability](@ref man-type-stability). Mientras que Common Lisp abstrae las operaciones de la máquina subyacente, Julia se mantiene más cerca de ellas. Por ejemplo:

      * La división entera usando `/` siempre devuelve un resultado de punto flotante, incluso si el cálculo es exacto.

          * `//` siempre devuelve un resultado racional
          * `÷` siempre devuelve un resultado entero (truncado)
      * Los bignums son compatibles, pero la conversión no es automática; enteros ordinarios [overflow](@ref faq-integer-arithmetic).
      * Los números complejos son compatibles, pero para obtener resultados complejos, [you need complex inputs](@ref faq-domain-errors).
      * Hay múltiples tipos Complejos y Racionales, con diferentes tipos de componentes.
  * Los módulos (espacios de nombres) pueden ser jerárquicos. [`import`](@ref) y [`using`](@ref) tienen un doble papel: cargan el código y lo hacen disponible en el espacio de nombres. `import` solo para el nombre del módulo es posible (equivalente a `ASDF:LOAD-OP`). Los nombres de los slots no necesitan ser exportados por separado. Las variables globales no pueden ser asignadas desde fuera del módulo (excepto con `eval(mod, :(var = val))` como una salida de escape).
  * Los macros comienzan con `@`, y no están tan integrados en el lenguaje como en Common Lisp; en consecuencia, el uso de macros no es tan generalizado como en este último. Una forma de higiene para [macros](@ref Metaprogramming) es soportada por el lenguaje. Debido a la diferente sintaxis superficial, no hay un equivalente a `COMMON-LISP:&BODY`.
  * *Todas* las funciones son genéricas y utilizan múltiples despachos. Las listas de argumentos no tienen que seguir la misma plantilla, lo que conduce a un poderoso idioma (ver [`do`](@ref)). Los argumentos opcionales y de palabra clave se manejan de manera diferente. Las ambigüedades de método no se resuelven como en el Sistema de Objetos de Lisp Común, lo que requiere la definición de un método más específico para la intersección.
  * Los símbolos no pertenecen a ningún paquete y no contienen ningún valor *per se*. `M.var` evalúa el símbolo `var` en el módulo `M`.
  * Un estilo de programación funcional es totalmente compatible con el lenguaje, incluidas las clausuras, pero no siempre es la solución idiomática para Julia. Algunos [workarounds](@ref man-performance-captured) pueden ser necesarios para el rendimiento al modificar variables capturadas.

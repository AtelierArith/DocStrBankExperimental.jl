```
Base.@assume_effects configurando... [ex]
```

Sobrescribe el modelado de efectos del compilador. Este macro se puede usar en varios contextos:

1. Inmediatamente antes de una definición de método, para sobrescribir todo el modelado de efectos del método aplicado.
2. Dentro de un cuerpo de función sin argumentos, para sobrescribir todo el modelado de efectos del método que lo contiene.
3. Aplicado a un bloque de código, para sobrescribir el modelado de efectos local del bloque de código aplicado.

# Ejemplos

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # uso 1:
           # este :terminates_locally permite que `fact` sea evaluado como constante
           res = 1
           0 ≤ x < 20 || error("mal fact")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (función genérica con 1 método)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # uso 2:
               # este :terminates_locally permite que esta función anónima sea evaluada como constante
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("mal fact")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("mal fact")
               # uso 3:
               # con esta anotación :terminates_locally el compilador omite la contaminación
               # del efecto `:terminates` dentro de este bloque `while`, permitiendo que la función
               # anónima padre sea evaluada como constante
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    Usar `Base.@assume_effects` requiere la versión 1.8 de Julia.


!!! compat "Julia 1.10"
    El uso dentro de un cuerpo de función requiere al menos Julia 1.10.


!!! compat "Julia 1.11"
    La anotación de bloque de código requiere al menos Julia 1.11.


!!! warning
    El uso inapropiado de este macro causa comportamiento indefinido (incluyendo bloqueos, respuestas incorrectas u otros errores difíciles de rastrear). Úselo con cuidado y solo como último recurso si es absolutamente necesario. Incluso en tal caso, DEBE tomar todas las medidas posibles para minimizar la fuerza de la afirmación de efecto (por ejemplo, no use `:total` si `:nothrow` hubiera sido suficiente).


En general, cada valor de `setting` hace una afirmación sobre el comportamiento de la función, sin requerir que el compilador demuestre que este comportamiento es realmente cierto. Estas afirmaciones se hacen para todas las edades del mundo. Por lo tanto, es aconsejable limitar el uso de funciones genéricas que pueden extenderse más tarde para invalidar la suposición (lo que causaría un comportamiento indefinido).

Los siguientes `setting`s son compatibles.

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# Ayuda extendida

---

## `:consistent`

La configuración `:consistent` afirma que para entradas iguales (`===`):

  * La forma de terminación (valor de retorno, excepción, no terminación) siempre será la misma.
  * Si el método retorna, los resultados siempre serán iguales.

!!! note
    Esto implica en particular que el método no debe devolver un objeto mutable recién asignado. Múltiples asignaciones de objetos mutables (incluso con contenidos idénticos) no son iguales.


!!! note
    La afirmación `:consistent` se hace por edad del mundo. Más formalmente, escriba $fᵢ$ para la evaluación de $f$ en la edad del mundo $i$, entonces esta configuración requiere:

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    Sin embargo, para dos edades del mundo $i$, $j$ tales que $i ≠ j$, podemos tener $fᵢ(x) ≢ fⱼ(y)$.

    Una implicación adicional es que las funciones `:consistent` no pueden hacer que su valor de retorno dependa del estado del heap o de cualquier otro estado global que no sea constante para una edad del mundo dada.


!!! note
    La `:consistent` incluye todas las reescrituras legales realizadas por el optimizador. Por ejemplo, las operaciones de fastmath de punto flotante no se consideran `:consistent`, porque el optimizador puede reescribirlas causando que la salida no sea `:consistent`, incluso para la misma edad del mundo (por ejemplo, porque una se ejecutó en el intérprete, mientras que la otra fue optimizada).


!!! note
    Si las funciones `:consistent` terminan lanzando una excepción, esa excepción en sí misma no está obligada a cumplir con el requisito de igualdad especificado anteriormente.


---

## `:effect_free`

La configuración `:effect_free` afirma que el método está libre de efectos secundarios semánticamente visibles externamente. La siguiente es una lista incompleta de efectos secundarios semánticamente visibles externamente:

  * Cambiar el valor de una variable global.
  * Mutar el heap (por ejemplo, un arreglo o valor mutable), excepto como se indica a continuación.
  * Cambiar la tabla de métodos (por ejemplo, a través de llamadas a eval).
  * Entrada/salida de archivos/red/etc.
  * Cambio de tareas.

Sin embargo, lo siguiente no es semánticamente visible, incluso si puede ser observable:

  * Asignaciones de memoria (tanto mutables como inmutables).
  * Tiempo transcurrido.
  * Recolección de basura.
  * Mutaciones del heap de objetos cuya vida útil no excede el método (es decir, que fueron asignados en el método y no escapan).
  * El valor devuelto (que es externamente visible, pero no un efecto secundario).

La regla general aquí es que un efecto secundario visible externamente es cualquier cosa que afectaría la ejecución del resto del programa si la función no se ejecutara.

!!! note
    La afirmación `:effect_free` se hace tanto para el método en sí como para cualquier código que se ejecute por el método. Tenga en cuenta que la afirmación debe ser válida para todas las edades del mundo y limite el uso de esta afirmación en consecuencia.


---

## `:nothrow`

La configuración `:nothrow` afirma que este método no lanza una excepción (es decir, siempre devolverá un valor o nunca devolverá).

!!! note
    Es permisible que los métodos anotados con `:nothrow` utilicen el manejo de excepciones internamente siempre que la excepción no se vuelva a lanzar fuera del método mismo.


!!! note
    Si la ejecución de un método puede generar `MethodError`s y excepciones similares, entonces el método no se considera `:nothrow`. Sin embargo, tenga en cuenta que errores dependientes del entorno como `StackOverflowError` o `InterruptException` no son modelados por este efecto y, por lo tanto, un método que puede resultar en `StackOverflowError` no necesita ser `!:nothrow` (aunque generalmente también debería ser `!:terminates`).


---

## `:terminates_globally`

La configuración `:terminates_globally` afirma que este método eventualmente terminará (ya sea normalmente o anormalmente), es decir, no entra en un bucle indefinido.

!!! note
    Esta afirmación `:terminates_globally` cubre cualquier otro método llamado por el método anotado.


!!! note
    El compilador considerará esto como una fuerte indicación de que el método terminará relativamente *rápidamente* y puede (si es legal de otro modo) llamar a este método en tiempo de compilación. Es decir, es una mala idea anotar esta configuración en un método que *técnicamente*, pero no *prácticamente*, termina.


---

## `:terminates_locally`

La configuración `:terminates_locally` es como `:terminates_globally`, excepto que solo se aplica al flujo de control sintáctico *dentro* del método anotado. Por lo tanto, es una afirmación mucho más débil (y por lo tanto más segura) que permite la posibilidad de no terminación si el método llama a algún otro método que no termina.

!!! note
    `:terminates_globally` implica `:terminates_locally`.


---

## `:notaskstate`

La configuración `:notaskstate` afirma que el método no utiliza ni modifica el estado de tarea local (almacenamiento local de tarea, estado de RNG, etc.) y, por lo tanto, puede ser movido entre tareas sin resultados observables.

!!! note
    La implementación del manejo de excepciones utiliza el estado almacenado en el objeto de tarea. Sin embargo, este estado actualmente no se considera dentro del alcance de `:notaskstate` y se rastrea por separado utilizando el efecto `:nothrow`.


!!! note
    La afirmación `:notaskstate` concierne al estado de la *tarea actualmente en ejecución*. Si se obtiene una referencia a un objeto `Task` por algún otro medio que no considera qué tarea está *actualmente* en ejecución, el efecto `:notaskstate` no necesita ser contaminado. Esto es cierto, incluso si dicho objeto de tarea resulta ser `===` a la tarea actualmente en ejecución.


!!! note
    El acceso al estado de tarea generalmente también resulta en la contaminación de otros efectos, como `:effect_free` (si se modifica el estado de tarea) o `:consistent` (si se utiliza el estado de tarea en el cálculo del resultado). En particular, el código que no es `:notaskstate`, pero es `:effect_free` y `:consistent` puede ser eliminado como código muerto y, por lo tanto, promovido a `:total`.


---

## `:inaccessiblememonly`

La configuración `:inaccessiblememonly` afirma que el método no accede ni modifica memoria mutable accesible externamente. Esto significa que el método puede acceder o modificar memoria mutable para objetos recién asignados que no son accesibles por otros métodos o ejecución de nivel superior antes de retornar del método, pero no puede acceder ni modificar ningún estado global mutable o memoria mutable apuntada por sus argumentos.

!!! note
    A continuación se presenta una lista incompleta de ejemplos que invalidan esta suposición:

      * una referencia global o llamada `getglobal` para acceder a una variable global mutable
      * una asignación global o llamada `setglobal!` para realizar una asignación a una variable global no constante
      * llamada `setfield!` que cambia un campo de una variable mutable global


!!! note
    Esta afirmación `:inaccessiblememonly` cubre cualquier otro método llamado por el método anotado.


---

## `:noub`

La configuración `:noub` afirma que el método no ejecutará ningún comportamiento indefinido (para cualquier entrada). Tenga en cuenta que el comportamiento indefinido puede técnicamente causar que el método viole cualquier otra afirmación de efecto (como `:consistent` o `:effect_free`) también, pero no modelamos esto, y asumen la ausencia de comportamiento indefinido.

---

## `:nortcall`

La configuración `:nortcall` afirma que el método no llama a `Core.Compiler.return_type`, y que cualquier otro método que este método pueda llamar tampoco llama a `Core.Compiler.return_type`.

!!! note
    Para ser precisos, esta afirmación se puede usar cuando no se realiza una llamada a `Core.Compiler.return_type` en tiempo de ejecución; es decir, cuando el resultado de `Core.Compiler.return_type` se conoce exactamente en tiempo de compilación y la llamada es eliminada por el optimizador. Sin embargo, dado que si el resultado de `Core.Compiler.return_type` se pliega en tiempo de compilación depende en gran medida de la implementación del compilador, generalmente es arriesgado afirmar esto si el método en cuestión utiliza `Core.Compiler.return_type` de alguna forma.


---

## `:foldable`

Esta configuración es un atajo conveniente para el conjunto de efectos que el compilador requiere que se garanticen para evaluar una llamada como constante en tiempo de compilación. Actualmente es equivalente a los siguientes `setting`s:

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    Esta lista en particular no incluye `:nothrow`. El compilador aún intentará la propagación constante y notará cualquier error lanzado en tiempo de compilación. Tenga en cuenta, sin embargo, que por los requisitos de `:consistent`, cualquier llamada anotada de este tipo debe lanzar consistentemente dado los mismos valores de argumento.


!!! note
    Una anotación explícita `@inbounds` dentro de la función también deshabilitará la evaluación constante y no será anulada por `:foldable`.


---

## `:removable`

Esta configuración es un atajo conveniente para el conjunto de efectos que el compilador requiere que se garanticen para eliminar una llamada cuyo resultado no se utiliza en tiempo de compilación. Actualmente es equivalente a los siguientes `setting`s:

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

Esta configuración es el conjunto máximo posible de efectos. Actualmente implica los siguientes otros `setting`s:

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total` es una afirmación muy fuerte y probablemente ganará semánticas adicionales en futuras versiones de Julia (por ejemplo, si se agregan efectos adicionales e incluidos en la definición de `:total`). Como resultado, debe usarse con cuidado. Siempre que sea posible, prefiera usar el conjunto mínimo posible de afirmaciones de efecto específicas requeridas para una aplicación particular. En casos donde se apliquen un gran número de sobrescrituras de efecto a un conjunto de funciones, se recomienda un macro personalizado sobre el uso de `:total`.


---

## Efectos negados

Los nombres de efecto pueden ser precedidos por `!` para indicar que el efecto debe ser eliminado de un efecto meta anterior. Por ejemplo, `:total !:nothrow` indica que, aunque la llamada es generalmente total, puede lanzar.

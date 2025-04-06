# Static analyzer annotations for GC correctness in C code

## Running the analysis

El complemento del analizador que impulsa el análisis se envía con julia. Su código fuente se puede encontrar en `src/clangsa`. Ejecutarlo requiere que la dependencia de clang esté construida. Establezca la variable `BUILD_LLVM_CLANG` en su Make.user para construir una versión apropiada de clang. También puede querer usar los binarios preconstruidos utilizando las opciones `USE_BINARYBUILDER_LLVM`.

Alternativamente (o si estos no son suficientes), prueba

```sh
make -C src install-analysis-deps
```

desde el directorio de nivel superior de Julia.

Después, ejecutar el análisis sobre el árbol fuente es tan simple como ejecutar `make -C src analyzegc`.

## General Overview

Dado que el GC de Julia es preciso, necesita mantener información de enraizamiento correcta para cualquier valor que pueda ser referenciado en cualquier momento en que ocurra el GC. Estos lugares se conocen como `puntos seguros` y en el contexto local de la función, extendemos esta designación a cualquier llamada de función que pueda terminar recursivamente en un punto seguro.

En el código generado, esto se maneja automáticamente mediante la pasada de colocación de raíces de GC (consulta el capítulo sobre raíces de GC en la documentación de desarrollo de código de LLVM). Sin embargo, en el código C, necesitamos informar al tiempo de ejecución sobre cualquier raíz de GC manualmente. Esto se hace utilizando los siguientes macros:

```
// The value assigned to any slot passed as an argument to these
// is rooted for the duration of this GC frame.
JL_GC_PUSH{1,...,6}(args...)
// The values assigned into the size `n` array `rts` are rooted
// for the duration of this GC frame.
JL_GC_PUSHARGS(rts, n)
// Pop a GC frame
JL_GC_POP
```

Si estos macros no se utilizan donde deben, o se utilizan incorrectamente, el resultado es una corrupción de memoria silenciosa. Por lo tanto, es muy importante que se coloquen correctamente en todo el código aplicable.

Como tal, empleamos análisis estático (y en particular el analizador estático clang) para ayudar a garantizar que estos macros se utilicen correctamente. El resto de este documento ofrece una visión general de este análisis estático y describe el soporte necesario en la base de código de julia para que las cosas funcionen.

## GC Invariants

Hay dos invariantes simples de corrección:

  * Todas las llamadas a `GC_PUSH` deben ir seguidas de un `GC_POP` apropiado (en la práctica, hacemos cumplir esto a nivel de función).
  * Si un valor no estaba previamente enraizado en ningún punto seguro, puede que ya no sea referenciado después.

Por supuesto, el diablo está en los detalles aquí. En particular, para satisfacer la segunda de las condiciones anteriores, necesitamos saber:

  * Qué llamadas son puntos seguros y cuáles no
  * Qué valores están enraizados en un punto seguro dado y cuáles no
  * Cuando se hace referencia a un valor

Para el segundo punto en particular, necesitamos saber qué ubicaciones de memoria se considerarán como raíces en tiempo de ejecución (es decir, los valores asignados a tales ubicaciones están enraizados). Esto incluye ubicaciones designadas explícitamente como tales al pasarlas a uno de los macros `GC_PUSH`, ubicaciones y valores enraizados globalmente, así como cualquier ubicación accesible recursivamente desde una de esas ubicaciones.

## Static Analysis Algorithm

La idea en sí es muy simple, aunque la implementación es bastante más complicada (principalmente debido a un gran número de casos especiales y complejidades de C y C++). En esencia, hacemos un seguimiento de todas las ubicaciones que están enraizadas, todos los valores que son enraizables y cualquier expresión (asignaciones, asignaciones de memoria, etc.) que afecte la enraizabilidad de cualquier valor enraizable. Luego, en cualquier punto seguro, realizamos un "GC simbólico" y envenenamos cualquier valor que no esté enraizado en dicha ubicación. Si estos valores se referencian más tarde, emitimos un error.

El analizador estático clang funciona construyendo un gráfico de estados y explorando este gráfico en busca de fuentes de errores. Varios nodos en este gráfico son generados por el propio analizador (por ejemplo, para el flujo de control), pero las definiciones anteriores aumentan este gráfico con nuestro propio estado.

El analizador estático es interprocedimental y puede analizar el flujo de control a través de los límites de las funciones. Sin embargo, el analizador estático no es completamente recursivo y toma decisiones heurísticas sobre qué llamadas explorar (además, algunas llamadas son de unidad de traducción cruzada e invisibles para el analizador). En nuestro caso, nuestra definición de corrección requiere información total. Por lo tanto, necesitamos anotar los prototipos de todas las llamadas a funciones con la información que el análisis requiere, incluso si esa información de otro modo estaría disponible mediante análisis estático interprocedimental.

Afortunadamente, sin embargo, aún podemos utilizar este análisis interprocedimental para asegurarnos de que las anotaciones que colocamos en una función dada son, de hecho, correctas dado la implementación de dicha función.

## The analyzer annotations

Estas anotaciones se encuentran en src/support/analyzer_annotations.h. Solo están activas cuando se utiliza el analizador y se expanden ya sea a nada (para anotaciones de prototipo) o a no-ops (para anotaciones de tipo función).

### `JL_NOTSAFEPOINT`

Esta es quizás la anotación más común, y debe colocarse en cualquier función que se sepa que no puede llevar a alcanzar un punto seguro de GC. En general, solo es seguro que tal función realice operaciones aritméticas, accesos a memoria y llamadas a funciones que estén anotadas como `JL_NOTSAFEPOINT` o que se sepa de otro modo que no son puntos seguros (por ejemplo, funciones en la biblioteca estándar de C, que están codificadas como tales en el analizador).

Es válido mantener valores no enraizados a través de llamadas a cualquier función anotada con este atributo:

Ejemplo de uso:

```c
void jl_get_one() JL_NOTSAFEPOINT {
  return 1;
}

jl_value_t *example() {
  jl_value_t *val = jl_alloc_whatever();
  // This is valid, even though `val` is unrooted, because
  // jl_get_one is not a safepoint
  jl_get_one();
  return val;
}
```

### `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`

Cuando `JL_MAYBE_UNROOTED` se anota como un argumento en una función, indica que dicho argumento puede ser pasado, incluso si no está enraizado. En el curso ordinario de los eventos, el ABI de Julia garantiza que los llamadores enraizan los valores antes de pasarlos a los llamados. Sin embargo, algunas funciones no siguen este ABI y permiten que los valores se les pasen incluso si no están enraizados. Sin embargo, hay que tener en cuenta que esto no implica automáticamente que dicho argumento será preservado. La anotación `ROOTS_TEMPORARILY` proporciona la garantía más fuerte de que, no solo puede que el valor esté desenraizado al ser pasado, sino que también será preservado a través de cualquier punto de seguridad interno por el llamado.

Tenga en cuenta que `JL_NOTSAFEPOINT` implica esencialmente `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`, porque la raíz de un argumento es irrelevante si la función no contiene puntos de seguridad.

Un punto adicional a tener en cuenta es que estas anotaciones se aplican tanto en el lado del llamador como en el lado del llamado. En el lado del llamador, levantan las restricciones de enraizamiento que normalmente se requieren para las funciones ABI de julia. En el lado del llamado, tienen el efecto inverso de evitar que estos argumentos sean considerados implícitamente enraizados.

Si se aplica cualquiera de estas anotaciones a la función en su conjunto, se aplica a todos los argumentos de la función. Esto generalmente solo debería ser necesario para funciones varargs.

Ejemplo de uso:

```c
JL_DLLEXPORT void JL_NORETURN jl_throw(jl_value_t *e JL_MAYBE_UNROOTED);
jl_value_t *jl_alloc_error();

void example() {
  // The return value of the allocation is unrooted. This would normally
  // be an error, but is allowed because of the above annotation.
  jl_throw(jl_alloc_error());
}
```

### `JL_PROPAGATES_ROOT`

Esta anotación se encuentra comúnmente en funciones de acceso que devuelven un objeto raíz almacenado dentro de otro. Cuando se anota en un argumento de función, le indica al analizador que la raíz para ese argumento también se aplica al valor devuelto por la función.

Ejemplo de uso:

```c
jl_value_t *jl_svecref(jl_svec_t *t JL_PROPAGATES_ROOT, size_t i) JL_NOTSAFEPOINT;

size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_svecref(svec, 1)
  // This is valid, because, as annotated by the PROPAGATES_ROOT annotation,
  // jl_svecref propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_ROOTING_ARGUMENT`/`JL_ROOTED_ARGUMENT`

Este es esencialmente el contraparte de asignación a `JL_PROPAGATES_ROOT`. Al asignar un valor a un campo de otro valor que ya está enraizado, el valor asignado heredará la raíz del valor en el que se asigna.

Ejemplo de uso:

```c
void jl_svecset(void *t JL_ROOTING_ARGUMENT, size_t i, void *x JL_ROOTED_ARGUMENT) JL_NOTSAFEPOINT


size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_box_long(10000);
  jl_svecset(svec, val);
  // This is valid, because the annotations imply that the
  // jl_svecset propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_GC_DISABLED`

Esta anotación implica que esta función solo se llama con el tiempo de ejecución del GC deshabilitado. Las funciones de este tipo se encuentran más a menudo durante el inicio y en el propio código del GC. Tenga en cuenta que esta anotación se verifica en relación con las llamadas de habilitación/deshabilitación del tiempo de ejecución, por lo que clang sabrá si miente. Esta no es una buena manera de deshabilitar el procesamiento de una función dada si el GC no está realmente deshabilitado (use `ifdef __clang_analyzer__` para eso si es necesario).

Ejemplo de uso:

```c
void jl_do_magic() JL_GC_DISABLED {
  // Wildly allocate here with no regard for roots
}

void example() {
  int en = jl_gc_enable(0);
  jl_do_magic();
  jl_gc_enable(en);
}
```

### `JL_REQUIRE_ROOTED_SLOT`

Esta anotación requiere que el llamador pase un slot que esté enraizado (es decir, los valores asignados a este slot estarán enraizados).

Ejemplo de uso:

```c
void jl_do_processing(jl_value_t **slot JL_REQUIRE_ROOTED_SLOT) {
  *slot = jl_box_long(1);
  // Ok, only, because the slot was annotated as rooting
  jl_gc_safepoint();
}

void example() {
  jl_value_t *slot = NULL;
  JL_GC_PUSH1(&slot);
  jl_do_processing(&slot);
  JL_GC_POP();
}
```

### `JL_GLOBALLY_ROOTED`

Esta anotación implica que un valor dado siempre está enraizado globalmente. Se puede aplicar a las declaraciones de variables globales, en cuyo caso se aplicará al valor de esas variables (o valores si la declaración es para un arreglo), o a funciones, en cuyo caso se aplicará al valor de retorno de tales funciones (por ejemplo, para funciones que siempre devuelven algún valor privado, enraizado globalmente).

Ejemplo de uso:

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

Esta anotación es esencialmente equivalente a `JL_GLOBALLY_ROOTED`, excepto que solo debe usarse si esos valores están globalmente enraizados en virtud de ser un tipo hoja. El enraizamiento de los tipos hoja es un poco complicado. Generalmente están enraizados a través del campo `cache` del correspondiente `TypeName`, que a su vez está enraizado por el módulo contenedor (por lo que están enraizados mientras el módulo contenedor esté bien) y generalmente podemos asumir que los tipos hoja están enraizados donde se utilizan, pero podemos refinar esta propiedad en el futuro, por lo que la anotación separada ayuda a desglosar la razón por la que están globalmente enraizados.

El analizador también detecta automáticamente las comprobaciones de la naturaleza de hoja y no se quejará por la falta de raíces de GC en estos caminos.

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

Esta es una anotación similar a una función. Cualquier valor pasado a esta anotación se considerará enraizado para el alcance de la función actual. Está diseñada como una salida para la insuficiencia del analizador o situaciones complicadas. Sin embargo, debe usarse con moderación, a favor de mejorar el propio analizador.

```
void example() {
  jl_value_t *val = jl_alloc_something();
  if (some_condition) {
    // We happen to know for complicated external reasons
    // that val is rooted under these conditions
    JL_GC_PROMISE_ROOTED(val);
  }
}
```

## Completeness of analysis

El analizador solo considera información local. En particular, por ejemplo, en el caso de `PROPAGATES_ROOT` mencionado anteriormente, asume que dicha memoria solo se modifica de maneras que puede ver, no en ninguna función llamada (a menos que decida considerar esas funciones en su análisis) y no en ningún hilo que se ejecute de manera concurrente. Como tal, puede pasar por alto algunos casos problemáticos, aunque en la práctica tal modificación concurrente es bastante rara. Mejorar el analizador para manejar más de tales casos puede ser un tema interesante para trabajos futuros.

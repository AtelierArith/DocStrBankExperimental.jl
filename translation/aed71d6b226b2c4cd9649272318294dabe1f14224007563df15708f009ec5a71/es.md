# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

La estructura `jl_value_t` es el nombre de un bloque de memoria propiedad del recolector de basura de Julia, que representa los datos asociados con un objeto de Julia en memoria. En ausencia de cualquier información de tipo, es simplemente un puntero opaco:

```c
typedef struct jl_value_t* jl_pvalue_t;
```

Cada estructura `jl_value_t` está contenida en una estructura `jl_typetag_t` que contiene información de metadatos sobre el objeto de Julia, como su tipo y la accesibilidad del recolector de basura (gc):

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

El tipo de cualquier objeto de Julia es una instancia de un objeto hoja `jl_datatype_t`. La función `jl_typeof()` se puede usar para consultarlo:

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

El diseño del objeto depende de su tipo. Se pueden utilizar métodos de reflexión para inspeccionar ese diseño. Un campo se puede acceder llamando a uno de los métodos de obtención de campo:

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

Si los tipos de campo se conocen, a priori, como todos punteros, los valores también se pueden extraer directamente como un acceso a un array:

```c
jl_value_t *v = value->fieldptr[n];
```

Como ejemplo, un `uint16_t` "en caja" se almacena de la siguiente manera:

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

Este objeto es creado por `jl_box_uint16()`. Tenga en cuenta que el puntero `jl_value_t` hace referencia a la porción de datos, no a los metadatos en la parte superior de la estructura.

Un valor puede ser almacenado "sin caja" en muchas circunstancias (solo los datos, sin los metadatos, y posiblemente ni siquiera almacenado, sino solo mantenido en registros), por lo que no es seguro asumir que la dirección de una caja es un identificador único. La prueba "egal" (correspondiente a la función `===` en Julia) debe ser utilizada en su lugar para comparar dos objetos desconocidos por equivalencia:

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

Esta optimización debería ser relativamente transparente para la API, ya que el objeto será "encapsulado" bajo demanda, siempre que se necesite un puntero `jl_value_t`.

Tenga en cuenta que la modificación de un puntero `jl_value_t` en memoria solo está permitida si el objeto es mutable. De lo contrario, la modificación del valor puede corromper el programa y el resultado será indefinido. La propiedad de mutabilidad de un valor se puede consultar con:

```c
int jl_is_mutable(jl_value_t *v);
```

Si el objeto que se está almacenando es un `jl_value_t`, el recolector de basura de Julia también debe ser notificado:

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

Sin embargo, la sección [Embedding Julia](@ref) del manual también es lectura obligatoria en este punto, ya que cubre otros detalles sobre el empaquetado y desempaquetado de varios tipos, y la comprensión de las interacciones del gc.

Los structs espejo para algunos de los tipos incorporados son [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Los objetos globales correspondientes `jl_datatype_t` se crean mediante [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c).

## Garbage collector mark bits

El recolector de basura utiliza varios bits de la porción de metadatos de `jl_typetag_t` para rastrear cada objeto en el sistema. Se pueden encontrar más detalles sobre este algoritmo en los comentarios de [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c).

## Object allocation

La mayoría de los nuevos objetos se asignan mediante `jl_new_structv()`:

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

Aunque, [`isbits`](@ref) los objetos también se pueden construir directamente desde la memoria:

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

Y algunos objetos tienen constructores especiales que deben usarse en lugar de las funciones anteriores:

Tipos:

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

Mientras que estas son las opciones más comúnmente utilizadas, también hay más constructores de bajo nivel, que puedes encontrar declarados en [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Estos se utilizan en `jl_init_types()` para crear los tipos iniciales necesarios para iniciar la creación de la imagen del sistema Julia.

Tuplas:

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

La representación de tuplas es altamente única en el ecosistema de representación de objetos de Julia. En algunos casos, un objeto [`Base.tuple()`](@ref) puede ser un array de punteros a los objetos contenidos por la tupla equivalente a:

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

Sin embargo, en otros casos, la tupla puede ser convertida a un tipo anónimo [`isbits`](@ref) y almacenada sin empaquetar, o puede que no se almacene en absoluto (si no se está utilizando en un contexto genérico como un `jl_value_t*`).

Símbolos:

```c
jl_sym_t *jl_symbol(const char *str);
```

Funciones y MethodInstance:

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

Arreglos:

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

Tenga en cuenta que muchos de estos tienen funciones de asignación alternativas para diversos propósitos especiales. La lista aquí refleja los usos más comunes, pero se puede encontrar una lista más completa leyendo el [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h).

Internamente en Julia, la memoria se asigna típicamente mediante `newstruct()` (o `newobj()` para los tipos especiales):

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

Y en el nivel más bajo, la memoria se asigna mediante una llamada al recolector de basura (en `gc.c`), luego se etiqueta con su tipo:

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    La documentación y el uso de la función `jl_gc_allocobj` pueden estar desactualizados.


Tenga en cuenta que todos los objetos se asignan en múltiplos de 4 bytes y se alinean al tamaño del puntero de la plataforma. La memoria se asigna de un grupo para objetos más pequeños, o directamente con `malloc()` para objetos grandes.

!!! sidebar "Singleton Types"
    Los tipos Singleton tienen solo una instancia y no campos de datos. Las instancias Singleton tienen un tamaño de 0 bytes y consisten únicamente en sus metadatos. p. ej. `nothing::Nothing`.

    Vea [Singleton Types](@ref man-singleton-types) y [Nothingness and missing values](@ref)


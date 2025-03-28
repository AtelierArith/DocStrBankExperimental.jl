# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

Die `jl_value_t`-Struktur ist der Name für einen Speicherblock, der vom Julia Garbage Collector verwaltet wird und die mit einem Julia-Objekt im Speicher verbundenen Daten darstellt. In Abwesenheit von Typinformationen ist es einfach ein undurchsichtiger Zeiger:

```c
typedef struct jl_value_t* jl_pvalue_t;
```

Jede `jl_value_t`-Struktur ist in einer `jl_typetag_t`-Struktur enthalten, die Metadateninformationen über das Julia-Objekt enthält, wie z. B. seinen Typ und die Erreichbarkeit durch den Garbage Collector (gc):

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

Der Typ eines beliebigen Julia-Objekts ist eine Instanz eines Blatt-`jl_datatype_t`-Objekts. Die Funktion `jl_typeof()` kann verwendet werden, um danach zu fragen:

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

Das Layout des Objekts hängt von seinem Typ ab. Reflexionsmethoden können verwendet werden, um dieses Layout zu inspizieren. Ein Feld kann durch Aufrufen einer der get-field-Methoden zugegriffen werden:

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

Wenn die Feldtypen a priori bekannt sind und alle Zeiger sind, können die Werte auch direkt als Array-Zugriff extrahiert werden:

```c
jl_value_t *v = value->fieldptr[n];
```

Als Beispiel wird ein "verpackter" `uint16_t` wie folgt gespeichert:

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

Dieses Objekt wird von `jl_box_uint16()` erstellt. Beachten Sie, dass der `jl_value_t`-Zeiger auf den Datenbereich verweist, nicht auf die Metadaten oben in der Struktur.

Ein Wert kann in vielen Umständen "unboxed" gespeichert werden (nur die Daten, ohne die Metadaten, und möglicherweise nicht einmal gespeichert, sondern nur in Registern gehalten), daher ist es unsicher anzunehmen, dass die Adresse einer Box ein eindeutiger Identifikator ist. Der "egal" Test (entsprechend der `===` Funktion in Julia) sollte stattdessen verwendet werden, um zwei unbekannte Objekte auf Äquivalenz zu vergleichen:

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

Diese Optimierung sollte für die API relativ transparent sein, da das Objekt "on-demand" "verpackt" wird, wann immer ein `jl_value_t`-Zeiger benötigt wird.

Beachten Sie, dass die Modifikation eines `jl_value_t` Zeigers im Speicher nur erlaubt ist, wenn das Objekt veränderlich ist. Andernfalls kann die Modifikation des Wertes das Programm beschädigen und das Ergebnis wird undefiniert sein. Die Änderbarkeitseigenschaft eines Wertes kann mit folgender Abfrage überprüft werden:

```c
int jl_is_mutable(jl_value_t *v);
```

Wenn das zu speichernde Objekt ein `jl_value_t` ist, muss auch der Julia-Garbage-Collector benachrichtigt werden:

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

Allerdings ist der Abschnitt [Embedding Julia](@ref) des Handbuchs zu diesem Zeitpunkt ebenfalls Pflichtlektüre, um weitere Details zum Boxen und Unboxen verschiedener Typen sowie die Interaktionen mit dem Garbage Collector zu verstehen.

Die Spiegelstrukturen für einige der eingebauten Typen sind [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Die entsprechenden globalen `jl_datatype_t`-Objekte werden erstellt durch [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c).

## Garbage collector mark bits

Der Garbage Collector verwendet mehrere Bits aus dem Metadatenbereich von `jl_typetag_t`, um jedes Objekt im System zu verfolgen. Weitere Details zu diesem Algorithmus finden Sie in den Kommentaren von [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c).

## Object allocation

Die meisten neuen Objekte werden von `jl_new_structv()` zugewiesen:

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

Obwohl [`isbits`](@ref) Objekte auch direkt aus dem Speicher erstellt werden können:

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

Und einige Objekte haben spezielle Konstruktoren, die anstelle der oben genannten Funktionen verwendet werden müssen:

Arten:

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

Während dies die am häufigsten verwendeten Optionen sind, gibt es auch weitere Low-Level-Konstruktoren, die Sie in [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) finden können. Diese werden in `jl_init_types()` verwendet, um die anfänglichen Typen zu erstellen, die benötigt werden, um die Erstellung des Julia-Systemimages zu bootstrappen.

Tuples:

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

Die Darstellung von Tupeln ist im Ökosystem der Objektrepräsentation von Julia äußerst einzigartig. In einigen Fällen kann ein [`Base.tuple()`](@ref) Objekt ein Array von Zeigern auf die Objekte sein, die durch das Tupel enthalten sind, was dem entspricht:

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

Allerdings kann in anderen Fällen das Tupel in einen anonymen [`isbits`](@ref) Typ umgewandelt und unboxed gespeichert werden, oder es wird möglicherweise gar nicht gespeichert (wenn es nicht in einem generischen Kontext als `jl_value_t*` verwendet wird).

Symbole:

```c
jl_sym_t *jl_symbol(const char *str);
```

Funktionen und MethodInstance:

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

Arrays:

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

Beachten Sie, dass viele dieser Funktionen alternative Zuweisungen für verschiedene Sonderzwecke haben. Die hier aufgeführte Liste spiegelt die gebräuchlicheren Verwendungen wider, aber eine vollständigere Liste finden Sie, indem Sie die [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h) lesen.

Intern zu Julia wird der Speicher typischerweise durch `newstruct()` (oder `newobj()` für die speziellen Typen) zugewiesen:

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

Und auf der niedrigsten Ebene wird der Speicher durch einen Aufruf des Garbage Collectors (in `gc.c`) zugewiesen und dann mit seinem Typ gekennzeichnet:

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    Die Dokumentation und Verwendung der Funktion `jl_gc_allocobj` könnte veraltet sein.


Beachten Sie, dass alle Objekte in Vielfachen von 4 Bytes zugewiesen und an die Zeigergröße der Plattform ausgerichtet sind. Der Speicher wird aus einem Pool für kleinere Objekte oder direkt mit `malloc()` für große Objekte zugewiesen.

!!! sidebar "Singleton Types"
    Singleton-Typen haben nur eine Instanz und keine Datenfelder. Singleton-Instanzen haben eine Größe von 0 Bytes und bestehen nur aus ihren Metadaten. z.B. `nothing::Nothing`.

    Siehe [Singleton Types](@ref man-singleton-types) und [Nothingness and missing values](@ref)


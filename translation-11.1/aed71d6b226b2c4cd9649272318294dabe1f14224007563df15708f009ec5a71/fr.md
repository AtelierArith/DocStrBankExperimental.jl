# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

La structure `jl_value_t` est le nom d'un bloc de mémoire détenu par le ramasse-miettes de Julia, représentant les données associées à un objet Julia en mémoire. En l'absence de toute information de type, il s'agit simplement d'un pointeur opaque :

```c
typedef struct jl_value_t* jl_pvalue_t;
```

Chaque struct `jl_value_t` est contenue dans une struct `jl_typetag_t` qui contient des informations de métadonnées sur l'objet Julia, telles que son type et la portée du ramasse-miettes (gc) :

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

Le type de tout objet Julia est une instance d'un objet feuille `jl_datatype_t`. La fonction `jl_typeof()` peut être utilisée pour le consulter :

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

La disposition de l'objet dépend de son type. Des méthodes de réflexion peuvent être utilisées pour inspecter cette disposition. Un champ peut être accédé en appelant l'une des méthodes de récupération de champ :

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

Si les types de champ sont connus, a priori, pour être tous des pointeurs, les valeurs peuvent également être extraites directement comme un accès au tableau :

```c
jl_value_t *v = value->fieldptr[n];
```

En tant qu'exemple, un `uint16_t` "encapsulé" est stocké comme suit :

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

Cet objet est créé par `jl_box_uint16()`. Notez que le pointeur `jl_value_t` fait référence à la portion de données, et non aux métadonnées en haut de la structure.

Une valeur peut être stockée "non encapsulée" dans de nombreuses circonstances (juste les données, sans les métadonnées, et peut-être même pas stockée mais simplement conservée dans des registres), il est donc dangereux de supposer que l'adresse d'une boîte est un identifiant unique. Le test "égal" (correspondant à la fonction `===` en Julia) doit plutôt être utilisé pour comparer deux objets inconnus pour équivalence :

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

Cette optimisation devrait être relativement transparente pour l'API, puisque l'objet sera "encapsulé" à la demande, chaque fois qu'un pointeur `jl_value_t` est nécessaire.

Notez que la modification d'un pointeur `jl_value_t` en mémoire n'est autorisée que si l'objet est mutable. Sinon, la modification de la valeur peut corrompre le programme et le résultat sera indéfini. La propriété de mutabilité d'une valeur peut être interrogée avec :

```c
int jl_is_mutable(jl_value_t *v);
```

Si l'objet stocké est un `jl_value_t`, le ramasse-miettes de Julia doit également être notifié :

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

Cependant, la section [Embedding Julia](@ref) du manuel est également une lecture obligatoire à ce stade, car elle couvre d'autres détails sur le boxing et le unboxing de divers types, ainsi que sur la compréhension des interactions avec le gc.

Les structures miroir pour certains des types intégrés sont [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Les objets `jl_datatype_t` globaux correspondants sont créés par [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c).

## Garbage collector mark bits

Le ramasse-miettes utilise plusieurs bits de la portion de métadonnées de `jl_typetag_t` pour suivre chaque objet dans le système. D'autres détails sur cet algorithme peuvent être trouvés dans les commentaires de [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c).

## Object allocation

La plupart des nouveaux objets sont alloués par `jl_new_structv()`:

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

Bien que les objets [`isbits`](@ref) puissent également être construits directement à partir de la mémoire :

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

Et certains objets ont des constructeurs spéciaux qui doivent être utilisés à la place des fonctions ci-dessus :

Types :

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

Bien que ce soient les options les plus couramment utilisées, il existe également d'autres constructeurs de bas niveau, que vous pouvez trouver déclarés dans [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Ceux-ci sont utilisés dans `jl_init_types()` pour créer les types initiaux nécessaires au démarrage de la création de l'image système de Julia.

Tuples :

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

La représentation des tuples est très unique dans l'écosystème de représentation des objets de Julia. Dans certains cas, un objet [`Base.tuple()`](@ref) peut être un tableau de pointeurs vers les objets contenus par le tuple équivalent à :

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

Cependant, dans d'autres cas, le tuple peut être converti en un type anonyme [`isbits`](@ref) et stocké sans boîte, ou il peut ne pas être stocké du tout (s'il n'est pas utilisé dans un contexte générique en tant que `jl_value_t*`).

Symboles :

```c
jl_sym_t *jl_symbol(const char *str);
```

Fonctions et Instance de Méthode :

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

Tableaux :

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

Notez que beaucoup de ces fonctions ont des fonctions d'allocation alternatives pour divers usages spéciaux. La liste ici reflète les usages les plus courants, mais une liste plus complète peut être trouvée en lisant le [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h).

En interne, le stockage est généralement alloué par `newstruct()` (ou `newobj()` pour les types spéciaux) :

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

Et au niveau le plus bas, la mémoire est allouée par un appel au ramasse-miettes (dans `gc.c`), puis étiquetée avec son type :

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    La documentation et l'utilisation de la fonction `jl_gc_allocobj` peuvent être obsolètes.


Notez que tous les objets sont alloués par multiples de 4 octets et alignés à la taille du pointeur de la plateforme. La mémoire est allouée à partir d'un pool pour les petits objets, ou directement avec `malloc()` pour les grands objets.

!!! sidebar "Singleton Types"
    Les types Singleton n'ont qu'une seule instance et aucun champ de données. Les instances Singleton ont une taille de 0 octet et se composent uniquement de leurs métadonnées. par ex. `nothing::Nothing`.

    Voir [Singleton Types](@ref man-singleton-types) et [Nothingness and missing values](@ref)


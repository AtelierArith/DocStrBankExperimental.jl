# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

`jl_value_t` yapısı, bellek üzerinde bir Julia nesnesi ile ilişkili veriyi temsil eden, Julia Çöp Toplayıcısı tarafından sahip olunan bir bellek bloğunun adıdır. Herhangi bir tür bilgisi olmadan, basitçe opak bir işaretçidir:

```c
typedef struct jl_value_t* jl_pvalue_t;
```

Her `jl_value_t` yapısı, Julia nesnesi hakkında türü ve çöp toplayıcı (gc) erişilebilirliği gibi meta veri bilgilerini içeren bir `jl_typetag_t` yapısında yer almaktadır:

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

Herhangi bir Julia nesnesinin türü, bir yaprak `jl_datatype_t` nesnesinin bir örneğidir. `jl_typeof()` fonksiyonu, bunu sorgulamak için kullanılabilir:

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

Nesnenin düzeni, türüne bağlıdır. Yansıma yöntemleri, bu düzeni incelemek için kullanılabilir. Bir alana, alanı alma yöntemlerinden birini çağırarak erişilebilir:

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

Eğer alan türleri önceden biliniyorsa ve hepsi işaretçi ise, değerler doğrudan bir dizi erişimi olarak da çıkarılabilir:

```c
jl_value_t *v = value->fieldptr[n];
```

Bir örnek olarak, "kutulu" bir `uint16_t` şu şekilde saklanır:

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

Bu nesne `jl_box_uint16()` ile oluşturulur. `jl_value_t` işaretçisinin veri bölümünü, yapının üstündeki meta veriyi değil, referans aldığını unutmayın.

Bir değer birçok durumda "kutusuz" olarak saklanabilir (sadece veri, meta veriler olmadan ve muhtemelen saklanmadan, sadece kayıtlarda tutulabilir), bu nedenle bir kutunun adresinin benzersiz bir tanımlayıcı olduğunu varsaymak güvenli değildir. İki bilinmeyen nesneyi eşitlik açısından karşılaştırmak için bunun yerine "egal" testi (Julia'daki `===` fonksiyonuna karşılık gelen) kullanılmalıdır:

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

Bu optimizasyon, API için nispeten şeffaf olmalıdır, çünkü nesne, bir `jl_value_t` işaretçesine ihtiyaç duyulduğunda "kutulanacak" şekilde talep üzerine işlenir.

`jl_value_t` işaretçisinin bellekte değiştirilmesine yalnızca nesne değiştirilebilir olduğunda izin verilir. Aksi takdirde, değerin değiştirilmesi programı bozabilir ve sonuç belirsiz olacaktır. Bir değerin değiştirilebilirlik özelliği şu şekilde sorgulanabilir:

```c
int jl_is_mutable(jl_value_t *v);
```

Eğer saklanan nesne bir `jl_value_t` ise, Julia çöp toplayıcısının da bilgilendirilmesi gerekir:

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

Ancak, bu noktada [Embedding Julia](@ref) bölümünün de okunması gerekmektedir; çünkü çeşitli türlerin kutulanması ve kutudan çıkarılması ile ilgili diğer ayrıntıları kapsamakta ve gc etkileşimlerini anlamaya yardımcı olmaktadır.

Aynı yapıların bazıları için ayna yapılar [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). Karşılık gelen global `jl_datatype_t` nesneleri [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) tarafından oluşturulmuştur.

## Garbage collector mark bits

Çöp toplayıcı, sistemdeki her nesneyi izlemek için `jl_typetag_t`'nin meta veri bölümünden birkaç bit kullanır. Bu algoritma hakkında daha fazla ayrıntı, [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) yorumlarında bulunabilir.

## Object allocation

Çoğu yeni nesne `jl_new_structv()` ile tahsis edilir:

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

Ancak, [`isbits`](@ref) nesneleri doğrudan bellekten de oluşturulabilir:

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

Ve bazı nesnelerin yukarıdaki fonksiyonlar yerine kullanılacak özel yapıcıları vardır:

Türler:

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

Bu en yaygın kullanılan seçenekler olsa da, [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) içinde tanımlanan daha düşük seviyeli yapıcılar da vardır. Bunlar, Julia sistem görüntüsünün oluşturulmasını başlatmak için gereken başlangıç türlerini oluşturmak üzere `jl_init_types()` içinde kullanılır.

Demetler:

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

Tuple'ların temsili, Julia nesne temsili ekosisteminde son derece benzersizdir. Bazı durumlarda, bir [`Base.tuple()`](@ref) nesnesi, tuple ile eşdeğer olan nesneleri içeren işaretçilerin bir dizisi olabilir:

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

Ancak, diğer durumlarda, demet anonim bir [`isbits`](@ref) türüne dönüştürülebilir ve kutusuz olarak saklanabilir veya hiç saklanmayabilir (eğer `jl_value_t*` olarak genel bir bağlamda kullanılmıyorsa).

Semboller:

```c
jl_sym_t *jl_symbol(const char *str);
```

Fonksiyonlar ve MethodInstance:

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

Diziler:

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

Not edin ki, bunların birçoğunun çeşitli özel amaçlar için alternatif tahsis fonksiyonları vardır. Buradaki liste daha yaygın kullanımları yansıtmaktadır, ancak daha kapsamlı bir listeyi [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h) okuyarak bulabilirsiniz.

Julia'nın iç yapısında, depolama genellikle `newstruct()` (veya özel türler için `newobj()`) ile tahsis edilir:

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

Ve en düşük seviyede, bellek, çöp toplayıcıya (`gc.c` içinde) yapılan bir çağrı ile tahsis edilir, ardından türü ile etiketlenir:

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    `jl_gc_allocobj` işlevinin belgeleri ve kullanımı güncel olmayabilir.


Not edin ki tüm nesneler 4 baytın katları halinde tahsis edilir ve platform işaretçi boyutuna göre hizalanır. Bellek, daha küçük nesneler için bir havuzdan, büyük nesneler için ise doğrudan `malloc()` ile tahsis edilir.

!!! sidebar "Singleton Types"
    Singleton türleri yalnızca bir örneğe sahiptir ve veri alanı yoktur. Singleton örnekleri 0 bayt boyutundadır ve yalnızca meta verilerinden oluşur. örn. `nothing::Nothing`.

    Gör [Singleton Types](@ref man-singleton-types) ve [Nothingness and missing values](@ref)


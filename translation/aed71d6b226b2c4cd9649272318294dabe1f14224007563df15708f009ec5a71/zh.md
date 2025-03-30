# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

`jl_value_t` 结构是由 Julia 垃圾收集器拥有的一块内存的名称，表示与内存中 Julia 对象相关的数据。在没有任何类型信息的情况下，它只是一个不透明指针：

```c
typedef struct jl_value_t* jl_pvalue_t;
```

每个 `jl_value_t` 结构体包含在一个 `jl_typetag_t` 结构体中，该结构体包含关于 Julia 对象的元数据，例如其类型和垃圾收集器 (gc) 可达性：

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

任何 Julia 对象的类型都是一个叶子 `jl_datatype_t` 对象的实例。可以使用 `jl_typeof()` 函数来查询它：

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

对象的布局取决于其类型。可以使用反射方法来检查该布局。可以通过调用其中一个获取字段的方法来访问字段：

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

如果字段类型已知，事先确定为所有指针，则值也可以直接作为数组访问提取：

```c
jl_value_t *v = value->fieldptr[n];
```

作为示例，一个“盒装”的 `uint16_t` 存储如下：

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

此对象是通过 `jl_box_uint16()` 创建的。请注意，`jl_value_t` 指针引用的是数据部分，而不是结构体顶部的元数据。

一个值在许多情况下可以“未包装”存储（仅数据，没有元数据，可能甚至不存储而只是保留在寄存器中），因此假设一个盒子的地址是唯一标识符是不安全的。应该使用“平等”测试（对应于Julia中的`===`函数）来比较两个未知对象的等价性：

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

此优化对 API 应该是相对透明的，因为对象将在需要 `jl_value_t` 指针时按需“装箱”。

请注意，只有在对象是可变的情况下，才能修改内存中的 `jl_value_t` 指针。否则，修改该值可能会破坏程序，结果将是未定义的。可以通过以下方式查询值的可变性属性：

```c
int jl_is_mutable(jl_value_t *v);
```

如果存储的对象是一个 `jl_value_t`，则必须通知 Julia 垃圾收集器：

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

然而，手册的 [Embedding Julia](@ref) 部分在此时也是必读内容，因为它涵盖了各种类型的装箱和拆箱的其他细节，以及理解垃圾回收的交互。

镜像结构体对于一些内置类型是 [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h)。相应的全局 `jl_datatype_t` 对象是通过 [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) 创建的。

## Garbage collector mark bits

垃圾收集器使用 `jl_typetag_t` 的元数据部分中的几个位来跟踪系统中的每个对象。有关此算法的更多详细信息，请参见 [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) 的注释。

## Object allocation

大多数新对象是通过 `jl_new_structv()` 分配的：

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

尽管 [`isbits`](@ref) 对象也可以直接从内存中构造：

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

有些对象具有特殊的构造函数，必须使用这些构造函数而不是上述函数：

类型：

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

虽然这些是最常用的选项，但还有更多低级构造函数，您可以在 [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) 中找到它们的声明。这些构造函数在 `jl_init_types()` 中用于创建引导创建 Julia 系统映像所需的初始类型。

元组：

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

元组的表示在Julia对象表示生态系统中是非常独特的。在某些情况下，一个 [`Base.tuple()`](@ref) 对象可能是指向元组所包含对象的指针数组，等同于：

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

然而，在其他情况下，元组可能会被转换为一个匿名 [`isbits`](@ref) 类型并以未包装的形式存储，或者根本不存储（如果它没有在作为 `jl_value_t*` 的泛型上下文中使用）。

符号：

```c
jl_sym_t *jl_symbol(const char *str);
```

函数和方法实例：

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

数组：

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

请注意，这些中有许多具有各种特殊用途的替代分配函数。这里的列表反映了更常见的用法，但可以通过阅读 [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h) 找到更完整的列表。

在Julia内部，存储通常通过`newstruct()`（或对于特殊类型使用`newobj()`）进行分配：

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

在最低层，内存通过对垃圾收集器的调用（在 `gc.c` 中）进行分配，然后标记其类型：

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    函数 `jl_gc_allocobj` 的文档和用法可能已经过时。


请注意，所有对象都是以4字节的倍数分配，并与平台指针大小对齐。内存是从池中为较小的对象分配的，或者对于较大的对象直接使用`malloc()`分配。

!!! sidebar "Singleton Types"
    单例类型只有一个实例，并且没有数据字段。单例实例的大小为0字节，仅由其元数据组成。例如：`nothing::Nothing`。

    请参见 [Singleton Types](@ref man-singleton-types) 和 [Nothingness and missing values](@ref)


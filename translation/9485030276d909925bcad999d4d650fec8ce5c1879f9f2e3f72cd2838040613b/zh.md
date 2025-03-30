# Embedding Julia

正如我们在 [Calling C and Fortran Code](@ref) 中看到的，Julia 有一种简单而高效的方法来调用用 C 编写的函数。但在某些情况下，需要反过来：从 C 代码调用 Julia 函数。这可以用于将 Julia 代码集成到更大的 C/C++ 项目中，而无需将所有内容重写为 C/C++。Julia 有一个 C API 使这成为可能。由于几乎所有编程语言都有某种方式来调用 C 函数，因此 Julia C API 也可以用于构建进一步的语言桥接（例如，从 Python、Rust 或 C# 调用 Julia）。尽管 Rust 和 C++ 可以直接使用 C 嵌入 API，但两者都有帮助的包，对于 C++，[Jluna](https://github.com/Clemapfel/jluna) 是有用的。

## High-Level Embedding

**注意**：本节介绍在类Unix操作系统中将Julia代码嵌入C语言。有关在Windows上执行此操作的信息，请参见后面的部分，[High-Level Embedding on Windows with Visual Studio](@ref)。

我们从一个简单的 C 程序开始，该程序初始化 Julia 并调用一些 Julia 代码：

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

为了构建此程序，您必须将Julia头文件的路径添加到包含路径中，并链接`libjulia`。例如，当Julia安装在`$JULIA_DIR`时，可以使用`gcc`编译上述测试程序`test.c`：

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

另外，可以查看Julia源代码树中`test/embedding/`文件夹中的`embedding.c`程序。文件`cli/loader_exe.c`程序是另一个简单的示例，展示了如何在链接`libjulia`时设置`jl_options`选项。

在调用任何其他 Julia C 函数之前，必须首先初始化 Julia。这是通过调用 `jl_init` 来完成的，它会尝试自动确定 Julia 的安装位置。如果您需要指定自定义位置，或指定要加载的系统映像，请改用 `jl_init_with_image`。

测试程序中的第二个语句使用对 `jl_eval_string` 的调用来评估一个 Julia 语句。

在程序终止之前，强烈建议调用 `jl_atexit_hook`。上述示例程序在从 `main` 返回之前调用了它。

!!! note
    目前，动态链接 `libjulia` 共享库需要传递 `RTLD_GLOBAL` 选项。在 Python 中，这看起来像是：

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    如果 Julia 程序需要访问主可执行文件中的符号，则可能需要在 Linux 上的编译时添加 `-Wl,--export-dynamic` 链接器标志，除了下面由 `julia-config.jl` 生成的标志。这在编译共享库时不是必需的。


### Using julia-config to automatically determine build parameters

脚本 `julia-config.jl` 的创建旨在帮助确定使用嵌入式 Julia 的程序所需的构建参数。该脚本使用被调用的特定 Julia 发行版的构建参数和系统配置，导出嵌入程序与该发行版交互所需的编译器标志。该脚本位于 Julia 共享数据目录中。

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

这个脚本的一个简单用法是在命令行中。假设 `julia-config.jl` 位于 `/usr/local/julia/share/julia`，可以直接在命令行中调用，并接受任意组合的三个标志：

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

如果上述示例源代码保存在文件 `embed_example.c` 中，则以下命令将在 Linux 和 Windows（MSYS2 环境）中将其编译为可执行程序。在 macOS 上，将 `gcc` 替换为 `clang`。

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

一般来说，嵌入项目会比上述示例更复杂，因此以下内容也允许通用的 makefile 支持——假设使用 GNU make，因为使用了 **shell** 宏扩展。此外，尽管 `julia-config.jl` 通常位于 `/usr/local` 目录，如果不在该目录中，则可以使用 Julia 本身来查找 `julia-config.jl`，并且 makefile 可以利用这一点。上述示例扩展为使用 makefile：

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

现在构建命令简单地是 `make`。

## High-Level Embedding on Windows with Visual Studio

如果尚未设置 `JULIA_DIR` 环境变量，请在启动 Visual Studio 之前通过系统面板添加它。JULIA_DIR 下的 `bin` 文件夹应在系统 PATH 中。

我们首先打开 Visual Studio 并创建一个新的控制台应用程序项目。打开 'stdafx.h' 头文件，并在末尾添加以下行：

```c
#include <julia.h>
```

然后，用以下代码替换项目中的 main() 函数：

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

下一步是设置项目以查找 Julia 包含文件和库。了解 Julia 安装是 32 位还是 64 位非常重要。在继续之前，请删除任何与 Julia 安装不对应的平台配置。

使用项目属性对话框，转到 `C/C++` | `General`，并将 `$(JULIA_DIR)\include\julia\` 添加到附加包含目录属性中。然后，转到 `Linker` | `General` 部分，将 `$(JULIA_DIR)\lib` 添加到附加库目录属性中。最后，在 `Linker` | `Input` 下，将 `libjulia.dll.a;libopenlibm.dll.a;` 添加到库列表中。

此时，项目应该可以构建并运行。

## Converting Types

真实应用不仅需要执行表达式，还需要将其值返回给主程序。 `jl_eval_string` 返回一个 `jl_value_t*`，这是指向堆分配的 Julia 对象的指针。以这种方式存储简单数据类型，如 [`Float64`](@ref) 被称为 `boxing`，而提取存储的原始数据被称为 `unboxing`。我们改进后的示例程序计算 2 的平方根并在 C 中读取结果的主体现在包含以下代码：

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

为了检查 `ret` 是否为特定的 Julia 类型，我们可以使用 `jl_isa`、`jl_typeis` 或 `jl_is_...` 函数。通过在 Julia shell 中输入 `typeof(sqrt(2.0))`，我们可以看到返回类型是 [`Float64`](@ref)（在 C 中为 `double`）。在上述代码片段中，使用 `jl_unbox_float64` 函数将被封装的 Julia 值转换为 C double。

相应的 `jl_box_...` 函数用于反向转换：

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

如我们接下来将看到的，调用具有特定参数的Julia函数需要进行装箱。

## Calling Julia Functions

虽然 `jl_eval_string` 允许 C 获取 Julia 表达式的结果，但它不允许将 C 中计算的参数传递给 Julia。为此，您需要直接调用 Julia 函数，使用 `jl_call`：

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

在第一步，通过调用 `jl_get_function` 获取对 Julia 函数 `sqrt` 的句柄。传递给 `jl_get_function` 的第一个参数是指向定义 `sqrt` 的 `Base` 模块的指针。然后，使用 `jl_box_float64` 对双精度值进行装箱。最后，在最后一步，使用 `jl_call1` 调用该函数。还存在 `jl_call0`、`jl_call2` 和 `jl_call3` 函数，以方便处理不同数量的参数。要传递更多参数，请使用 `jl_call`：

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

它的第二个参数 `args` 是一个 `jl_value_t*` 参数的数组，`nargs` 是参数的数量。

还有一种替代方法，可能更简单地调用 Julia 函数，即通过 [`@cfunction`](@ref)。使用 `@cfunction` 允许您在 Julia 端进行类型转换，这通常比在 C 端进行转换更容易。上面的 `sqrt` 示例使用 `@cfunction` 可以写成：

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

我们首先在 Julia 中定义一个可调用的 C 函数，从中提取函数指针，最后调用它。除了通过在更高级的语言中进行类型转换来简化类型转换外，通过 `@cfunction` 指针调用 Julia 函数消除了 `jl_call` 所需的动态调度开销（所有参数都是“盒装”的），并且性能应与原生 C 函数指针相当。

## Memory Management

正如我们所看到的，Julia 对象在 C 中表示为类型为 `jl_value_t*` 的指针。这引发了一个问题：谁负责释放这些对象。

通常，Julia 对象由垃圾收集器（GC）释放，但 GC 并不知道我们从 C 持有对 Julia 值的引用。这意味着 GC 可能会在你不知情的情况下释放对象，从而使指针变得无效。

GC 仅在分配新的 Julia 对象时运行。像 `jl_box_float64` 这样的调用会进行分配，但在运行 Julia 代码的任何时刻也可能发生分配。

在嵌入 Julia 的代码中，通常可以安全地在 `jl_...` 调用之间使用 `jl_value_t*` 值（因为 GC 只会在这些调用中被触发）。但是，为了确保值能够在 `jl_...` 调用中存活，我们必须告诉 Julia 我们仍然持有对 Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf) 值的引用，这个过程称为 "GC rooting"。根植一个值将确保垃圾收集器不会意外地将该值识别为未使用并释放支持该值的内存。这可以使用 `JL_GC_PUSH` 宏来完成：

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

`JL_GC_POP` 调用释放由之前的 `JL_GC_PUSH` 建立的引用。请注意，`JL_GC_PUSH` 将引用存储在 C 栈上，因此在退出作用域之前必须与 `JL_GC_POP` 精确配对。也就是说，在函数返回之前，或者控制流以其他方式离开调用 `JL_GC_PUSH` 的块。

可以使用 `JL_GC_PUSH2` 到 `JL_GC_PUSH6` 宏一次性推送多个 Julia 值：

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

要推送一个 Julia 值的数组，可以使用 `JL_GC_PUSHARGS` 宏，使用方法如下：

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

每个作用域必须只有一次对 `JL_GC_PUSH*` 的调用，并且应该只与一次 `JL_GC_POP` 调用配对。如果您想要根植的所有必要变量不能通过一次 `JL_GC_PUSH*` 调用来推送，或者如果要推送的变量超过 6 个并且使用参数数组不是一个选项，那么可以使用内部块：

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

请注意，在调用 `JL_GC_PUSH*` 之前，不必拥有有效的 `jl_value_t*` 值。将一些初始化为 `NULL` 的值传递给 `JL_GC_PUSH*` 然后再创建实际的 Julia 值是可以的。例如：

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

如果需要在函数（或块作用域）之间保持对变量的指针，则无法使用 `JL_GC_PUSH*`。在这种情况下，有必要在 Julia 全局作用域中创建并保持对变量的引用。实现这一点的一个简单方法是使用全局的 `IdDict` 来保存引用，从而避免被垃圾回收器回收。然而，这种方法仅适用于可变类型。

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

如果变量是不可变的，那么它需要被包装在一个等效的可变容器中，或者更好的是，在一个 `RefValue{Any}` 中，然后再推送到 `IdDict`。在这种方法中，容器必须通过 C 代码创建或填充，例如使用函数 `jl_new_struct`。如果容器是通过 `jl_call*` 创建的，那么您需要重新加载指针以在 C 代码中使用。

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

GC 可以通过使用 `delete!` 函数从 `refs` 中删除对变量的引用来允许释放变量，前提是没有在其他地方保留对该变量的任何引用：

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

作为非常简单情况的替代方案，可以创建一个类型为 `Vector{Any}` 的全局容器，并在必要时从中获取元素，或者甚至为每个指针创建一个全局变量，使用

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

垃圾收集器还假设它知道每个指向年轻代对象的老年代对象。每当更新指针打破该假设时，必须通过 `jl_gc_wb`（写屏障）函数向收集器发出信号，如下所示：

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

通常无法预测在运行时哪些值会变旧，因此必须在所有显式存储之后插入写屏障。一个显著的例外是，如果`parent`对象刚刚被分配，并且自那时以来没有运行垃圾收集。请注意，大多数`jl_...`函数有时会调用垃圾收集。

写屏障在直接更新指针数组的数据时也是必要的。通常更推荐调用 `jl_array_ptr_set`。但也可以进行直接更新。例如：

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

有一些函数可以控制垃圾回收。在正常使用情况下，这些通常是不必要的。

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

Julia 和 C 可以共享数组数据而无需复制。接下来的示例将展示这是如何实现的。

Julia 数组在 C 中由数据类型 `jl_array_t*` 表示。基本上，`jl_array_t` 是一个包含以下内容的结构：

  * 关于数据类型的信息
  * 指向数据块的指针
  * 数组大小的信息

为了简单起见，我们从一维数组开始。创建一个包含长度为10的Float64元素的数组可以这样完成：

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

或者，如果您已经分配了数组，您可以在其数据周围生成一个薄包装器：

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

最后一个参数是一个布尔值，指示 Julia 是否应该拥有数据的所有权。如果该参数非零，当数组不再被引用时，GC 将对数据指针调用 `free`。

为了访问 `x` 的数据，我们可以使用 `jl_array_data`：

```c
double *xData = jl_array_data(x, double);
```

现在我们可以填充数组：

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

现在让我们调用一个在 `x` 上执行就地操作的 Julia 函数：

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

通过打印数组，可以验证 `x` 的元素现在已被反转。

### Accessing Returned Arrays

如果一个 Julia 函数返回一个数组，`jl_eval_string` 和 `jl_call` 的返回值可以被转换为 `jl_array_t*`：

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

现在可以像以前一样使用 `jl_array_data` 访问 `y` 的内容。和往常一样，请确保在使用数组时保持对它的引用。

### Multidimensional Arrays

Julia的多维数组在内存中以列优先顺序存储。以下是一些创建二维数组并访问其属性的代码：

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

请注意，虽然 Julia 数组使用 1 基索引，但 C API 使用 0 基索引（例如在调用 `jl_array_dim` 时），以便读取时显得更符合习惯的 C 代码。

## Exceptions

Julia 代码可以抛出异常。例如，考虑：

```c
jl_eval_string("this_function_does_not_exist()");
```

此调用看起来没有任何作用。然而，可以检查是否抛出了异常：

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

如果您正在从支持异常的语言（例如 Python、C#、C++）使用 Julia C API，那么将每个对 `libjulia` 的调用包装在一个检查是否抛出异常的函数中是有意义的，然后在主机语言中重新抛出异常。

### Throwing Julia Exceptions

在编写可调用的 Julia 函数时，可能需要验证参数并抛出异常以指示错误。典型的类型检查如下：

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

一般异常可以使用以下函数引发：

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error` 接受一个 C 字符串，而 `jl_errorf` 的调用方式类似于 `printf`：

```c
jl_errorf("argument x = %d is too large", x);
```

在这个例子中，`x` 被假设为一个整数。

### Thread-safety

一般来说，Julia C API 并不是完全线程安全的。在将 Julia 嵌入多线程应用程序时，需要注意不要违反以下限制：

  * `jl_init()` 在应用程序的生命周期中只能被调用一次。`jl_atexit_hook()` 也是如此，它只能在 `jl_init()` 之后被调用。
  * `jl_...()` API 函数只能从调用 `jl_init()` 的线程中调用，*或从由 Julia 运行时启动的线程中调用*。从用户启动的线程调用 Julia API 函数是不支持的，可能会导致未定义行为和崩溃。

上述第二个条件意味着您不能安全地从未由 Julia 启动的线程中调用 `jl_...()` 函数（调用 `jl_init()` 的线程是例外）。例如，以下情况不受支持，并且很可能会导致段错误：

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

相反，从同一个用户创建的线程中执行所有 Julia 调用将会有效：

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

从Julia自身启动的线程调用Julia C API的示例：

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

如果我们使用 2 个 Julia 线程运行这段代码，我们将得到以下输出（注意：输出会因运行和系统而异）：

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

如可以看到，Julia 线程 1 对应于 pthread ID 3bfd9c00，Julia 线程 2 对应于 ID 23938640，这表明确实在 C 级别使用了多个线程，并且我们可以安全地从这些线程调用 Julia C API 例程。

# Static analyzer annotations for GC correctness in C code

## Running the analysis

分析器插件随 Julia 一起提供。其源代码可以在 `src/clangsa` 中找到。运行它需要构建 clang 依赖项。请在您的 Make.user 中设置 `BUILD_LLVM_CLANG` 变量，以构建适当版本的 clang。您可能还想使用 `USE_BINARYBUILDER_LLVM` 选项来使用预构建的二进制文件。

或者（或者如果这些不够），请尝试

```sh
make -C src install-analysis-deps
```

从Julia的顶层目录。

之后，在源代码树上运行分析就像运行 `make -C src analyzegc` 一样简单。

## General Overview

由于Julia的垃圾回收（GC）是精确的，它需要维护任何可能在GC发生时被引用的值的正确根信息。这些地方被称为`safepoints`，在函数的局部上下文中，我们将这一称谓扩展到任何可能递归最终到达safepoint的函数调用。

在生成的代码中，这由 GC 根放置阶段自动处理（请参阅 LLVM 代码生成开发文档中的 GC 根章节）。然而，在 C 代码中，我们需要手动通知运行时任何 GC 根。这是通过以下宏完成的：

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

如果这些宏没有在需要的地方使用，或者使用不当，结果将是静默的内存损坏。因此，确保它们在所有适用的代码中正确放置是非常重要的。

因此，我们使用静态分析（特别是 clang 静态分析器）来帮助确保这些宏的正确使用。本文档的其余部分概述了这种静态分析，并描述了在 julia 代码库中使其正常工作的支持。

## GC Invariants

有两个简单的不变性正确性：

  * 所有 `GC_PUSH` 调用后需要跟随一个适当的 `GC_POP`（在实践中，我们在函数级别强制执行这一点）
  * 如果一个值之前没有在任何安全点上被根植，那么之后可能不再被引用。

当然，细节决定成败。特别是为了满足上述条件中的第二个，我们需要知道：

  * 哪些调用是安全点，哪些不是
  * 哪些值在任何给定的安全点上是根植的，哪些不是
  * 何时引用一个值

对于第二点，我们需要知道在运行时哪些内存位置将被视为根（即分配给这些位置的值是根）。这包括通过将它们传递给其中一个 `GC_PUSH` 宏显式指定的地点、全局根位置和值，以及从这些位置递归可达的任何位置。

## Static Analysis Algorithm

这个想法本身非常简单，尽管实现起来要复杂得多（主要是由于大量的特殊情况和 C 及 C++ 的复杂性）。本质上，我们跟踪所有根位置、所有可根化的值，以及任何表达式（赋值、分配等）对任何可根化值的根状态的影响。然后，在任何安全点，我们执行一次“符号 GC”，并毒化在该位置未被根化的任何值。如果这些值后来被引用，我们会发出错误。

Clang 静态分析器通过构建状态图并探索该图以寻找错误源来工作。该图中的几个节点是由分析器本身生成的（例如，用于控制流），但上述定义通过我们自己的状态增强了该图。

静态分析器是跨过程的，可以分析跨越函数边界的控制流。然而，静态分析器并不是完全递归的，并且对要探索的调用做出启发式决策（此外，一些调用是跨翻译单元的，对分析器不可见）。在我们的案例中，我们对正确性的定义要求完全的信息。因此，我们需要用分析所需的任何信息注释所有函数调用的原型，即使这些信息在跨过程静态分析中本可以获得。

幸运的是，我们仍然可以使用这种跨过程分析来确保我们在给定函数上放置的注释确实是正确的，考虑到该函数的实现。

## The analyzer annotations

这些注释位于 src/support/analyzer_annotations.h 中。它们仅在使用分析器时有效，并且要么扩展为无（用于原型注释），要么扩展为无操作（用于函数类似的注释）。

### `JL_NOTSAFEPOINT`

这可能是最常见的注释，应该放在任何已知不会导致达到 GC 安全点的函数上。一般来说，这样的函数只安全地执行算术运算、内存访问和调用被注释为 `JL_NOTSAFEPOINT` 的函数或其他已知不是安全点的函数（例如 C 标准库中的函数，这些函数在分析器中被硬编码为这样的）。

在对任何带有此属性的函数的调用中，保持值未根植是有效的：

用法示例：

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

当 `JL_MAYBE_UNROOTED` 被注解为函数的一个参数时，表示该参数可以被传递，即使它没有被根植。在正常情况下，Julia ABI 保证调用者在将值传递给被调用者之前会根植这些值。然而，一些函数并不遵循这个 ABI，允许未根植的值被传递给它们。请注意，这并不自动意味着该参数会被保留。`ROOTS_TEMPORARILY` 注解提供了更强的保证，不仅在传递时值可能未根植，而且在被调用者的任何内部安全点之间也会被保留。

注意，`JL_NOTSAFEPOINT` 本质上意味着 `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`，因为如果函数不包含安全点，则参数的根状态是无关紧要的。

另一个需要注意的点是，这些注释适用于调用者和被调用者两侧。在调用者一侧，它们解除通常要求的与根相关的限制，这些限制适用于 Julia ABI 函数。在被调用者一侧，它们则起到相反的作用，防止这些参数被视为隐式根。

如果将这两个注释中的任何一个应用于整个函数，则它适用于函数的所有参数。通常情况下，这仅在 varargs 函数中是必要的。

使用示例：

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

此注释通常出现在返回存储在另一个对象中的一个可根对象的访问器函数上。当注释在函数参数上时，它告诉分析器该参数的根也适用于函数返回的值。

用法示例：

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

这本质上是 `JL_PROPAGATES_ROOT` 的赋值对应。当将一个值赋给另一个已经被根植的值的字段时，赋值将继承被赋值对象的根。

用法示例：

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

此注释意味着此函数仅在禁用 GC 运行时的情况下被调用。这类函数通常在启动期间和 GC 代码本身中遇到。请注意，此注释会与运行时启用/禁用调用进行检查，因此 clang 会知道您是否撒谎。如果 GC 实际上并未禁用，这并不是禁用给定函数处理的好方法（如果必须，可以使用 `ifdef __clang_analyzer__`）。

使用示例：

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

此注解要求调用者传入一个根槽（即分配给此槽的值将被根化）。

用法示例：

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

此注释意味着给定的值始终是全局根植的。它可以应用于全局变量声明，在这种情况下，它将适用于这些变量的值（如果声明是针对数组，则适用于值），或者应用于函数，在这种情况下，它将适用于此类函数的返回值（例如，对于始终返回某些私有、全局根植值的函数）。

用法示例：

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

此注释本质上等同于 `JL_GLOBALLY_ROOTED`，但仅在这些值因作为叶类型而被全局根植时使用。叶类型的根植有点复杂。它们通常通过相应 `TypeName` 的 `cache` 字段根植，而该字段本身由包含模块根植（因此只要包含模块正常，它们就被根植），我们通常可以假设叶类型在使用的地方是根植的，但我们可能会在未来细化这一属性，因此单独的注释有助于分离出全局根植的原因。

分析器还会自动检测叶类型的检查，并且不会对这些路径上缺少 GC 根进行抱怨。

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

这是一个类似函数的注释。传递给此注释的任何值将在当前函数的作用域内被视为根。它被设计为分析器不足或复杂情况的逃生阀。然而，应该谨慎使用，优先考虑改善分析器本身。

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

分析器仅关注本地信息。特别是，例如在上述 `PROPAGATES_ROOT` 的情况下，它假设这样的内存仅以它可以看到的方式被修改，而不是在任何被调用的函数中（除非它恰好决定在其分析中考虑这些函数），也不是在任何并发运行的线程中。因此，它可能会错过一些问题案例，尽管在实践中这种并发修改相对较少。改进分析器以处理更多此类案例可能是未来工作的一个有趣主题。

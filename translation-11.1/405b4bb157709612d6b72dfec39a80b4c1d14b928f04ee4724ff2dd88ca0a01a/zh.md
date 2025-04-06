# Julia ASTs

Julia 有两种代码表示形式。首先是由解析器返回的表面语法 AST（例如 [`Meta.parse`](@ref) 函数），并由宏进行操作。它是代码书写时的结构化表示，由 `julia-parser.scm` 从字符流构建。接下来是降低形式，或 IR（中间表示），用于类型推断和代码生成。在降低形式中，节点的类型更少，所有宏都被展开，所有控制流都转换为显式分支和语句序列。降低形式由 `julia-syntax.scm` 构建。

首先我们将重点关注 AST，因为它是编写宏所必需的。

## Surface syntax AST

前端 AST 几乎完全由 [`Expr`](@ref) 和原子（例如符号、数字）组成。通常，每种视觉上不同的语法形式都有一个不同的表达式头。将以 s 表达式语法给出示例。每个带括号的列表对应一个 Expr，其中第一个元素是头。例如，`(call f x)` 对应于 Julia 中的 `Expr(:call, :f, :x)`。

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` 语法：

```julia
f(x) do a,b
    body
end
```

解析为 `(do (call f x) (-> (tuple a b) (block body)))`。

### Operators

大多数运算符的使用只是函数调用，因此它们被解析为头部 `call`。然而，一些运算符是特殊形式（不一定是函数调用），在这些情况下，运算符本身就是表达式的头部。在 julia-parser.scm 中，这些被称为“语法运算符”。一些运算符（`+` 和 `*`）使用 N-元解析；链式调用被解析为单个 N-参数调用。最后，比较链有其自己的特殊表达式结构。

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

文档字符串语法：

```julia
"some docs"
f(x) = x
```

解析为 `(macrocall (|.| Core '@doc) (line) "一些文档" (= (call f x) (block x)))`。

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using` 的表示与 `import` 相同，但表达式头为 `:using` 而不是 `:import`。

### Numbers

Julia 支持比许多 Scheme 实现更多的数字类型，因此并非所有数字都直接作为 AST 中的 Scheme 数字表示。

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

一个语句块被解析为 `(block stmt1 stmt2 ...)`。

如果语句：

```julia
if a
    b
elseif c
    d
else
    e
end
```

解析为：

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

一个 `while` 循环解析为 `(while condition body)`。

一个 `for` 循环解析为 `(for (= var iter) body)`。如果有多个迭代规范，它们被解析为一个块：`(for (block (= v1 iter1) (= v2 iter2)) body)`。

`break` 和 `continue` 被解析为 0 个参数的表达式 `(break)` 和 `(continue)`。

`let` 被解析为 `(let (= var val) body)` 或 `(let (block (= var1 val1) (= var2 val2) ...) body)`，类似于 `for` 循环。

一个基本的函数定义被解析为 `(function (call f x) body)`。一个更复杂的例子：

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

解析为：

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

类型定义：

```julia
mutable struct Foo{T<:S}
    x::T
end
```

解析为：

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

第一个参数是一个布尔值，指示类型是否可变。

`try` 块解析为 `(try try_block var catch_block finally_block)`。如果在 `catch` 后没有变量，则 `var` 为 `#f`。如果没有 `finally` 子句，则最后一个参数不存在。

### Quote expressions

Julia 源代码语法形式用于代码引用（`quote` 和 `:( )`）支持使用 `$` 进行插值。在 Lisp 术语中，这意味着它们实际上是“反引号”或“准引号”形式。在内部，也需要没有插值的代码引用。在 Julia 的方案代码中，不插值的引用用表达式头 `inert` 表示。

`inert` 表达式被转换为 Julia 的 `QuoteNode` 对象。这些对象包装了任何类型的单个值，并在评估时简单地返回该值。

一个 `quote` 表达式，其参数是一个原子，也会被转换为 `QuoteNode`。

### Line numbers

源位置信息表示为 `(line line_num file_name)`，其中第三个组件是可选的（当当前行号变化但文件名不变时省略）。

这些表达式在 Julia 中表示为 `LineNumberNode`。

### Macros

宏卫生通过表达式头对 `escape` 和 `hygienic-scope` 来表示。宏扩展的结果会自动包裹在 `(hygienic-scope block module)` 中，以表示新作用域的结果。用户可以在内部插入 `(escape block)` 来插入调用者的代码。

## Lowered form

降低形式（IR）对编译器更为重要，因为它用于类型推断、内联等优化以及代码生成。对于人类来说，它也不那么明显，因为它是输入语法经过重大重组的结果。

除了 `Symbol` 和一些数字类型，以下数据类型以降低形式存在：

  * `表达式`

    具有由 `head` 字段指示的节点类型，以及一个 `args` 字段，该字段是一个 `Vector{Any}` 的子表达式。虽然几乎表面 AST 的每个部分都由 `Expr` 表示，但 IR 仅使用有限数量的 `Expr`，主要用于调用和一些仅限于顶层的形式。
  * `插槽编号`

    通过连续编号识别参数和局部变量。它具有一个整数值的 `id` 字段，给出插槽索引。这些插槽的类型可以在其 `CodeInfo` 对象的 `slottypes` 字段中找到。
  * `论点`

    与 `SlotNumber` 相同，但仅在优化后出现。表示引用的插槽是封闭函数的一个参数。
  * `代码信息`

    将一组语句的 IR 包装起来。它的 `code` 字段是一个要执行的表达式数组。
  * `GotoNode`

    无条件跳转。参数是跳转目标，表示为代码数组中的索引。
  * `GotoIfNot`

    条件分支。如果 `cond` 字段的值为假，则跳转到 `dest` 字段所标识的索引。
  * `返回节点`

    将其参数（`val` 字段）作为封闭函数的值返回。如果 `val` 字段未定义，则这表示一个不可达语句。
  * `引用节点`

    将任意值包装为引用数据。例如，函数 `f() = :a` 包含一个 `QuoteNode`，其 `value` 字段是符号 `a`，以便返回符号本身而不是对其进行求值。
  * `全球引用`

    引用模块 `mod` 中的全局变量 `name`。
  * `SSA值`

    指由编译器插入的连续编号（从1开始）的静态单赋值（SSA）变量。`SSAValue`的编号（`id`）是表示其值的表达式的代码数组索引。
  * `新变量节点`

    标记一个变量（插槽）被创建的点。这会导致变量重置为未定义。

### `Expr` types

这些符号出现在 `head` 字段的 [`Expr`](@ref) 中的小写形式。

  * `呼叫`

    函数调用（动态调度）。 `args[1]` 是要调用的函数，`args[2:end]` 是参数。
  * `调用`

    函数调用（静态调度）。 `args[1]` 是要调用的 MethodInstance，`args[2:end]` 是参数（包括正在被调用的函数，在 `args[2]`）。
  * `静态参数`

    通过索引引用静态参数。
  * `=`

    作业。在 IR 中，第一个参数始终是 `SlotNumber` 或 `GlobalRef`。
  * `方法`

    添加一个方法到泛型函数，并在必要时分配结果。

    具有1个参数形式和3个参数形式。1个参数形式源自语法`function foo end`。在1个参数形式中，参数是一个符号。如果这个符号已经在当前作用域中命名了一个函数，则不会发生任何事情。如果符号未定义，则会创建一个新函数并将其分配给符号指定的标识符。如果符号已定义但命名的是一个非函数，则会引发错误。“命名一个函数”的定义是绑定是常量，并且指向一个单例类型的对象。这样做的理由是，单例类型的实例唯一标识要添加方法的类型。当类型具有字段时，添加的方法是添加到实例还是其类型就不清楚了。

    3个参数形式具有以下参数：

      * `args[1]`

        一个函数名称，或者如果未知或不需要则为`nothing`。如果是一个符号，则表达式首先像上面的1个参数形式那样行为。从那时起，这个参数将被忽略。当方法严格按类型添加时，它可以是`nothing`，`(::T)(x) = x`，或者当一个方法被添加到一个现有函数时，`MyModule.f(x) = x`。
      * `args[2]`

        一个 `SimpleVector` 的参数类型数据。`args[2][1]` 是一个参数类型的 `SimpleVector`，而 `args[2][2]` 是一个与方法的静态参数对应的类型变量的 `SimpleVector`。
      * `args[3]`

        一个方法本身的 `CodeInfo`。对于“超出范围”的方法定义（向一个函数添加一个在不同范围内定义的方法），这是一个求值为 `:lambda` 表达式的表达式。
  * `结构类型`

    一个定义新 `struct` 的 7 个参数表达式：

      * `args[1]`

        `struct` 的名称
      * `args[2]`

        一个 `call` 表达式，用于创建一个 `SimpleVector` 并指定其参数
      * `args[3]`

        一个 `call` 表达式，用于创建一个 `SimpleVector` 并指定其字段名称
      * `args[4]`

        一个 `Symbol`、`GlobalRef` 或 `Expr`，指定超类型（例如，`:Integer`、`GlobalRef(Core, :Any)` 或 `:(Core.apply_type(AbstractArray, T, N))`）
      * `args[5]`

        一个 `call` 表达式，用于创建一个 `SimpleVector` 并指定其字段类型
      * `args[6]`

        一个布尔值，如果`mutable`则为真
      * `args[7]`

        初始化的参数数量。这将是字段的数量，或由内部构造函数的 `new` 语句调用的最小字段数量。
  * `抽象类型`

    一个定义新抽象类型的三参数表达式。参数与 `struct_type` 表达式的参数 1、2 和 4 相同。
  * `原始类型`

    一个定义新原始类型的4个参数表达式。参数1、2和4与`struct_type`相同。参数3是位数。

    !!! compat "Julia 1.5"
        `struct_type`、`abstract_type` 和 `primitive_type` 在 Julia 1.5 中被移除，并被新的内置函数替代。
  * `全球`

    声明一个全局绑定。
  * `常量`

    声明一个（全局）变量为常量。
  * `新`

    分配一个新的类似结构的对象。第一个参数是类型。[`new`](@ref) 伪函数被简化为此，类型始终由编译器插入。这确实是一个内部专用特性，并且不进行任何检查。评估任意的 `new` 表达式可能会导致段错误。
  * `splatnew`

    类似于 `new`，但字段值作为一个单一的元组传递。其工作方式类似于 `splat(new)`，如果 `new` 是一个一等函数的话，因此得名。
  * `已定义`

    `Expr(:isdefined, :x)` 返回一个布尔值，指示 `x` 是否已经在当前作用域中定义。
  * `the_exception`

    在 `catch` 块中返回捕获的异常，由 `jl_current_exception(ct)` 返回。
  * `输入`

    进入异常处理程序（`setjmp`）。`args[1]` 是在出错时跳转到的捕获块的标签。产生一个由 `pop_exception` 消耗的令牌。
  * `离开`

    弹出异常处理程序。`args[1]` 是要弹出的处理程序数量。
  * `pop_exception`

    在离开捕获块时，将当前异常的堆栈弹出到与关联的 `enter` 相同的状态。 `args[1]` 包含来自关联 `enter` 的令牌。

    !!! compat "Julia 1.1"
        `pop_exception` 是 Julia 1.1 中的新功能。
  * `入站`

    控制开启或关闭边界检查。维护一个栈；如果该表达式的第一个参数为真或假（`true`表示禁用边界检查），则将其推入栈中。如果第一个参数为`:pop`，则弹出栈。
  * `边界检查`

    如果内联到标记为 `@inbounds` 的代码段中，则值为 `false`，否则值为 `true`。
  * `循环信息`

    标记循环的结束。包含传递给 `LowerSimdLoop` 的元数据，用于标记 `@simd` 表达式的内部循环，或将信息传播给 LLVM 循环传递。
  * `copyast`

    部分的准引用实现。参数是一个表面语法 AST，它被递归复制并在运行时返回。
  * `元`

    元数据。 `args[1]` 通常是一个符号，用于指定元数据的类型，其余参数为自由格式。以下是常用的几种元数据类型：

      * `:inline` 和 `:noinline`：内联提示。
  * `foreigncall`

    静态计算的 `ccall` 信息容器。字段包括：

      * `args[1]` : 名称

        将被解析的外部函数的表达式。
      * `args[2]::Type` : RT

        返回类型（字面意思），在定义包含方法时静态计算。
      * `args[3]::SimpleVector`（类型）：AT

        包含方法定义时静态计算的参数类型的（字面）向量。
      * `args[4]::Int` : nreq

        可变参数函数定义所需的参数数量。
      * `args[5]::QuoteNode{Symbol}` : 调用约定

        调用约定。
      * `args[6:5+length(args[3])]` : 参数

        所有参数的值（每个参数的类型在 args[3] 中给出）。
      * `args[6+length(args[3])+1:end]` : gc-roots

        在调用期间可能需要被 gc-rooted 的附加对象。请参见 [Working with LLVM](@ref Working-with-LLVM) 以了解这些对象的来源及其处理方式。
  * `new_opaque_closure`

    构造一个新的不透明闭包。字段包括：

      * `args[1]` : 签名

        不透明闭包的函数签名。不透明闭包不参与调度，但输入类型可以被限制。
      * `args[2]` : isva

        指示闭包是否接受可变参数。
      * `args[3]` : lb

        输出类型的下界。（默认为 `Union{}`）
      * `args[4]` : ub

        输出类型的上限。（默认为 `Any`）
      * `args[5]` : 方法

        实际方法作为 `opaque_closure_method` 表达式。
      * `args[6:end]` : 捕获

        不透明闭包捕获的值。

    !!! compat "Julia 1.7"
        不透明闭包是在 Julia 1.7 中添加的

### [Method](@id ast-lowered-method)

一个独特的容器，描述单个方法的共享元数据。

  * `名称`, `模块`, `文件`, `行`, `签名`

    元数据用于唯一识别计算机和人类的方法。
  * `模糊`

    与此方法可能存在歧义的其他方法的缓存。
  * `专业化`

    此方法创建的所有 MethodInstance 的缓存，用于确保唯一性。唯一性对于效率至关重要，特别是在增量预编译和方法失效跟踪时。
  * `源`

    原始源代码（如果可用，通常是压缩的）。
  * `生成器`

    一个可调用对象，可以执行以获取特定方法签名的专用源代码。
  * `根`

    指向非AST事物的指针，这些事物已被插入到AST中，这是AST压缩、类型推断或本机代码生成所必需的。
  * `nargs`，`isva`，`called`，`is_for_opaque_closure`，

    描述此方法源代码的位域。
  * `主要世界`

    拥有这种方法的世界时代。

### MethodInstance

一个独特的容器，描述了一个方法的单一可调用签名。特别请参阅 [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks) 以获取有关如何安全修改这些字段的重要细节。

  * `specTypes`

    此 MethodInstance 的主键。通过 `def.specializations` 查找保证唯一性。
  * `def`

    该函数描述的 `Method` 的特化。或者是一个 `Module`，如果这是在模块中展开的顶级 Lambda，并且不属于任何方法。
  * `sparam_vals`

    `specTypes` 中静态参数的值。对于 `Method.unspecialized` 的 `MethodInstance`，这是空的 `SimpleVector`。但是对于来自 `MethodTable` 缓存的运行时 `MethodInstance`，这将始终被定义并且可索引。
  * `未推断`

    未压缩的顶层 thunk 源代码。此外，对于生成的函数，这是可能找到源代码的众多地方之一。
  * `反向边`

    我们存储缓存依赖项的反向列表，以便有效跟踪在新方法定义后可能需要的增量重新分析/重新编译工作。这是通过保持其他 `MethodInstance` 的列表来实现的，这些 `MethodInstance` 已被推断或优化为可能调用此 `MethodInstance`。这些优化结果可能存储在 `cache` 的某个地方，或者可能是我们不想缓存的某些结果，例如常量传播。因此，我们在这里将所有这些反向边合并到各种缓存条目中（无论如何，几乎总是只有一个适用的缓存条目，具有最大世界的哨兵值）。
  * `缓存`

    共享此模板实例化的 `CodeInstance` 对象的缓存。

### CodeInstance

  * `def`

    该缓存条目派生自的 `MethodInstance`。
  * `所有者`

    一个表示此 `CodeInstance` 拥有者的令牌。将使用 `jl_egal` 进行匹配。

  * `rettype`/`rettype_const`

    `specFunctionObject` 字段的推断返回类型，通常也是该函数的一般计算返回类型。
  * `推断`

    可能包含此函数推断源的缓存，或者可以设置为 `nothing` 以仅指示 `rettype` 是推断的。
  * `ftpr`

    通用的 jlcall 入口点。
  * `jlcall_api`

    调用 `fptr` 时使用的 ABI。一些重要的包括：

      * 0 - 尚未编译
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - 常量（存储在 `rettype_const` 中的值）
      * 3 - 使用静态参数转发 `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - 在解释器中运行 `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_world` / `max_world`

    此方法实例有效调用的世界年龄范围。如果 max_world 是特殊标记值 `-1`，则该值尚不清楚。在我们遇到需要重新考虑的回边之前，它可能会继续被使用。

### CodeInfo

一个（通常是临时的）用于保存降级源代码的容器。

  * `代码`

    一个 `Any` 语句数组
  * `插槽名称`

    一个符号数组，为每个槽（参数或局部变量）提供名称。
  * `slotflags`

    一个 `UInt8` 数组的槽属性，表示为位标志：

      * 0x02 - 已分配（仅在此变量左侧没有*任何*赋值语句时为假）
      * 0x08 - 已使用（如果有对插槽的读取或写入）
      * 0x10 - 静态分配一次
      * 0x20 - 可能在赋值之前使用。此标志仅在类型推断后有效。
  * `ssavaluetypes`

    要么是一个数组，要么是一个 `Int`。

    如果是 `Int`，则给出函数中编译器插入的临时位置的数量（`code` 数组的长度）。如果是数组，则为每个位置指定一个类型。
  * `ssaflags`

    每个表达式的语句级 32 位标志。在 julia.h 中查看 `jl_code_info_t` 的定义以获取更多详细信息。
  * `linetable`

    一个源位置对象的数组
  * `codelocs`

    一个整数索引数组，指向 `linetable`，给出与每个语句相关联的位置。

可选字段：

  * `槽类型`

    一个用于插槽的类型数组。
  * `rettype`

    推断的返回类型为降低形式（IR）。默认值为 `Any`。
  * `推理限制启发式方法`

    `method_for_inference_heuristics` 将在推理过程中根据需要扩展给定方法的生成器。
  * `父母`

    拥有此对象的 `MethodInstance`（如果适用）。
  * `边缘`

    将边缘转发到必须失效的方法实例。
  * `min_world`/`max_world`

    该代码在推断时有效的世界年龄范围。

布尔属性：

  * `推断`

    这是否是通过类型推断生成的。
  * `内联的`

    是否应该符合内联的条件。
  * `传播内部`

    是否在内联时应传播 `@inbounds` 以省略 `@boundscheck` 块。

`UInt8` 设置：

  * `constprop`

      * 0 = 使用启发式方法
      * 1 = 侵略性
      * 2 = 无
  * `purity` 由 5 个位标志构成：

      * 0x01 << 0 = 此方法保证一致地返回或终止 (`:consistent`)
      * 0x01 << 1 = 该方法没有外部语义可见的副作用 (`:effect_free`)
      * 0x01 << 2 = 此方法保证不会抛出异常 (`:nothrow`)
      * 0x01 << 3 = 此方法保证终止 (`:terminates_globally`)
      * 0x01 << 4 = 此方法中的语法控制流保证会终止 (`:terminates_locally`)

    请参阅 `Base.@assume_effects` 的文档以获取更多详细信息。

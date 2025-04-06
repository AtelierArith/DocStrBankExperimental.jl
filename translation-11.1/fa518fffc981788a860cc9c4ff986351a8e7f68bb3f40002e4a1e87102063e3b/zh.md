# [Modules](@id modules)

在Julia中，模块帮助将代码组织成一致的单元。它们在语法上用 `module NameOfModule ... end` 限定，并具有以下特性：

1. 模块是独立的命名空间，每个模块引入一个新的全局作用域。这是有用的，因为它允许在不同的函数或全局变量之间使用相同的名称而不会发生冲突，只要它们位于不同的模块中。
2. 模块具有详细的命名空间管理功能：每个模块定义了一组它 `export` 的名称并标记为 `public`，并可以使用 `using` 和 `import` 从其他模块导入名称（我们将在下面解释这些）。
3. 模块可以预编译以加快加载速度，并可能包含用于运行时初始化的代码。

通常，在较大的 Julia 包中，您会看到模块代码组织成文件，例如

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

文件和文件名与模块大多无关；模块仅与模块表达式相关。每个模块可以有多个文件，每个文件可以有多个模块。`include` 的行为就像源文件的内容在包含模块的全局作用域中被评估一样。在本章中，我们使用简短和简化的示例，因此我们不会使用 `include`。

推荐的风格是不缩进模块的主体，因为这通常会导致整个文件被缩进。此外，模块名称通常使用 `UpperCamelCase`（就像类型一样），如果适用，尤其是当模块包含一个同名标识符时，使用复数形式，以避免名称冲突。例如，

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

命名空间管理是指语言提供的使模块中的名称在其他模块中可用的功能。我们将在下面详细讨论相关概念和功能。

### Qualified names

全局作用域中的函数、变量和类型的名称，如 `sin`、`ARGS` 和 `UnitRange`，始终属于一个模块，称为 *父模块*，可以通过 [`parentmodule`](@ref) 交互式地找到，例如

```jldoctest
julia> parentmodule(UnitRange)
Base
```

一个人也可以通过在其模块前加上模块名来在其父模块之外引用这些名称，例如 `Base.UnitRange`。这被称为 *合格名称*。父模块可以通过一系列子模块访问，例如 `Base.Math.sin`，其中 `Base.Math` 被称为 *模块路径*。由于语法歧义，限定仅包含符号的名称（例如运算符）时，需要插入一个冒号，例如 `Base.:+`。少数运算符还需要括号，例如 `Base.:(==)`。

如果一个名称是合格的，那么它总是*可访问*的，并且在函数的情况下，可以通过将合格名称用作函数名称来添加方法。

在一个模块内，可以通过将其声明为 `global x` 来“保留”一个变量名，而不必为其赋值。这可以防止在加载后初始化的全局变量之间发生名称冲突。语法 `M.x = y` 不适用于在另一个模块中赋值全局变量；全局赋值始终是模块局部的。

### Export lists

名称（指函数、类型、全局变量和常量）可以通过 `export` 添加到模块的 *导出列表* 中：这些是当 `using` 模块时被导入的符号。通常，它们位于模块定义的顶部或附近，以便源代码的读者可以轻松找到它们，如下所示：

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

但这只是一个样式建议——一个模块可以在任意位置有多个 `export` 语句。

在导出作为 API（应用程序编程接口）一部分的名称时，这是很常见的。在上面的代码中，导出列表建议用户使用 `nice` 和 `DOG`。然而，由于合格名称始终使标识符可访问，这只是组织 API 的一种选择：与其他语言不同，Julia 没有真正隐藏模块内部的功能。

此外，一些模块根本不导出名称。这通常是因为它们在其 API 中使用了常见词汇，例如 `derivative`，这可能会与其他模块的导出列表发生冲突。我们将在下面看到如何处理名称冲突。

要将名称标记为公共而不将其导出到调用 `using NiceStuff` 的人的命名空间中，可以使用 `public` 而不是 `export`。这将公共名称标记为公共 API 的一部分，但没有任何命名空间的影响。`public` 关键字仅在 Julia 1.11 及以上版本中可用。为了与 Julia 1.10 及以下版本保持兼容，请使用 [Compat](https://github.com/JuliaLang/Compat.jl) 包中的 `@compat` 宏。

### Standalone `using` and `import`

对于交互式使用，加载模块的最常见方法是 `using ModuleName`。这 [loads](@ref code-loading) 与 `ModuleName` 相关的代码，并引入

1. 模块名称
2. 并将导出列表的元素放入周围的全局命名空间。

从技术上讲，语句 `using ModuleName` 意味着一个名为 `ModuleName` 的模块将可用于根据需要解析名称。当遇到一个在当前模块中没有定义的全局变量时，系统将会在 `ModuleName` 导出的变量中搜索它，并在找到时使用它。这意味着在当前模块中对该全局变量的所有使用都将解析为 `ModuleName` 中该变量的定义。

要从包中加载模块，可以使用语句 `using ModuleName`。要从本地定义的模块加载模块，需要在模块名称前添加一个点，如 `using .ModuleName`。

为了继续我们的例子，

```jldoctest module_manual
julia> using .NiceStuff
```

将上述代码加载后，将使 `NiceStuff`（模块名称）、`DOG` 和 `nice` 可用。`Dog` 不在导出列表中，但如果使用模块路径（在这里仅为模块名称）进行限定，则可以访问它，形式为 `NiceStuff.Dog`。

重要的是，**`using ModuleName` 是唯一一个导出列表有意义的形式**。

相反，

```jldoctest module_manual
julia> import .NiceStuff
```

仅将模块名称引入作用域。用户需要使用 `NiceStuff.DOG`、`NiceStuff.Dog` 和 `NiceStuff.nice` 来访问其内容。通常，在用户希望保持命名空间干净的情况下使用 `import ModuleName`。正如我们将在下一节中看到的，`import .NiceStuff` 等同于 `using .NiceStuff: NiceStuff`。

您可以将多个相同类型的 `using` 和 `import` 语句组合在一个以逗号分隔的表达式中，例如

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

当 `using ModuleName:` 或 `import ModuleName:` 后面跟着一个以逗号分隔的名称列表时，模块会被加载，但 *只有那些特定的名称会被引入到命名空间* 中。例如，

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

将导入名称 `nice` 和 `DOG`。

重要的是，模块名称 `NiceStuff` 将 *不* 在命名空间中。如果您想使其可访问，您必须明确列出它，如下所示：

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

当两个或多个包/模块导出一个名称，并且该名称在每个包中并不指代相同的事物时，如果通过 `using` 加载这些包而没有明确的名称列表，则引用该名称而不进行限定是一个错误。因此，建议旨在与其依赖项和 Julia 的未来版本向前兼容的代码，例如发布包中的代码，列出它从每个加载的包中使用的名称，例如 `using Foo: Foo, f` 而不是 `using Foo`。

Julia 有两种形式看似相同，因为只有 `import ModuleName: f` 允许在 *没有模块路径* 的情况下向 `f` 添加方法。也就是说，以下示例将会报错：

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

此错误防止意外地将方法添加到您仅打算使用的其他模块中的函数。

有两种方法来处理这个问题。您可以始终使用模块路径来限定函数名称：

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

或者，您可以 `import` 特定的函数名称：

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

选择哪一个是风格的问题。第一种形式清楚地表明您正在向另一个模块中的函数添加一个方法（请记住，导入和方法定义可能在不同的文件中），而第二种形式更简洁，特别是在您定义多个方法时，这一点尤其方便。

一旦通过 `using` 或 `import` 使变量可见，模块就不能创建同名的变量。导入的变量是只读的；对全局变量的赋值总是影响当前模块拥有的变量，否则会引发错误。

### Renaming with `as`

通过 `import` 或 `using` 引入作用域的标识符可以使用关键字 `as` 进行重命名。这对于解决名称冲突以及缩短名称非常有用。例如，`Base` 导出了函数名 `read`，但 CSV.jl 包也提供了 `CSV.read`。如果我们要多次调用 CSV 读取，省略 `CSV.` 限定符会很方便。但那样就会模糊我们是指 `Base.read` 还是 `CSV.read`：

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

重命名提供了解决方案：

```julia-repl
julia> import CSV: read as rd
```

导入的包也可以重命名：

```julia
import BenchmarkTools as BT
```

`as` 仅在引入单个标识符到作用域时与 `using` 一起使用。例如，`using CSV: read as rd` 可以正常工作，但 `using CSV as C` 不可以，因为它作用于 `CSV` 中导出的所有名称。

### Mixing multiple `using` and `import` statements

当使用多个 `using` 或 `import` 语句时，它们的效果按出现的顺序组合。例如，

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

将所有导出的 `NiceStuff` 名称和模块名称本身引入作用域，并且还允许在不使用模块名称前缀的情况下向 `nice` 添加方法。

### Handling name conflicts

考虑两（或更多）个包导出相同名称的情况，如在

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

语句 `using .A, .B` 可以正常工作，但当你尝试调用 `f` 时，会出现错误提示。

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

在这里，Julia 无法决定你所指的 `f` 是哪个，因此你必须做出选择。以下解决方案是常用的：

1. 简单地使用合格的名称，如 `A.f` 和 `B.f`。这使得代码的上下文对读者来说更加清晰，特别是当 `f` 恰好重合但在不同包中具有不同含义时。例如，`degree` 在数学、自然科学和日常生活中有多种用法，这些含义应该保持分开。
2. 使用 `as` 关键字来重命名一个或两个标识符，例如

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    将 `B.f` 作为 `g` 可用。在这里，我们假设您之前没有使用 `using A`，否则会将 `f` 引入命名空间。
3. 当相关名称*确实*共享一个含义时，通常一个模块会从另一个模块导入它，或者有一个轻量级的“基础”包，其唯一功能是定义一个像这样的接口，可以被其他包使用。通常这样的包名以`...Base`结尾（这与Julia的`Base`模块无关）。

### Default top-level definitions and bare modules

模块自动包含 `using Core`、`using Base`，以及 [`eval`](@ref) 和 [`include`](@ref) 函数的定义，这些函数在该模块的全局作用域内评估表达式/文件。

如果不需要这些默认定义，可以使用关键字 [`baremodule`](@ref) 来定义模块（注意：`Core` 仍然被导入）。就 `baremodule` 而言，一个标准的 `module` 看起来是这样的：

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

如果连 `Core` 都不想要，可以定义一个不导入任何内容且不定义任何名称的模块，使用 `Module(:YourNameHere, false, false)`，并可以通过 [`@eval`](@ref) 或 [`Core.eval`](@ref) 将代码评估到其中：

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

有三个重要的标准模块：

  * [`Core`](@ref) 包含了语言中“内置”的所有功能。
  * [`Base`](@ref) 包含在几乎所有情况下都很有用的基本功能。
  * [`Main`](@ref) 是顶级模块，也是当 Julia 启动时的当前模块。

!!! note "Standard library modules"
    默认情况下，Julia 附带了一些标准库模块。这些模块的行为类似于常规的 Julia 包，但您不需要显式安装它们。例如，如果您想进行一些单元测试，可以按如下方式加载 `Test` 标准库：

    ```julia
    using Test
    ```


## Submodules and relative paths

模块可以包含 *子模块*，嵌套相同的语法 `module ... end`。它们可以用来引入独立的命名空间，这对于组织复杂的代码库是有帮助的。请注意，每个 `module` 都引入了自己的 [scope](@ref scope-of-variables)，因此子模块不会自动“继承”来自其父模块的名称。

建议子模块在 `using` 和 `import` 语句中使用 *相对模块限定符* 来引用封闭父模块（包括后者）中的其他模块。相对模块限定符以一个句点（`.`）开头，表示当前模块，每个后续的 `.` 指向当前模块的父模块。如果需要，后面可以跟模块，最终是要访问的实际名称，所有部分用 `.` 分隔。

考虑以下示例，其中子模块 `SubA` 定义了一个函数，然后在其“兄弟”模块中进行了扩展：

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

您可能会在包中看到代码，在类似的情况下，使用

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

然而，这通过 [code loading](@ref code-loading) 操作，因此仅在 `ParentModule` 在一个包中时有效。使用相对路径更好。

请注意，如果您正在评估值，定义的顺序也很重要。考虑

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

其中 `Sub` 尝试在 `TestPackage.y` 被定义之前使用它，因此它没有值。

出于类似的原因，您不能使用循环排序：

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

大型模块的加载可能需要几秒钟，因为执行模块中的所有语句通常涉及编译大量代码。Julia 创建模块的预编译缓存以减少此时间。

预编译模块文件（有时称为“缓存文件”）在 `import` 或 `using` 加载模块时会自动创建和使用。如果缓存文件尚不存在，模块将被编译并保存以供将来重用。您还可以手动调用 [`Base.compilecache(Base.identify_package("modulename"))`](@ref) 来创建这些文件，而无需加载模块。生成的缓存文件将存储在 `DEPOT_PATH[1]` 的 `compiled` 子文件夹中。如果您的系统没有任何变化，这些缓存文件将在您使用 `import` 或 `using` 加载模块时被使用。

预编译缓存文件存储模块、类型、方法和常量的定义。它们还可能存储方法特化及为其生成的代码，但这通常要求开发者添加显式的 [`precompile`](@ref) 指令或执行强制在包构建期间进行编译的工作负载。

然而，如果您更新模块的依赖项或更改其源代码，则在 `using` 或 `import` 时，模块会自动重新编译。依赖项是它导入的模块、Julia 构建、它包含的文件或在模块文件中由 [`include_dependency(path)`](@ref) 明确声明的依赖项。

对于通过 `include` 加载的文件依赖，变更是通过检查文件大小（`fsize`）或内容（压缩为哈希）是否未改变来确定的。对于通过 `include_dependency` 加载的文件依赖，变更是通过检查修改时间（`mtime`）是否未改变，或是否等于截断到最近一秒的修改时间（以适应无法以亚秒精度复制 mtime 的系统）来确定的。它还考虑了 `require` 中搜索逻辑选择的文件路径是否与创建预编译文件的路径匹配。它还考虑了已经加载到当前进程中的依赖集，并且不会重新编译这些模块，即使它们的文件发生变化或消失，以避免在运行系统和预编译缓存之间产生不兼容性。最后，它还考虑了任何 [compile-time preferences](@ref preferences) 的变化。

如果您知道某个模块*不*安全进行预编译（例如，出于以下描述的某些原因），您应该在模块文件中放置 `__precompile__(false)`（通常放在顶部）。这将导致 `Base.compilecache` 抛出错误，并使 `using` / `import` 直接将其加载到当前进程中，跳过预编译和缓存。这也因此防止该模块被任何其他预编译模块导入。

您可能需要了解在创建增量共享库时固有的某些行为，这可能在编写模块时需要谨慎。例如，外部状态不会被保留。为了解决这个问题，请明确将必须在*运行时*发生的任何初始化步骤与可以在*编译时*发生的步骤分开。为此，Julia 允许您在模块中定义一个 `__init__()` 函数，该函数执行必须在运行时发生的任何初始化步骤。此函数在编译期间（`--output-*`）不会被调用。实际上，您可以假设它将在代码的生命周期中运行一次。当然，如果有必要，您可以手动调用它，但默认情况下假设此函数处理的是本地机器的计算状态，这不需要被捕获在编译的映像中，甚至不应该被捕获。它将在模块加载到进程后被调用，包括如果它被加载到增量编译中（`--output-incremental=yes`），但如果它被加载到完整编译过程中，则不会被调用。

特别地，如果您在模块中定义了一个 `function __init__()`，那么 Julia 会在模块加载后立即调用 `__init__()`（例如，通过 `import`、`using` 或 `require`）第一次运行时（即，`__init__` 只会被调用一次，并且仅在模块中的所有语句执行完毕后）。因为它是在模块完全导入后调用的，所以任何子模块或其他导入的模块的 `__init__` 函数会在封闭模块的 `__init__` 之前被调用。

`__init__` 的两个典型用法是调用外部 C 库的运行时初始化函数和初始化涉及外部库返回的指针的全局常量。例如，假设我们正在调用一个 C 库 `libfoo`，该库要求我们在运行时调用 `foo_init()` 初始化函数。假设我们还想定义一个全局常量 `foo_data_ptr`，它保存由 `libfoo` 定义的 `void *foo_data()` 函数的返回值——这个常量必须在运行时初始化（而不是在编译时），因为指针地址会在每次运行时发生变化。您可以通过在模块中定义以下 `__init__` 函数来实现这一点：

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

注意，在像 `__init__` 这样的函数内部定义全局变量是完全可能的；这就是使用动态语言的一个优势。但是，通过在全局范围内将其定义为常量，我们可以确保类型对编译器是已知的，并允许它生成更优化的代码。显然，您模块中任何依赖于 `foo_data_ptr` 的其他全局变量也必须在 `__init__` 中初始化。

涉及大多数 Julia 对象的常量，如果不是由 [`ccall`](@ref) 生成的，则不需要放在 `__init__` 中：它们的定义可以被预编译并从缓存的模块映像中加载。这包括像数组这样的复杂堆分配对象。然而，任何返回原始指针值的例程必须在运行时调用，以使预编译工作正常（[`Ptr`](@ref) 对象将变成空指针，除非它们隐藏在 [`isbits`](@ref) 对象中）。这包括 Julia 函数 [`@cfunction`](@ref) 和 [`pointer`](@ref) 的返回值。

字典和集合类型，或者一般来说，任何依赖于 `hash(key)` 方法输出的内容，都是一个更棘手的情况。在常见的情况下，当键是数字、字符串、符号、范围、`Expr` 或这些类型的组合（通过数组、元组、集合、对等）时，它们是安全的可以预编译。然而，对于一些其他键类型，例如 `Function` 或 `DataType` 以及未定义 `hash` 方法的通用用户定义类型，后备的 `hash` 方法依赖于对象的内存地址（通过其 `objectid`），因此可能会在不同的运行中变化。如果你有这些键类型，或者不确定，为了安全起见，你可以在 `__init__` 函数中初始化这个字典。或者，你可以使用 [`IdDict`](@ref) 字典类型，它是通过预编译特别处理的，因此在编译时初始化是安全的。

在使用预编译时，保持对编译阶段和执行阶段之间区别的清晰认识是很重要的。在这种模式下，通常会更明显地表明，Julia 是一个编译器，它允许执行任意的 Julia 代码，而不是一个同时生成编译代码的独立解释器。

其他已知的潜在故障场景包括：

1. 全局计数器（例如，用于尝试唯一标识对象）。考虑以下代码片段：

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    虽然这段代码的意图是为每个实例提供一个唯一的 ID，但计数器的值是在编译结束时记录的。所有后续对这个增量编译模块的使用都将从相同的计数器值开始。

    请注意，`objectid`（通过对内存指针进行哈希来工作）存在类似的问题（请参见下面关于 `Dict` 使用的说明）。

    一种替代方案是使用宏来捕获 [`@__MODULE__`](@ref) 并将其与当前的 `counter` 值单独存储，然而，重新设计代码以不依赖于这个全局状态可能更好。
2. 关联集合（如 `Dict` 和 `Set`）需要在 `__init__` 中重新哈希。（将来可能会提供一种机制来注册初始化函数。）
3. 根据编译时副作用在加载时的持续性。示例包括：修改其他 Julia 模块中的数组或其他变量；保持对打开的文件或设备的句柄；存储指向其他系统资源（包括内存）的指针；
4. 创建意外的“副本”全局状态来自另一个模块，通过直接引用它而不是通过其查找路径。例如，（在全局作用域中）：

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

在预编译代码时，施加了几个额外的限制，以帮助用户避免其他错误行为的情况：

1. 调用 [`eval`](@ref) 以在另一个模块中引发副作用。当增量预编译标志设置时，这也会导致发出警告。
2. `global const` 语句在 `__init__()` 开始后从局部作用域中使用（请参见问题 #12010，了解添加此错误的计划）
3. 替换模块是在进行增量预编译时的运行时错误。

还有几点需要注意：

1. 在对源文件本身进行更改后（包括通过 `Pkg.update`），不会执行代码重载/缓存失效，并且在 `Pkg.rm` 之后不会进行清理。
2. 重塑数组的内存共享行为在预编译时被忽略（每个视图都有自己的副本）
3. 期望在编译时和运行时文件系统保持不变，例如 [`@__FILE__`](@ref)/`source_path()` 在运行时查找资源，或 BinDeps 的 `@checked_lib` 宏。有时这是不可避免的。然而，在可能的情况下，将资源在编译时复制到模块中是一个好习惯，这样在运行时就不需要查找它们。
4. `WeakRef` 对象和终结器目前未被序列化器正确处理（这将在即将发布的版本中修复）。
5. 通常最好避免捕获对内部元数据对象实例的引用，例如 `Method`、`MethodInstance`、`MethodTable`、`TypeMapLevel`、`TypeMapEntry` 及这些对象的字段，因为这可能会使序列化器感到困惑，并可能不会导致您期望的结果。这样做不一定是错误的，但您需要做好准备，系统会尝试复制其中一些，并创建其他对象的唯一实例。

在模块开发过程中，有时关闭增量预编译是有帮助的。命令行标志 `--compiled-modules={yes|no|existing}` 使您能够切换模块预编译的开启和关闭。当使用 `--compiled-modules=no` 启动 Julia 时，编译缓存中的序列化模块在加载模块和模块依赖项时会被忽略。在某些情况下，您可能希望加载现有的预编译模块，但不创建新的模块。这可以通过使用 `--compiled-modules=existing` 启动 Julia 来实现。使用 `--pkgimages={yes|no|existing}` 可以获得更细粒度的控制，这仅影响预编译期间的本机代码存储。`Base.compilecache` 仍然可以手动调用。此命令行标志的状态会传递给 `Pkg.build`，以在安装、更新和显式构建包时禁用自动预编译触发。

您还可以通过环境变量调试一些预编译失败。设置 `JULIA_VERBOSE_LINKING=true` 可能有助于解决编译的本机代码共享库链接失败的问题。请参阅 Julia 手册中的 **开发者文档** 部分，您将在“包图像”下的 Julia 内部文档部分找到更多详细信息。

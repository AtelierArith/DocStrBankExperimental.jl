# [Types](@id man-types)

类型系统传统上分为两种截然不同的类型：静态类型系统，其中每个程序表达式的类型必须在程序执行之前可计算，和动态类型系统，其中在运行时之前对类型一无所知，只有在程序操作的实际值可用时才能知道。面向对象编程允许在静态类型语言中有一定的灵活性，因为可以在编译时不知道值的精确类型的情况下编写代码。能够编写可以操作不同类型的代码的能力称为多态性。经典动态类型语言中的所有代码都是多态的：只有通过显式检查类型，或者当对象在运行时未能支持操作时，任何值的类型才会受到限制。

Julia的类型系统是动态的，但通过使得可以指示某些值是特定类型，从而获得了一些静态类型系统的优势。这在生成高效代码方面可以提供很大帮助，但更重要的是，它允许基于函数参数的类型进行方法调度，这与语言深度集成。方法调度在[Methods](@ref)中进行了详细探讨，但其根源在于这里呈现的类型系统。

在Julia中，当省略类型时，默认行为是允许值为任何类型。因此，可以编写许多有用的Julia函数，而无需明确使用类型。然而，当需要额外的表达能力时，可以很容易地逐步将显式类型注释引入之前的“无类型”代码中。添加注释主要有三个目的：利用Julia强大的多重分发机制，提高人类可读性，以及捕捉程序员错误。

Describing Julia in the lingo of [type systems](https://en.wikipedia.org/wiki/Type_system), it is: dynamic, nominative and parametric. Generic types can be parameterized, and the hierarchical relationships between types are [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system), rather than [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system). One particularly distinctive feature of Julia's type system is that concrete types may not subtype each other: all concrete types are final and may only have abstract types as their supertypes. While this might at first seem unduly restrictive, it has many beneficial consequences with surprisingly few drawbacks. It turns out that being able to inherit behavior is much more important than being able to inherit structure, and inheriting both causes significant difficulties in traditional object-oriented languages. Other high-level aspects of Julia's type system that should be mentioned up front are:

  * 在Julia中，对象值和非对象值之间没有划分：所有值都是具有类型的真正对象，这些类型属于一个单一的、完全连接的类型图，所有节点在类型上都是同等的第一类。
  * 没有“编译时类型”的有意义概念：一个值的唯一类型是在程序运行时的实际类型。在面向对象的语言中，这被称为“运行时类型”，因为静态编译与多态性的结合使这一区分变得重要。
  * 只有值，而不是变量，具有类型——变量只是绑定到值的名称，尽管为了简单起见，我们可以将“变量的类型”作为“变量所指向的值的类型”的简写。
  * 抽象类型和具体类型都可以通过其他类型进行参数化。它们还可以通过符号进行参数化，通过任何类型的值进行参数化，对于这些值，[`isbits`](@ref) 返回 true（本质上，像数字和布尔值这样的东西，它们像 C 类型或没有指向其他对象的指针的 `struct` 一样存储），也可以通过这些元组进行参数化。当类型参数不需要被引用或限制时，可以省略它们。

Julia 的类型系统旨在强大而富有表现力，同时又清晰、直观且不显眼。许多 Julia 程序员可能从未感到需要编写明确使用类型的代码。然而，某些类型的编程在声明类型后变得更清晰、更简单、更快速且更稳健。

## Type Declarations

`::` 运算符可以用于将类型注解附加到程序中的表达式和变量上。这样做主要有两个原因：

1. 作为一种断言，以帮助确认您的程序按预期工作，并且
2. 为了向编译器提供额外的类型信息，从而在某些情况下提高性能。

当附加到计算值的表达式时，`::` 运算符被读作“是……的实例”。它可以在任何地方使用，以断言左侧表达式的值是右侧类型的实例。当右侧的类型是具体类型时，左侧的值必须具有该类型作为其实现——请记住，所有具体类型都是最终的，因此没有实现是任何其他类型的子类型。当类型是抽象类型时，只需左侧的值由一个具体类型实现，该具体类型是抽象类型的子类型。如果类型断言不成立，将抛出异常；否则，将返回左侧的值：

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

这允许类型断言直接附加到任何表达式上。

当附加到赋值左侧的变量上，或作为 `local` 声明的一部分时，`::` 运算符的含义略有不同：它声明变量始终具有指定的类型，类似于静态类型语言（如 C）中的类型声明。分配给变量的每个值都将使用 [`convert`](@ref) 转换为声明的类型：

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

此功能对于避免性能“陷阱”非常有用，因为如果对变量的某个赋值意外地改变了其类型，可能会导致问题。

这种“声明”行为仅在特定上下文中发生：

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

并适用于整个当前范围，甚至在声明之前。

从 Julia 1.8 开始，类型声明现在可以在全局范围内使用，即可以向全局变量添加类型注释，以使访问它们的类型稳定。

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

声明也可以附加到函数定义上：

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

从这个函数返回的行为就像对一个声明类型的变量进行赋值：值总是被转换为 `Float64`。

## [Abstract Types](@id man-abstract-types)

抽象类型不能被实例化，仅作为类型图中的节点，描述一组相关的具体类型：那些作为其后代的具体类型。我们从抽象类型开始，尽管它们没有实例化，因为它们是类型系统的支柱：它们形成了概念层次，使得Julia的类型系统不仅仅是对象实现的集合。

回想一下在 [Integers and Floating-Point Numbers](@ref) 中，我们介绍了多种具体的数值类型：[`Int8`](@ref)，[`UInt8`](@ref)，[`Int16`](@ref)，[`UInt16`](@ref)，[`Int32`](@ref)，[`UInt32`](@ref)，[`Int64`](@ref)，[`UInt64`](@ref)，[`Int128`](@ref)，[`UInt128`](@ref)，[`Float16`](@ref)，[`Float32`](@ref)，以及 [`Float64`](@ref)。尽管它们的表示大小不同，`Int8`、`Int16`、`Int32`、`Int64` 和 `Int128` 都有一个共同点，即它们是有符号整数类型。同样，`UInt8`、`UInt16`、`UInt32`、`UInt64` 和 `UInt128` 都是无符号整数类型，而 `Float16`、`Float32` 和 `Float64` 则不同，因为它们是浮点类型而不是整数。通常，一段代码只有在其参数是某种整数时才有意义，但并不真正依赖于特定的*种类*整数。例如，最大公约数算法适用于所有种类的整数，但不适用于浮点数。抽象类型允许构建类型层次结构，提供一个上下文，使具体类型能够适应。这使得你可以轻松地编程到任何整数类型，而不将算法限制为特定类型的整数。

抽象类型使用 [`abstract type`](@ref) 关键字声明。声明抽象类型的一般语法是：

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

`abstract type` 关键字引入了一种新的抽象类型，其名称由 `«name»` 给出。这个名称可以选择性地跟随 [`<:`](@ref) 和一个已经存在的类型，表示新声明的抽象类型是这个“父”类型的子类型。

当没有给出超类型时，默认超类型是 `Any` —— 一个所有对象都是其实例、所有类型都是其子类型的预定义抽象类型。在类型理论中，`Any` 通常被称为“顶层”，因为它位于类型图的顶端。Julia 还有一个预定义的抽象“底层”类型，位于类型图的底端，写作 `Union{}`。它与 `Any` 完全相反：没有对象是 `Union{}` 的实例，所有类型都是 `Union{}` 的超类型。

让我们考虑构成Julia数值层次的一些抽象类型：

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

[`Number`](@ref) 类型是 `Any` 的直接子类型，而 [`Real`](@ref) 是它的子类型。反过来，`Real` 有两个子类型（它有更多，但这里只显示两个；稍后我们会讨论其他类型）：[`Integer`](@ref) 和 [`AbstractFloat`](@ref)，将世界分为整数的表示和实数的表示。实数的表示包括浮点类型，但也包括其他类型，例如有理数。`AbstractFloat` 仅包括实数的浮点表示。整数进一步细分为 [`Signed`](@ref) 和 [`Unsigned`](@ref) 类型。

`<:` 运算符通常表示“是一个子类型”，并且在像上面那样的声明中使用时，声明右侧类型为新声明类型的直接超类型。它也可以在表达式中用作子类型运算符，当其左操作数是其右操作数的子类型时返回 `true`：

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

抽象类型的一个重要用途是为具体类型提供默认实现。举个简单的例子，考虑：

```julia
function myplus(x,y)
    x+y
end
```

首先需要注意的是，上述参数声明等价于 `x::Any` 和 `y::Any`。当这个函数被调用时，比如 `myplus(2,5)`，调度器会选择与给定参数匹配的最具体的名为 `myplus` 的方法。（有关多重调度的更多信息，请参见 [Methods](@ref)。）

假设没有比上述更具体的方法被找到，Julia 接下来内部定义并编译一个名为 `myplus` 的方法，专门用于两个 `Int` 参数，基于上述给出的通用函数，即它隐式地定义并编译：

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

最后，它调用了这个特定的方法。

因此，抽象类型允许程序员编写通用函数，这些函数可以作为许多具体类型组合的默认方法。由于多重调度，程序员可以完全控制使用默认方法还是更具体的方法。

一个重要的要点是，如果程序员依赖于一个参数为抽象类型的函数，则性能不会下降，因为它会针对每个具体参数类型的元组进行重新编译。然而，在函数参数是抽象类型的容器的情况下，可能会存在性能问题；请参见 [Performance Tips](@ref man-performance-abstract-container)。

## Primitive Types

!!! warning
    几乎总是更可取将现有的原始类型包装在一个新的复合类型中，而不是定义自己的原始类型。

    此功能的存在是为了允许Julia引导LLVM支持的标准原始类型。一旦它们被定义，就几乎没有理由再定义更多。


原始类型是一个具体类型，其数据由普通的位组成。原始类型的经典示例是整数和浮点值。与大多数语言不同，Julia 允许您声明自己的原始类型，而不仅仅提供一组固定的内置类型。实际上，标准原始类型都是在语言本身中定义的：

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

声明原始类型的一般语法是：

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

位数表示该类型所需的存储量，而名称则为新类型命名。原始类型可以选择声明为某个超类型的子类型。如果省略超类型，则该类型默认为以 `Any` 作为其直接超类型。因此，上述声明 [`Bool`](@ref) 意味着布尔值需要八位来存储，并且其直接超类型为 [`Integer`](@ref)。目前，仅支持8位的倍数大小，您可能会在使用其他大小时遇到LLVM错误。因此，布尔值虽然实际上只需要一个位，但不能声明为小于八位。

类型 [`Bool`](@ref)、[`Int8`](@ref) 和 [`UInt8`](@ref) 都具有相同的表示：它们是八位字节的内存块。然而，由于 Julia 的类型系统是命名的，它们并不能互换，尽管它们具有相同的结构。它们之间的一个根本区别在于它们具有不同的超类型：`4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` 的直接超类型是 [`Integer`](@ref)，`4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` 的超类型是 [`Signed`](@ref)，而 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` 的超类型是 [`Unsigned`](@ref)。`4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`、`4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` 和 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` 之间的所有其他区别都是行为问题——当将这些类型的对象作为参数传递时，函数的定义方式。这就是为什么命名类型系统是必要的原因：如果结构决定类型，而类型又决定行为，那么就不可能使 `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` 的行为与 `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` 或 `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` 有所不同。

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type) 在各种语言中被称为记录、结构或对象。复合类型是命名字段的集合，其实例可以被视为单个值。在许多语言中，复合类型是唯一可用户定义的类型，并且它们也是 Julia 中最常用的用户定义类型。

在主流的面向对象语言中，如 C++、Java、Python 和 Ruby，复合类型也有与之关联的命名函数，这种组合被称为“对象”。在更纯粹的面向对象语言中，如 Ruby 或 Smalltalk，所有值都是对象，无论它们是否是复合类型。在不那么纯粹的面向对象语言中，包括 C++ 和 Java，一些值，如整数和浮点值，并不是对象，而用户定义的复合类型的实例是真正的对象，具有相关的方法。在 Julia 中，所有值都是对象，但函数并不与它们操作的对象捆绑在一起。这是必要的，因为 Julia 通过多重分发选择使用哪个函数的方法，这意味着在选择方法时会考虑函数的 *所有* 参数的类型，而不仅仅是第一个（有关方法和分发的更多信息，请参见 [Methods](@ref)）。因此，函数“属于”它们的第一个参数是不合适的。将方法组织成函数对象，而不是在每个对象“内部”拥有命名的方法包，最终成为语言设计的一个高度有益的方面。

复合类型通过 [`struct`](@ref) 关键字引入，后面跟着一个字段名称块，字段名称可以选择性地使用 `::` 运算符注释类型：

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

没有类型注解的字段默认为 `Any`，因此可以容纳任何类型的值。

新的 `Foo` 类型的对象是通过将 `Foo` 类型对象像函数一样应用于其字段的值来创建的：

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

当一个类型像函数一样被应用时，它被称为*构造函数*。自动生成两个构造函数（这些被称为*默认构造函数*）。一个接受任何参数并调用 [`convert`](@ref) 将它们转换为字段的类型，另一个接受与字段类型完全匹配的参数。生成这两个构造函数的原因是，这使得添加新定义变得更容易，而不会无意中替换默认构造函数。

由于 `bar` 字段在类型上没有限制，因此任何值都可以。然而，`baz` 的值必须可以转换为 `Int`：

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

您可以使用 [`fieldnames`](@ref) 函数找到字段名称的列表。

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

您可以使用传统的 `foo.bar` 语法访问复合对象的字段值：

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

用 `struct` 声明的复合对象是 *不可变的*；在构造后无法修改。这起初可能看起来很奇怪，但它有几个优点：

  * 它可以更高效。一些结构可以有效地打包到数组中，在某些情况下，编译器能够完全避免分配不可变对象。
  * 不可能违反类型构造函数提供的不变性。
  * 使用不可变对象的代码更容易推理。

一个不可变对象可能包含可变对象，例如数组，作为字段。这些包含的对象将保持可变；只有不可变对象本身的字段不能更改为指向不同的对象。

在需要的情况下，可使用关键字 [`mutable struct`](@ref) 声明可变复合对象，具体将在下一节讨论。

如果一个不可变结构的所有字段都是不可区分的 (`===`)，那么包含这些字段的两个不可变值也是不可区分的：

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

关于复合类型实例的创建还有很多要说的内容，但这个讨论依赖于 [Parametric Types](@ref) 和 [Methods](@ref)，并且足够重要，值得在自己的章节中讨论：[Constructors](@ref man-constructors)。

对于许多用户定义的类型 `X`，您可能希望定义一个方法 [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting)，以便该类型的实例作为 [broadcasting](@ref Broadcasting) 的 0 维“标量”进行操作。

## Mutable Composite Types

如果一个复合类型是用 `mutable struct` 声明的，而不是用 `struct`，那么它的实例可以被修改：

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

可以通过 [Instance Properties](@ref man-instance-properties) 提供一个额外的接口，连接字段和用户。这提供了更多的控制权，允许使用 `bar.baz` 语法访问和修改内容。

为了支持变异，这类对象通常在堆上分配，并具有稳定的内存地址。可变对象就像一个小容器，可能随着时间的推移而保存不同的值，因此只能通过其地址可靠地识别。相比之下，不可变类型的实例与特定的字段值相关联——字段值本身告诉你关于对象的所有信息。在决定是否使一个类型可变时，问问两个具有相同字段值的实例是否会被视为相同，或者它们是否可能需要独立地随时间变化。如果它们会被视为相同，那么该类型可能应该是不可变的。

回顾一下，有两个基本属性定义了Julia中的不可变性：

  * 不允许修改不可变类型的值。

      * 对于位类型，这意味着一旦设置值的位模式将永远不会改变，并且该值就是位类型的标识。
      * 对于复合类型，这意味着其字段值的身份将永远不会改变。当字段是位类型时，这意味着它们的位将永远不会改变；对于值是可变类型（如数组）的字段，这意味着这些字段将始终引用相同的可变值，即使该可变值的内容可能会被修改。
  * 一个具有不可变类型的对象可以被编译器自由复制，因为它的不可变性使得在程序上无法区分原始对象和副本。

      * 特别地，这意味着像整数和浮点数这样足够小的不可变值通常通过寄存器（或栈分配）传递给函数。
      * 可变值则是堆分配的，并作为指向堆分配值的指针传递给函数，除非编译器确定没有办法判断这不是正在发生的情况。

在某些情况下，如果一个可变结构体的一个或多个字段已知是不可变的，可以使用 `const` 声明这些字段，如下所示。这使得某些，但不是所有的不可变结构体的优化成为可能，并且可以用于强制特定标记为 `const` 的字段的不变性。

!!! compat "Julia 1.8"
    `const` 注解可变结构体字段需要至少 Julia 1.8。


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

在前面的章节中讨论的三种类型（抽象类型、原始类型、复合类型）实际上都是紧密相关的。它们共享相同的关键属性：

  * 它们被明确声明。
  * 他们有名字。
  * 他们已明确声明超类型。
  * 它们可能有参数。

由于这些共享属性，这些类型在内部被表示为同一概念的实例，即 `DataType`，这是这些类型的任何类型。

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

一个 `DataType` 可以是抽象的或具体的。如果它是具体的，它具有指定的大小、存储布局和（可选的）字段名称。因此，原始类型是一个具有非零大小但没有字段名称的 `DataType`。复合类型是一个具有字段名称或为空（零大小）的 `DataType`。

系统中的每个具体值都是某种 `DataType` 的实例。

## Type Unions

类型联合是一种特殊的抽象类型，它包含作为对象的所有实例，任何其参数类型的实例，使用特殊的 [`Union`](@ref) 关键字构造：

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

许多语言的编译器都有一个内部的联合体构造，用于推理类型；Julia 只是将其暴露给程序员。Julia 编译器能够在存在 `Union` 类型的情况下生成高效的代码，且类型数量较少 [^1]，通过为每种可能的类型在不同的分支中生成专门的代码。

一个特别有用的 `Union` 类型案例是 `Union{T, Nothing}`，其中 `T` 可以是任何类型，而 [`Nothing`](@ref) 是唯一类型，其唯一实例是对象 [`nothing`](@ref)。这种模式是 Julia 中 [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) 类型在其他语言中的等价物。将函数参数或字段声明为 `Union{T, Nothing}` 允许将其设置为类型 `T` 的值，或设置为 `nothing` 以指示没有值。有关更多信息，请参见 [this FAQ entry](@ref faq-nothing)。

## Parametric Types

Julia 的类型系统一个重要而强大的特性是它是参数化的：类型可以接受参数，因此类型声明实际上引入了一整套新的类型——每种可能的参数值组合都有一个类型。许多语言支持某种版本的 [generic programming](https://en.wikipedia.org/wiki/Generic_programming)，在其中可以在不指定涉及的确切类型的情况下指定数据结构和操作它们的算法。例如，ML、Haskell、Ada、Eiffel、C++、Java、C#、F# 和 Scala 等语言中存在某种形式的泛型编程，仅举几例。这些语言中的一些支持真正的参数多态（例如 ML、Haskell、Scala），而其他语言则支持临时的、基于模板的泛型编程风格（例如 C++、Java）。由于各种语言中有如此多不同种类的泛型编程和参数化类型，我们甚至不会尝试将 Julia 的参数化类型与其他语言进行比较，而是专注于解释 Julia 自身的系统。然而，我们会注意到，由于 Julia 是一种动态类型语言，并且不需要在编译时做出所有类型决策，因此在静态参数化类型系统中遇到的许多传统困难可以相对容易地处理。

所有声明的类型（`DataType` 类型）都可以参数化，语法在每种情况下都是相同的。我们将按以下顺序讨论它们：首先是参数化复合类型，然后是参数化抽象类型，最后是参数化原始类型。

### [Parametric Composite Types](@id man-parametric-composite-types)

类型参数紧接在类型名称后面，引号括起来：

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

此声明定义了一种新的参数化类型 `Point{T}`，它包含两个类型为 `T` 的“坐标”。人们可能会问，`T` 是什么？好吧，这正是参数化类型的要点：它可以是任何类型（或者实际上是任何位类型的值，尽管在这里它显然被用作类型）。`Point{Float64}` 是一个具体类型，相当于通过在 `Point` 的定义中用 [`Float64`](@ref) 替换 `T` 而定义的类型。因此，这个单一的声明实际上声明了无限数量的类型：`Point{Float64}`、`Point{AbstractString}`、`Point{Int64}` 等等。每一个这些现在都是可用的具体类型：

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

类型 `Point{Float64}` 是一个坐标为 64 位浮点值的点，而类型 `Point{AbstractString}` 是一个“点”，其“坐标”是字符串对象（见 [Strings](@ref)）。

`Point` 本身也是一个有效的类型对象，包含所有实例 `Point{Float64}`、`Point{AbstractString}` 等作为子类型：

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

其他类型当然不是它的子类型：

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

具体的 `Point` 类型具有不同的 `T` 值，彼此之间永远不是子类型：

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    这一最后一点是 *非常* 重要的：即使 `Float64 <: Real`，我们 **并不** 有 `Point{Float64} <: Point{Real}`。


换句话说，在类型理论的术语中，Julia 的类型参数是 *不变的*，而不是 [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29)。这是出于实际原因：虽然 `Point{Float64}` 的任何实例在概念上可能与 `Point{Real}` 的实例相似，但这两种类型在内存中的表示是不同的：

  * 一个 `Point{Float64}` 的实例可以紧凑且高效地表示为一对 64 位值；
  * 一个 `Point{Real}` 的实例必须能够容纳任何一对 [`Real`](@ref) 的实例。由于 `Real` 的实例可以具有任意大小和结构，因此在实践中，`Point{Real}` 的实例必须表示为指向单独分配的 `Real` 对象的指针对。

通过能够存储具有即时值的 `Point{Float64}` 对象所获得的效率在数组的情况下被极大地放大：`Array{Float64}` 可以作为 64 位浮点值的连续内存块存储，而 `Array{Real}` 必须是指向单独分配的 [`Real`](@ref) 对象的指针数组——这些对象可能是 [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing) 64 位浮点值，但也可能是任意大、复杂的对象，这些对象被声明为 `Real` 抽象类型的实现。

由于 `Point{Float64}` 不是 `Point{Real}` 的子类型，因此以下方法无法应用于 `Point{Float64}` 类型的参数：

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

定义一个接受所有类型为 `Point{T}` 的参数的方法的正确方式，其中 `T` 是 [`Real`](@ref) 的子类型：

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

（等效地，可以定义 `function norm(p::Point{T} where T<:Real)` 或 `function norm(p::Point{T}) where T<:Real`；请参见 [UnionAll Types](@ref)。）

更多示例将在 [Methods](@ref) 中讨论。

如何构造一个 `Point` 对象？可以为复合类型定义自定义构造函数，具体内容将在 [Constructors](@ref man-constructors) 中详细讨论，但在没有任何特殊构造函数声明的情况下，有两种默认的方法来创建新的复合对象，一种是显式给出类型参数，另一种是通过对象构造函数的参数隐含给出。

由于类型 `Point{Float64}` 是一个具体类型，相当于用 [`Float64`](@ref) 替代 `T` 声明的 `Point`，因此可以相应地作为构造函数使用：

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

对于默认构造函数，每个字段必须提供恰好一个参数：

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

仅为参数化类型生成一个默认构造函数，因为无法重写它。该构造函数接受任何参数并将其转换为字段类型。

在许多情况下，提供要构造的 `Point` 对象的类型是多余的，因为构造函数调用的参数类型已经隐式提供了类型信息。因此，只要参数类型 `T` 的隐含值不模糊，您也可以将 `Point` 本身作为构造函数使用：

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

在 `Point` 的情况下，只有当 `Point` 的两个参数具有相同类型时，`T` 的类型才是明确的。如果情况不是这样，构造函数将会失败，并显示 [`MethodError`](@ref)：

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

构造方法可以定义以适当地处理这种混合情况，但这将在稍后在 [Constructors](@ref man-constructors) 中讨论。

### Parametric Abstract Types

参数化抽象类型声明以类似的方式声明了一组抽象类型：

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

通过这个声明，`Pointy{T}` 是每个类型或整数值 `T` 的一个独特抽象类型。与参数化复合类型一样，每个这样的实例都是 `Pointy` 的一个子类型：

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

参数化抽象类型是不可变的，就像参数化复合类型一样：

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

符号 `Pointy{<:Real}` 可用于表示 Julia 中的 *协变* 类型，而 `Pointy{>:Int}` 则表示 *逆变* 类型，但从技术上讲，这些表示的是 *类型集合*（参见 [UnionAll Types](@ref)）。

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

正如普通的抽象类型用于在具体类型上创建有用的类型层次结构，参数化抽象类型在参数化复合类型方面也起到相同的作用。例如，我们可以将 `Point{T}` 声明为 `Pointy{T}` 的子类型，如下所示：

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

给定这样的声明，对于每个 `T` 的选择，我们有 `Point{T}` 作为 `Pointy{T}` 的子类型：

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

这个关系也是不变的：

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

参数化抽象类型如 `Pointy` 的目的是什么？考虑如果我们创建一个类似点的实现，只需要一个坐标，因为该点位于对角线 *x = y* 上：

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

现在 `Point{Float64}` 和 `DiagPoint{Float64}` 都是 `Pointy{Float64}` 抽象的实现，其他可能的类型 `T` 选择也是如此。这允许以所有 `Pointy` 对象共享的公共接口进行编程，`Point` 和 `DiagPoint` 都实现了该接口。然而，在我们引入方法和调度的下一节 [Methods](@ref) 之前，这一点无法完全演示。

在某些情况下，类型参数自由地覆盖所有可能的类型可能没有意义。在这种情况下，可以通过以下方式限制 `T` 的范围：

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

通过这样的声明，可以接受使用任何类型，该类型是 [`Real`](@ref) 的子类型来替代 `T`，但不能使用不是 `Real` 的子类型的类型：

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

参数化复合类型的类型参数可以以相同的方式进行限制：

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

为了给出一个实际的例子，说明所有这些参数类型机制如何有用，这里是 Julia 的 [`Rational`](@ref) 不可变类型的实际定义（为了简化，我们在这里省略了构造函数），表示整数的精确比率：

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

它只有在取整数值的比率时才有意义，因此参数类型 `T` 被限制为 [`Integer`](@ref) 的子类型，并且整数的比率表示实数线上的一个值，因此任何 [`Rational`](@ref) 是 [`Real`](@ref) 抽象的一个实例。

### Tuple Types

元组是函数参数的抽象——没有函数本身。函数参数的显著方面是它们的顺序和类型。因此，元组类型类似于一个参数化的不可变类型，其中每个参数是一个字段的类型。例如，2元素元组类型类似于以下不可变类型：

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

然而，有三个关键区别：

  * 元组类型可以有任意数量的参数。
  * 元组类型在其参数中是*协变*的：`Tuple{Int}` 是 `Tuple{Any}` 的子类型。因此，`Tuple{Any}` 被视为抽象类型，只有当其参数是具体的时，元组类型才是具体的。
  * 元组没有字段名称；字段只能通过索引访问。

元组值用括号和逗号表示。当构造一个元组时，会按需生成适当的元组类型：

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

注意协方差的含义：

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

直观上，这对应于函数参数的类型是函数签名的子类型（当签名匹配时）。

### Vararg Tuple Types

元组类型的最后一个参数可以是特殊值 [`Vararg`](@ref)，表示任意数量的尾随元素：

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

此外，`Vararg{T}` 对应于零个或多个类型为 `T` 的元素。Vararg 元组类型用于表示 varargs 方法接受的参数（参见 [Varargs Functions](@ref)）。

特殊值 `Vararg{T,N}`（当用作元组类型的最后一个参数时）对应于恰好 `N` 个类型为 `T` 的元素。 `NTuple{N,T}` 是 `Tuple{Vararg{T,N}}` 的一个方便别名，即包含恰好 `N` 个类型为 `T` 的元素的元组类型。

### Named Tuple Types

命名元组是 [`NamedTuple`](@ref) 类型的实例，该类型有两个参数：一个给字段名称的符号元组和一个给字段类型的元组类型。为了方便，`NamedTuple` 类型使用 [`@NamedTuple`](@ref) 宏进行打印，该宏提供了一种方便的类似 `struct` 的语法，通过 `key::Type` 声明这些类型，其中省略的 `::Type` 对应于 `::Any`。

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

`@NamedTuple` 宏的 `begin ... end` 形式允许声明跨多行（类似于结构体声明），但在其他方面是等效的：

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

一个 `NamedTuple` 类型可以用作构造函数，接受一个元组参数。构造的 `NamedTuple` 类型可以是一个具体类型，指定了两个参数，或者是一个仅指定字段名称的类型：

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

如果指定了字段类型，则参数会被转换。否则，参数的类型将直接使用。

### Parametric Primitive Types

原始类型也可以被参数化声明。例如，指针被表示为原始类型，在Julia中可以这样声明：

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

这些声明与典型的参数化复合类型相比，稍显奇特的特征是，类型参数 `T` 并未在类型本身的定义中使用——它只是一个抽象标签，实质上定义了一整个具有相同结构的类型家族，仅通过其类型参数进行区分。因此，`Ptr{Float64}` 和 `Ptr{Int64}` 是不同的类型，尽管它们具有相同的表示形式。当然，所有特定的指针类型都是伞形 [`Ptr`](@ref) 类型的子类型：

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

我们已经说过，像 `Ptr` 这样的参数类型充当其所有实例（`Ptr{Int64}` 等）的超类型。这是如何工作的呢？`Ptr` 本身不能是一个普通的数据类型，因为在不知道引用数据类型的情况下，该类型显然无法用于内存操作。答案是 `Ptr`（或其他参数类型如 `Array`）是一种不同类型，称为 [`UnionAll`](@ref) 类型。这种类型表示某个参数的所有值的 *迭代并集*。

`UnionAll` 类型通常使用关键字 `where` 来编写。例如，`Ptr` 可以更准确地写成 `Ptr{T} where T`，这意味着所有类型为 `Ptr{T}` 的值，其中 `T` 的某个值。在这个上下文中，参数 `T` 也常被称为“类型变量”，因为它就像一个在类型上变化的变量。每个 `where` 引入一个单一的类型变量，因此对于具有多个参数的类型，这些表达式是嵌套的，例如 `Array{T,N} where N where T`。

类型应用语法 `A{B,C}` 要求 `A` 是一个 `UnionAll` 类型，并首先将 `B` 替换为 `A` 中最外层的类型变量。结果预计是另一个 `UnionAll` 类型，然后将 `C` 替换进去。因此，`A{B,C}` 等价于 `A{B}{C}`。这解释了为什么可以部分实例化一个类型，例如 `Array{Float64}`：第一个参数值已被固定，但第二个仍然可以在所有可能的值中变化。使用显式的 `where` 语法，可以固定任何参数的子集。例如，所有一维数组的类型可以写为 `Array{T,1} where T`。

类型变量可以通过子类型关系进行限制。 `Array{T} where T<:Integer` 指的是所有元素类型为某种 [`Integer`](@ref) 的数组。语法 `Array{<:Integer}` 是 `Array{T} where T<:Integer` 的一种方便的简写。类型变量可以同时具有下界和上界。 `Array{T} where Int<:T<:Number` 指的是所有能够包含 `Int` 的 [`Number`](@ref) 数组（因为 `T` 必须至少与 `Int` 一样大）。语法 `where T>:Int` 也可以用来仅指定类型变量的下界，而 `Array{>:Int}` 等价于 `Array{T} where T>:Int`。

由于 `where` 表达式可以嵌套，类型变量的边界可以引用外部类型变量。例如 `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real` 指的是 2 元组，其第一个元素是某个 [`Real`](@ref)，而第二个元素是任何类型的数组的 `Array`，其元素类型包含第一个元组元素的类型。

`where` 关键字本身可以嵌套在更复杂的声明中。例如，考虑以下声明创建的两种类型：

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

类型 `T1` 定义了一个一维数组，其中包含一维数组；每个内部数组由相同类型的对象组成，但这种类型可以在不同的内部数组之间变化。另一方面，类型 `T2` 定义了一个一维数组，其中所有内部数组必须具有相同的类型。请注意，`T2` 是一个抽象类型，例如，`Array{Array{Int,1},1} <: T2`，而 `T1` 是一个具体类型。因此，`T1` 可以通过零参数构造函数构造 `a=T1()`，但 `T2` 不能。

有一种方便的语法用于命名此类类型，类似于函数定义语法的简写形式：

```julia
Vector{T} = Array{T, 1}
```

这相当于 `const Vector = Array{T,1} where T`。写 `Vector{Float64}` 相当于写 `Array{Float64,1}`，而伞形类型 `Vector` 的实例是所有 `Array` 对象，其中第二个参数 - 数组维度的数量 - 是 1，无论元素类型是什么。在必须始终完整指定参数类型的语言中，这并不是特别有用，但在 Julia 中，这允许人们仅写 `Vector` 来表示包括任何元素类型的所有一维稠密数组的抽象类型。

## [Singleton types](@id man-singleton-types)

不可变的复合类型没有字段被称为 *单例*。正式地，如果

1. `T` 是一种不可变的复合类型（即使用 `struct` 定义），
2. `a isa T && b isa T` 意味着 `a === b`，

然后 `T` 是一个单例类型。[^2] [`Base.issingletontype`](@ref) 可以用来检查一个类型是否是单例类型。[Abstract types](@ref man-abstract-types) 由于构造的原因不能是单例类型。

根据定义，可以得出这样的类型只能有一个实例：

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

[`===`](@ref) 函数确认构造的 `NoFields` 实例实际上是同一个。

当上述条件成立时，参数化类型可以是单例类型。例如，

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

每个函数都有自己的类型，该类型是 `Function` 的子类型。

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

注意 `typeof(foo41)` 打印为它本身。这仅仅是打印的一个约定，因为它是一个可以像其他值一样使用的第一类对象：

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

顶层定义的函数类型是单例。当有必要时，您可以将它们与 [`===`](@ref) 进行比较。

[Closures](@ref man-anonymous-functions) 也有自己的类型，通常以 `#<number>` 结尾的名称打印。不同位置定义的函数的名称和类型是不同的，但不保证在不同会话中以相同的方式打印。

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

闭包的类型不一定是单例。

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

对于每种类型 `T`，`Type{T}` 是一个抽象的参数化类型，其唯一实例是对象 `T`。在我们讨论 [Parametric Methods](@ref) 和 [conversions](@ref conversion-and-promotion) 之前，很难解释这个构造的实用性，但简而言之，它允许人们根据特定类型作为 *值* 来专门化函数行为。这对于编写方法（尤其是参数化方法）非常有用，因为其行为依赖于作为显式参数给出的类型，而不是由其参数之一的类型隐含得出。

由于定义有点难以理解，我们来看一些例子：

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

换句话说，[`isa(A, Type{B})`](@ref) 仅在 `A` 和 `B` 是同一个对象且该对象是一个类型时为真。

特别地，由于参数化类型是 [invariant](@ref man-parametric-composite-types)，我们有

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

没有参数时，`Type` 只是一个抽象类型，其所有类型对象都是它的实例：

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

任何不是类型的对象都不是 `Type` 的实例：

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

虽然 `Type` 是朱莉亚类型层次结构的一部分，像其他任何抽象参数类型一样，但它在方法签名之外并不常用，除非在某些特殊情况下。`Type` 的另一个重要用例是细化字段类型，否则这些类型会被捕获得不够精确，例如在下面的示例中作为 [`DataType`](@ref man-declared-types)，其中默认构造函数可能导致依赖于精确包装类型的代码出现性能问题（类似于 [abstract type parameters](@ref man-performance-abstract-container)）。

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

有时为一个已经可表达的类型引入一个新名称是方便的。这可以通过简单的赋值语句来完成。例如，`UInt` 被别名为 [`UInt32`](@ref) 或 [`UInt64`](@ref)，具体取决于系统上指针的大小：

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

这是通过 `base/boot.jl` 中的以下代码实现的：

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

当然，这取决于 `Int` 被别名为什么——但它被预定义为正确的类型——要么是 [`Int32`](@ref)，要么是 [`Int64`](@ref)。

（请注意，与 `Int` 不同，`Float` 并不存在作为特定大小的类型别名 [`AbstractFloat`](@ref)。与整数寄存器不同，`Int` 的大小反映了该机器上本机指针的大小，而浮点寄存器的大小则由 IEEE-754 标准规定。）

类型别名可以被参数化：

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

由于 Julia 中的类型本身就是对象，普通函数可以对它们进行操作。一些特别有用的函数已经被引入，用于处理或探索类型，例如 `<:` 运算符，它指示其左侧操作数是否是其右侧操作数的子类型。

[`isa`](@ref) 函数测试一个对象是否属于给定类型，并返回 true 或 false：

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

[`typeof`](@ref) 函数，已经在手册中的示例中使用，返回其参数的类型。正如上面所提到的，类型是对象，因此它们也有类型，我们可以询问它们的类型是什么：

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

如果我们重复这个过程会怎样？类型的类型是什么？实际上，类型都是复合值，因此它们都有一个类型为 `DataType`：

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType` 是它自己的类型。

另一个适用于某些类型的操作是 [`supertype`](@ref)，它揭示了一个类型的超类型。只有声明的类型（`DataType`）具有明确的超类型：

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

如果您将 [`supertype`](@ref) 应用到其他类型对象（或非类型对象）上，将会引发 [`MethodError`](@ref)：

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

通常，人们希望自定义类型实例的显示方式。这是通过重载 [`show`](@ref) 函数来实现的。例如，假设我们定义一个类型来表示极坐标形式的复数：

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

在这里，我们添加了一个自定义构造函数，以便它可以接受不同类型的 [`Real`](@ref) 参数并将它们提升到一个共同类型（参见 [Constructors](@ref man-constructors) 和 [Conversion and Promotion](@ref conversion-and-promotion)）。 （当然，我们还必须定义许多其他方法，以使其表现得像一个 [`Number`](@ref)，例如 `+`、`*`、`one`、`zero`、提升规则等等。）默认情况下，这种类型的实例显示得相当简单，包含类型名称和字段值的信息，例如 `Polar{Float64}(3.0,4.0)`。

如果我们希望它显示为 `3.0 * exp(4.0im)`，我们将定义以下方法将对象打印到给定的输出对象 `io`（表示文件、终端、缓冲区等；见 [Networking and Streams](@ref)）：

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

对 `Polar` 对象的显示进行更细粒度的控制是可能的。特别是，有时人们希望同时拥有一种详细的多行打印格式，用于在 REPL 和其他交互式环境中显示单个对象，以及一种更紧凑的单行格式，用于 [`print`](@ref) 或将对象作为另一个对象的一部分显示（例如，在数组中）。尽管默认情况下在这两种情况下都会调用 `show(io, z)` 函数，但您可以通过重载一个三参数形式的 `show` 来定义一种*不同的*多行格式，该形式将 `text/plain` MIME 类型作为第二个参数（参见 [Multimedia I/O](@ref Multimedia-I/O)），例如：

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

（注意，这里的 `print(..., z)` 将调用带有两个参数的 `show(io, z)` 方法。）这将导致：

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

在仍然使用单行 `show(io, z)` 形式来处理 `Polar` 值数组的地方。 从技术上讲，REPL 调用 `display(z)` 来显示执行一行的结果，默认情况下为 `show(stdout, MIME("text/plain"), z)`，而这又默认调用 `show(stdout, z)`，但你*不应该*定义新的 [`display`](@ref) 方法，除非你正在定义一个新的多媒体显示处理程序（参见 [Multimedia I/O](@ref Multimedia-I/O)）。

此外，您还可以为其他 MIME 类型定义 `show` 方法，以便在支持此功能的环境中（例如 IJulia）实现对象的更丰富显示（HTML、图像等）。例如，我们可以通过以下方式定义 `Polar` 对象的格式化 HTML 显示，带有上标和斜体：

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

一个 `Polar` 对象将在支持 HTML 显示的环境中自动显示，但如果您想要，可以手动调用 `show` 以获取 HTML 输出：

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

作为经验法则，单行的 `show` 方法应该打印出一个有效的 Julia 表达式，用于创建所显示的对象。当这个 `show` 方法包含中缀运算符，例如我们上面为 `Polar` 定义的单行 `show` 方法中的乘法运算符 (`*`)，在作为另一个对象的一部分打印时，可能无法正确解析。要查看这一点，请考虑表达式对象（参见 [Program representation](@ref)），它对我们 `Polar` 类型的特定实例进行平方运算：

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

因为运算符 `^` 的优先级高于 `*`（参见 [Operator Precedence and Associativity](@ref)），因此此输出并未忠实地表示表达式 `a ^ 2`，它应该等于 `(3.0 * exp(4.0im)) ^ 2`。为了解决这个问题，我们必须为 `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)` 创建一个自定义方法，该方法在打印时由表达式对象内部调用：

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

上述定义的方法在调用运算符的优先级高于或等于乘法的优先级时，会在对 `show` 的调用周围添加括号。此检查允许在打印时省略那些在没有括号的情况下也能正确解析的表达式（例如 `:($a + 2)` 和 `:($a == 2)`）：

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

在某些情况下，根据上下文调整 `show` 方法的行为是有用的。这可以通过 [`IOContext`](@ref) 类型来实现，该类型允许传递上下文属性以及一个包装的 IO 流。例如，当 `:compact` 属性设置为 `true` 时，我们可以在 `show` 方法中构建一个更简短的表示，如果该属性为 `false` 或缺失，则回退到长表示：

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

当传递的 IO 流是一个 `IOContext` 对象并且设置了 `:compact` 属性时，将使用这种新的紧凑表示法。特别是在打印具有多列的数组时（当水平空间有限时），情况就是如此：

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

请参阅 [`IOContext`](@ref) 文档，以获取可用于调整打印的常见属性列表。

## "Value types"

在 Julia 中，你不能基于 *值* 进行调度，例如 `true` 或 `false`。然而，你可以基于参数化类型进行调度，Julia 允许你将“普通位”值（类型、符号、整数、浮点数、元组等）作为类型参数包含在内。一个常见的例子是 `Array{T,N}` 中的维度参数，其中 `T` 是一个类型（例如，[`Float64`](@ref)），但 `N` 只是一个 `Int`。

您可以创建自己的自定义类型，这些类型将值作为参数，并使用它们来控制自定义类型的调度。为了说明这个想法，让我们引入参数类型 `Val{x}`，及其构造函数 `Val(x) = Val{x}()`，这是一种利用此技术的常用方式，适用于您不需要更复杂层次结构的情况。

[`Val`](@ref) 被定义为：

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

`Val` 的实现没有更多内容。 Julia 标准库中的一些函数接受 `Val` 实例作为参数，您也可以使用它来编写自己的函数。例如：

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

为了在 Julia 中保持一致，调用位置应始终传递一个 `Val` *实例*，而不是使用 *类型*，即使用 `foo(Val(:bar))` 而不是 `foo(Val{:bar})`。

值得注意的是，错误使用参数化的“值”类型（包括 `Val`）是非常容易的；在不利的情况下，您可能会使代码的性能变得更糟。特别是，您绝对不想像上面那样编写实际代码。有关 `Val` 的正确（和不正确）用法的更多信息，请阅读 [the more extensive discussion in the performance tips](@ref man-performance-value-type)。

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.

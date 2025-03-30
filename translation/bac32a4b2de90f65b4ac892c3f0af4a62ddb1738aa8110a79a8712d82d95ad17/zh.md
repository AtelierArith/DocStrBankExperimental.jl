# Frequently Asked Questions

## General

### Is Julia named after someone or something?

不。

### Why don't you compile Matlab/Python/R/… code to Julia?

由于许多人对其他动态语言的语法很熟悉，并且已经有很多代码是用这些语言编写的，因此自然会想知道为什么我们不直接将 Matlab 或 Python 前端插入 Julia 后端（或“转译”代码为 Julia），以便在不要求程序员学习新语言的情况下获得 Julia 的所有性能优势。简单，对吧？

基本问题是，*Julia的编译器没有什么特别之处*：我们使用的是一种常见的编译器（LLVM），没有其他语言开发者不知道的“秘密武器”。实际上，Julia的编译器在许多方面比其他动态语言（例如PyPy或LuaJIT）要简单得多。Julia的性能优势几乎完全来自于其前端：其语言语义允许一个[well-written Julia program](@ref man-performance-tips) *给编译器提供更多生成高效代码和内存布局的机会*。如果你尝试将Matlab或Python代码编译为Julia，我们的编译器将受到Matlab或Python语义的限制，生成的代码不会比现有的这些语言的编译器更好（可能还更差）。语义的关键作用也是为什么一些现有的Python编译器（如Numba和Pythran）仅尝试优化语言的一个小子集（例如对Numpy数组和标量的操作），而对于这个子集，它们的表现已经至少和我们在相同语义下的表现一样好。参与这些项目的人非常聪明，取得了惊人的成就，但将编译器改装到一个设计为解释执行的语言上是一个非常困难的问题。

Julia 的优势在于良好的性能并不局限于少数“内置”类型和操作，用户可以编写高层次的类型泛型代码，适用于任意用户定义的类型，同时保持快速和内存高效。在像 Python 这样的语言中，类型信息不足以提供给编译器以实现类似的能力，因此一旦你将这些语言用作 Julia 的前端，你就会陷入困境。

出于类似的原因，自动翻译成 Julia 的代码通常也会生成不可读、缓慢且不符合习惯用法的代码，这并不是从其他语言移植到原生 Julia 的一个良好起点。

另一方面，语言 *互操作性* 是非常有用的：我们希望从 Julia 利用其他语言中现有的高质量代码（反之亦然）！ 实现这一点的最佳方式不是转译器，而是通过简单的跨语言调用设施。 我们在这方面付出了很多努力，从内置的 `ccall` 内在（用于调用 C 和 Fortran 库）到 [JuliaInterop](https://github.com/JuliaInterop) 包，这些包将 Julia 连接到 Python、Matlab、C++ 等等。

## [Public API](@id man-api)

### How does Julia define its public API?

Julia的公共 [API](https://en.wikipedia.org/wiki/API) 是来自 `Base` 和标准库的公共符号文档中描述的行为。如果函数、类型和常量不是公共的，即使它们有文档字符串或在文档中被描述，也不属于公共API。此外，只有公共符号的文档化行为才是公共API的一部分。公共符号的未文档化行为是内部的。

公共符号是指标记为 `public foo` 或 `export foo` 的符号。

换句话说：

  * 公共符号的文档化行为是公共 API 的一部分。
  * 公共符号的未记录行为不属于公共 API 的一部分。
  * 私有符号的文档行为不属于公共 API 的一部分。
  * 私有符号的未记录行为不属于公共 API 的一部分。

您可以使用 `names(MyModule)` 获取模块的公共符号的完整列表。

包的作者被鼓励以类似的方式定义他们的公共 API。

Julia 的公共 API 中的任何内容都受到 [SemVer](https://semver.org/) 的保护，因此在 Julia 2.0 之前不会被删除或发生重大破坏性更改。

### There is a useful undocumented function/type/constant. Can I use it?

Updating Julia may break your code if you use non-public API.  If the code is self-contained, it may be a good idea to copy it into your project.  If you want to rely on a complex non-public API, especially when using it from a stable package, it is a good idea to open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning it into a public API.  However, we do not discourage the attempt to create packages that expose stable public interfaces while relying on non-public implementation details of Julia and buffering the differences across different Julia versions.

### The documentation is not accurate enough. Can I rely on the existing behavior?

请打开一个 [issue](https://github.com/JuliaLang/julia/issues) 或 [pull request](https://github.com/JuliaLang/julia/pulls) 来开始讨论将现有行为转变为公共 API。

## Sessions and the REPL

### How do I delete an object in memory?

Julia没有MATLAB的`clear`函数的类似功能；一旦在Julia会话中定义了一个名称（从技术上讲，在模块`Main`中），它将始终存在。

如果内存使用是您的关注点，您可以随时用消耗更少内存的对象替换对象。例如，如果 `A` 是一个您不再需要的千兆字节大小的数组，您可以通过 `A = nothing` 释放内存。内存将在下次垃圾收集器运行时释放；您可以通过 [`GC.gc()`](@ref Base.GC.gc) 强制执行此操作。此外，尝试使用 `A` 可能会导致错误，因为大多数方法在类型 `Nothing` 上未定义。

### How can I modify the declaration of a type in my session?

也许你已经定义了一个类型，然后意识到需要添加一个新字段。如果你在 REPL 中尝试这样做，你会得到错误：

```
ERROR: invalid redefinition of constant MyType
```

模块 `Main` 中的类型无法重新定义。

虽然在开发新代码时这可能会带来不便，但有一个很好的解决方法。模块可以通过重新定义来替换，因此如果你将所有新代码包装在一个模块中，你可以重新定义类型和常量。你不能将类型名称导入到 `Main` 中，然后期望在那里重新定义它们，但你可以使用模块名称来解决作用域。换句话说，在开发过程中，你可能会使用类似这样的工作流程：

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

当一个文件通过 `julia file.jl` 作为主脚本运行时，可能希望激活额外的功能，例如命令行参数处理。确定一个文件以这种方式运行的方法是检查 `abspath(PROGRAM_FILE) == @__FILE__` 是否为 `true`。

然而，建议不要编写既作为脚本又作为可导入库的文件。如果需要同时作为库和脚本可用的功能，最好将其编写为库，然后将功能导入到一个独立的脚本中。

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

运行 Julia 脚本使用 `julia file.jl` 时，在尝试用 CTRL-C (SIGINT) 终止它时不会抛出 [`InterruptException`](@ref)。要在终止 Julia 脚本之前运行某段代码（这可能是由 CTRL-C 引起的，也可能不是），请使用 [`atexit`](@ref)。或者，您可以使用 `julia -e 'include(popfirst!(ARGS))' file.jl` 来执行脚本，同时能够在 [`try`](@ref) 块中捕获 `InterruptException`。请注意，使用此策略时，[`PROGRAM_FILE`](@ref) 将不会被设置。

### How do I pass options to `julia` using `#!/usr/bin/env`?

在所谓的 shebang 行中将选项传递给 `julia`，例如 `#!/usr/bin/env julia --startup-file=no`，在许多平台（BSD、macOS、Linux）上将无法工作，因为内核与 shell 不同，不会在空格字符处拆分参数。选项 `env -S` 提供了一种简单的解决方法，它将单个参数字符串在空格处拆分为多个参数，类似于 shell：

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    选项 `env -S` 出现在 FreeBSD 6.0（2005 年）、macOS Sierra（2016 年）和 GNU/Linux coreutils 8.30（2018 年）。


### Why doesn't `run` support `*` or pipes for scripting external programs?

Julia的 [`run`](@ref) 函数直接启动外部程序，而不调用 [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing))（与其他语言如Python、R或C中的 `system("...")` 函数不同）。这意味着 `run` 不会对 `*` 进行通配符扩展 (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming)))，也不会像 `|` 或 `>` 那样解释 [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix))。

您仍然可以使用 Julia 特性进行通配符匹配和管道。例如，内置的 [`pipeline`](@ref) 函数允许您链接外部程序和文件，类似于 shell 管道，而 [Glob.jl package](https://github.com/vtjnash/Glob.jl) 实现了与 POSIX 兼容的通配符匹配。

您当然可以通过显式传递一个 shell 和一个命令字符串给 `run` 来通过 shell 运行程序，例如 ```run(`sh -c "ls > files.txt"`)``` 来使用 Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell)，但您通常应该更倾向于使用纯 Julia 脚本，例如 ```run(pipeline(`ls`, "files.txt"))```。我们默认避免使用 shell 的原因是 [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/)：通过 shell 启动进程速度慢，对特殊字符的引用脆弱，错误处理差，并且在可移植性方面存在问题。（Python 开发者也遇到了 [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation)。）

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

你可能有类似的内容：

```
x = 0
while x < 10
    x += 1
end
```

并注意到它在交互环境（如 Julia REPL）中运行良好，但在脚本或其他文件中运行时会给出 ```UndefVarError: `x` not defined```。发生这种情况是因为 Julia 通常要求你 **在局部作用域中明确地为全局变量赋值**。

这里，`x` 是一个全局变量，`while` 定义了一个 [local scope](@ref scope-of-variables)，而 `x += 1` 是对该局部作用域中的全局变量的赋值。

如上所述，Julia（版本 1.5 或更高）允许您在 REPL（以及许多其他交互式环境）中省略 `global` 关键字，以简化探索（例如，从函数中复制粘贴代码以进行交互式运行）。然而，一旦您转向文件中的代码，Julia 对全局变量的处理要求更加严格。您至少有三种选择：

1. 将代码放入一个函数中（这样 `x` 就是函数中的一个*局部*变量）。一般来说，使用函数而不是全局脚本是良好的软件工程实践（在线搜索“为什么全局变量不好”可以看到许多解释）。在 Julia 中，全局变量也是 [slow](@ref man-performance-tips)。
2. 将代码包裹在一个 [`let`](@ref) 块中。 （这使得 `x` 成为 `let ... end` 语句中的局部变量，再次消除了对 `global` 的需求）。
3. 在局部作用域内显式地将 `x` 标记为 `global`，然后再对其赋值，例如写 `global x += 1`。

更多的解释可以在手册部分 [on soft scope](@ref on-soft-scope) 找到。

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

假设你这样调用一个函数：

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

在 Julia 中，变量 `x` 的绑定不能通过将 `x` 作为参数传递给函数来改变。当在上述示例中调用 `change_value!(x)` 时，`y` 是一个新创建的变量，最初绑定到 `x` 的值，即 `10`；然后 `y` 被重新绑定到常量 `17`，而外部作用域的变量 `x` 保持不变。

然而，如果 `x` 绑定到一个类型为 `Array`（或任何其他 *可变* 类型）的对象。在函数内部，您无法将 `x` 从这个 Array 中“解绑”，但您 *可以* 更改其内容。例如：

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

在这里，我们创建了一个函数 `change_array!`，它将 `5` 赋值给传入数组的第一个元素（在调用位置绑定为 `x`，在函数内部绑定为 `A`）。请注意，在函数调用后，`x` 仍然绑定到同一个数组，但该数组的内容发生了变化：变量 `A` 和 `x` 是指向同一个可变 `Array` 对象的不同绑定。

### Can I use `using` or `import` inside a function?

不，您不允许在函数内部使用 `using` 或 `import` 语句。如果您想导入一个模块但只在特定函数或函数集内部使用它的符号，您有两个选择：

1. 使用 `import`：

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    这加载了模块 `Foo` 并定义了一个变量 `Foo`，该变量指向该模块，但并未将模块中的其他符号导入到当前命名空间中。你可以通过它们的限定名称 `Foo.bar` 等来引用 `Foo` 符号。
2. 将您的函数包装在一个模块中：

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    这将从 `Foo` 导入所有符号，但仅在模块 `Bar` 内部。

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

许多初学者在使用 Julia 时发现 `...` 运算符令人困惑。使 `...` 运算符令人困惑的部分原因在于，它在不同的上下文中有两种不同的含义。

#### `...` combines many arguments into one argument in function definitions

在函数定义的上下文中，`...` 运算符用于将许多不同的参数组合成一个单一的参数。将 `...` 用于将许多不同的参数组合成一个单一的参数的用法称为 slurping：

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

如果 Julia 是一种更自由使用 ASCII 字符的语言，那么吸取运算符可能会被写成 `<-...` 而不是 `...`。

#### `...` splits one argument into many different arguments in function calls

与使用 `...` 运算符在定义函数时将许多不同的参数合并为一个参数相对，`...` 运算符在函数调用的上下文中也用于将单个函数参数拆分为许多不同的参数。这种 `...` 的用法称为展开：

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

如果 Julia 是一种更自由使用 ASCII 字符的语言，展开运算符可能会被写成 `...->` 而不是 `...`。

### What is the return value of an assignment?

运算符 `=` 总是返回右侧的值，因此：

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

和类似地：

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

这意味着输出的类型可以从输入的类型中预测。特别是，这意味着输出的类型不能根据输入的*值*而变化。以下代码*不是*类型稳定的：

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

It returns either an `Int` or a [`Float64`](@ref) depending on the value of its argument. Since Julia can't predict the return type of this function at compile-time, any computation that uses it must be able to cope with values of both types, which makes it hard to produce fast machine code.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

某些操作在数学上是合理的，但会导致错误：

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

这种行为是对类型稳定性要求的不便后果。在 [`sqrt`](@ref) 的情况下，大多数用户希望 `sqrt(2.0)` 返回一个实数，如果它返回复数 `1.4142135623730951 + 0.0im`，用户会感到不满。可以编写 `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` 函数，使其仅在传入负数时切换到复数输出（这在其他一些语言中是 `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` 的做法），但这样结果就不会是 [type-stable](@ref man-type-stability)，而且 `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` 函数的性能会很差。

在这些和其他情况下，您可以通过选择一种*输入类型*来获得您想要的结果，这种输入类型传达了您愿意接受一种*输出类型*，其中结果可以被表示：

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

[parametric type](@ref Parametric-Types) 的参数可以容纳类型或位值，而类型本身选择如何使用这些参数。例如，`Array{Float64, 2}` 通过类型 `Float64` 参数化以表示其元素类型，并通过整数值 `2` 表示其维数。当定义您自己的参数化类型时，可以使用子类型约束声明某个参数必须是某个抽象类型或先前类型参数的子类型 ([`<:`](@ref))。然而，没有专门的语法来声明参数必须是给定类型的 *值* — 也就是说，您不能直接在 `struct` 定义中声明一个类似维度的参数 [`isa`](@ref) 为 `Int`。同样，您不能对类型参数进行计算（包括简单的加法或减法）。相反，这些约束和关系可以通过在类型的 [constructors](@ref man-constructors) 中计算和强制执行的额外类型参数来表达。

作为一个例子，考虑

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

用户希望强制第三个类型参数始终是第二个类型参数加一。这可以通过一个显式的类型参数来实现，该参数由一个 [inner constructor method](@ref man-inner-constructor-methods) 检查（可以与其他检查结合使用）：

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

此检查通常是 *无成本* 的，因为编译器可以省略对有效具体类型的检查。如果第二个参数也是计算得出的，提供一个 [outer constructor method](@ref man-outer-constructor-methods) 来执行此计算可能是有利的：

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

Julia 使用机器算术进行整数计算。这意味着 `Int` 值的范围是有限的，并且在两端会环绕，因此加、减和乘整数可能会溢出或下溢，导致一些结果在开始时可能会让人感到不安：

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

显然，这与数学整数的行为相去甚远，你可能会认为让高级编程语言将这一点暴露给用户并不理想。然而，对于效率和透明度至关重要的数值工作来说，其他选择更糟。

一个可以考虑的替代方案是检查每个整数操作是否溢出，并在溢出的情况下将结果提升到更大的整数类型，例如 [`Int128`](@ref) 或 [`BigInt`](@ref)。不幸的是，这在每个整数操作上引入了重大开销（想想递增循环计数器）——这需要在算术指令之后发出代码以执行运行时溢出检查，并分支以处理潜在的溢出。更糟糕的是，这将导致每个涉及整数的计算都变得类型不稳定。正如我们上面提到的，[type-stability is crucial](@ref man-type-stability) 用于有效生成高效代码。如果你不能依赖整数操作的结果是整数，那么就不可能像 C 和 Fortran 编译器那样生成快速、简单的代码。

这种方法的一个变体，避免了类型不稳定的表现，是将 `Int` 和 [`BigInt`](@ref) 类型合并为一个单一的混合整数类型，该类型在结果不再适合机器整数的大小时内部改变表示。虽然这在表面上避免了 Julia 代码层面的类型不稳定，但实际上只是将问题掩盖了，因为它将所有相同的困难转嫁给实现该混合整数类型的 C 代码。这种方法 *可以* 被实现，并且在许多情况下甚至可以变得相当快速，但也有几个缺点。一个问题是，整数和整数数组的内存表示不再与 C、Fortran 和其他具有本机机器整数的语言使用的自然表示相匹配。因此，为了与这些语言进行互操作，我们最终仍然需要引入本机整数类型。任何无界的整数表示都不能具有固定的位数，因此不能在线存储在具有固定大小插槽的数组中——大整数值总是需要单独的堆分配存储。而且，无论使用多么巧妙的混合整数实现，总会存在性能陷阱——性能意外下降的情况。复杂的表示、与 C 和 Fortran 的互操作性缺乏、无法在没有额外堆存储的情况下表示整数数组，以及不可预测的性能特征，使得即使是最聪明的混合整数实现也不适合高性能数值工作。

一种替代使用混合整数或提升到 BigInt 的方法是使用饱和整数算术，其中将最大整数值相加时保持不变，最小整数值相减时也保持不变。这正是 Matlab™ 所做的：

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

乍一看，这似乎是合理的，因为 9223372036854775807 离 9223372036854775808 更近，而 -9223372036854775808 离它更远，并且整数仍然以与 C 和 Fortran 兼容的自然方式以固定大小表示。然而，饱和整数算术却是深具问题的。第一个也是最明显的问题是，这并不是机器整数算术的工作方式，因此实现饱和操作需要在每个机器整数操作后发出指令，以检查下溢或上溢，并根据需要将结果替换为 [`typemin(Int)`](@ref) 或 [`typemax(Int)`](@ref)。仅此一项就将每个整数操作从单个快速指令扩展为半打指令，可能还包括分支。哎呀。但情况更糟——饱和整数算术不是结合的。考虑这个 Matlab 计算：

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

这使得编写许多基本整数算法变得困难，因为许多常见技术依赖于机器加法在溢出时 *是* 结合的。考虑在 Julia 中使用表达式 `(lo + hi) >>> 1` 来查找整数值 `lo` 和 `hi` 之间的中点：

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

看到了吗？没问题。这是2^62和2^63之间的正确中点，尽管`n + 2n`是-4611686018427387904。现在在Matlab中试试：

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

哎呀。在 Matlab 中添加 `>>>` 运算符是没有帮助的，因为在将 `n` 和 `2n` 相加时发生的饱和已经破坏了计算正确中点所需的信息。

缺乏结合性不仅对无法依赖它进行此类技术的程序员来说是不幸的，而且还破坏了编译器可能想要做的几乎所有优化整数算术的尝试。例如，由于Julia整数使用正常的机器整数算术，LLVM可以积极优化像`f(k) = 5k-1`这样的简单小函数。该函数的机器代码就是这样：

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

函数的实际主体是一个单独的 `leaq` 指令，它一次性计算整数乘法和加法。当 `f` 被内联到另一个函数中时，这一点更为有利：

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

由于对 `f` 的调用被内联，循环体最终只剩下一个 `leaq` 指令。接下来，考虑如果我们将循环迭代次数固定会发生什么：

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

因为编译器知道整数加法和乘法是结合的，并且乘法对加法是分配的——而饱和算术并不具备这些特性——它可以将整个循环优化为仅仅一个乘法和一个加法。饱和算术完全破坏了这种优化，因为在每次循环迭代中，结合性和分配性可能会失效，导致不同的结果，具体取决于失败发生在哪次迭代中。编译器可以展开循环，但它无法将多个操作代数上简化为更少的等效操作。

对整数算术运算静默溢出最合理的替代方案是在所有地方进行检查算术运算，当加法、减法和乘法溢出时引发错误，产生不正确的值。在这个 [blog post](https://danluu.com/integer-overflow/) 中，Dan Luu 分析了这一点，并发现与理论上这种方法应该具有的微不足道的成本相比，由于编译器（LLVM 和 GCC）未能优雅地优化添加的溢出检查，最终导致了相当大的成本。如果未来这一点有所改善，我们可以考虑在 Julia 中默认使用检查整数算术运算，但目前，我们必须接受溢出的可能性。

与此同时，可以通过使用外部库实现安全的整数溢出操作，例如 [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl)。请注意，如前所述，使用这些库会显著增加使用检查整数类型的代码的执行时间。然而，对于有限的使用情况，这远比用于所有整数操作要小得多的问题。您可以关注讨论的状态 [here](https://github.com/JuliaLang/julia/issues/855)。

### What are the possible causes of an `UndefVarError` during remote execution?

如错误所述，远程节点上 `UndefVarError` 的直接原因是不存在该名称的绑定。让我们探讨一些可能的原因。

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

闭包 `x->x` 持有对 `Foo` 的引用，由于在节点 2 上 `Foo` 不可用，因此抛出了 `UndefVarError`。

在 `Main` 以外的模块下的全局变量不会按值序列化到远程节点。只会发送一个引用。创建全局绑定的函数（除了在 `Main` 下）可能会导致后续抛出 `UndefVarError`。

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

在上述示例中，`@everywhere module Foo` 在所有节点上定义了 `Foo`。然而，调用 `Foo.foo()` 在本地节点上创建了一个新的全局绑定 `gvar`，但在节点 2 上未找到该绑定，导致出现 `UndefVarError` 错误。

请注意，这不适用于在模块 `Main` 下创建的全局变量。在模块 `Main` 下的全局变量会被序列化，并在远程节点上创建新的绑定。

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

这不适用于 `function` 或 `struct` 声明。然而，绑定到全局变量的匿名函数会被序列化，如下所示。

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

如您尝试此操作，将会看到结果是一个 `MethodError`：

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

这是因为 `Vector{Real}` 不是 `Vector{Int}` 的超类型！你可以通过类似 `foo(bar::Vector{T}) where {T<:Real}` 的方式解决这个问题（如果函数体内不需要静态参数 `T`，可以使用简短形式 `foo(bar::Vector{<:Real})`）。`T` 是一个通配符：你首先指定它必须是 Real 的子类型，然后指定函数接受一个该类型元素的 Vector。

这个问题同样适用于任何复合类型 `Comp`，不仅仅是 `Vector`。如果 `Comp` 声明了一个类型为 `Y` 的参数，那么另一个类型 `Comp2` 具有类型为 `X<:Y` 的参数就不是 `Comp` 的子类型。这是类型不变性（相比之下，元组在其参数中是类型协变的）。请参见 [Parametric Composite Types](@ref man-parametric-composite-types) 以获取更多解释。

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

[main argument](@ref man-concatenation) 对 `+` 的反对意见在于字符串连接不是交换的，而 `+` 通常被用作交换运算符。虽然 Julia 社区承认其他语言使用不同的运算符，并且 `*` 对某些用户可能不熟悉，但它传达了某些代数属性。

请注意，您还可以使用 `string(...)` 来连接字符串（以及转换为字符串的其他值）；类似地，可以使用 `repeat` 代替 `^` 来重复字符串。[interpolation syntax](@ref string-interpolation) 也有助于构造字符串。

## Packages and Modules

### What is the difference between "using" and "import"?

`using` 和 `import` 之间有几个区别（请参见 [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules)），但有一个重要的区别在初看时可能并不直观，从表面上看（即语法上）似乎非常微小。当使用 `using` 加载模块时，你需要说 `function Foo.bar(...` 来扩展模块 `Foo` 的函数 `bar`，但使用 `import Foo.bar` 时，你只需说 `function bar(...`，它会自动扩展模块 `Foo` 的函数 `bar`。

这之所以重要到需要单独的语法，是因为你不想意外地扩展一个你不知道存在的函数，因为这很容易导致错误。这种情况最有可能发生在一个接受常见类型（如字符串或整数）的方法上，因为你和其他模块都可能定义一个方法来处理这种常见类型。如果你使用 `import`，那么你将用你的新实现替换其他模块的 `bar(s::AbstractString)` 的实现，这可能会完全做一些不同的事情（并破坏模块 Foo 中所有/许多依赖于调用 bar 的其他函数的未来用法）。

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

与许多语言（例如 C 和 Java）不同，Julia 对象默认不能为“null”。当一个引用（变量、对象字段或数组元素）未初始化时，访问它会立即抛出错误。可以使用 [`isdefined`](@ref) 或 [`isassigned`](@ref Base.isassigned) 函数检测这种情况。

有些函数仅用于其副作用，而不需要返回值。在这些情况下，约定是返回值 `nothing`，这只是一个类型为 `Nothing` 的单例对象。这是一个普通类型，没有字段；除了这个约定之外，它没有什么特别之处，并且 REPL 不会为其打印任何内容。一些本来不会有值的语言构造也会产生 `nothing`，例如 `if false; end`。

对于值 `x` 类型 `T` 仅在某些情况下存在的情况，可以使用 `Union{T, Nothing}` 类型作为函数参数、对象字段和数组元素类型，相当于其他语言中的 [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type)。如果值本身可以是 `nothing`（特别是当 `T` 是 `Any` 时），则 `Union{Some{T}, Nothing}` 类型更为合适，因为 `x == nothing` 表示缺少值，而 `x == Some(nothing)` 表示存在一个等于 `nothing` 的值。[`something`](@ref) 函数允许解包 `Some` 对象，并使用默认值代替 `nothing` 参数。请注意，编译器能够在处理 `Union{T, Nothing}` 参数或字段时生成高效的代码。

要在统计意义上表示缺失数据（R 中的 `NA` 或 SQL 中的 `NULL`），请使用 [`missing`](@ref) 对象。有关更多详细信息，请参见 [`Missing Values`](@ref missing) 部分。

在某些语言中，空元组（`()`）被视为虚无的典范形式。然而，在Julia中，它最好被视为一个普通的元组，只是恰好包含零个值。

空类型（或称“底层”类型），写作 `Union{}`（一个空的联合类型），是一种没有值和子类型（除了它自己）的类型。通常情况下，您不需要使用这种类型。

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

在 Julia 中，`x += y` 在降低阶段被替换为 `x = x + y`。对于数组，这意味着它不会将结果存储在与 `x` 相同的内存位置，而是分配一个新的数组来存储结果。如果你更喜欢修改 `x`，请使用 `x .+= y` 来逐个更新每个元素。

虽然这种行为可能会让一些人感到惊讶，但这个选择是故意的。主要原因是Julia中存在不可变对象，一旦创建就无法更改其值。实际上，数字就是一个不可变对象；语句`x = 5; x += 1`并不修改`5`的含义，而是修改了绑定到`x`的值。对于不可变对象，改变值的唯一方法是重新赋值。

为了进一步放大，考虑以下函数：

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

在调用 `x = 5; y = power_by_squaring(x, 4)` 之后，你会得到预期的结果：`x == 5 && y == 625`。然而，现在假设 `*=` 在与矩阵一起使用时，会改变左侧的值。这将会有两个问题：

  * 对于一般的方阵，`A = A*B` 不能在没有临时存储的情况下实现：`A[1,1]` 在左侧计算并存储之前，您已经在右侧使用了它。
  * 假设你愿意为计算分配一个临时变量（这将消除大多数使得 `*=` 在原地工作意义的原因）；如果你利用了 `x` 的可变性，那么这个函数对于可变和不可变的输入会表现得不同。特别是，对于不可变的 `x`，在调用之后（一般来说）会有 `y != x`，但对于可变的 `x`，你会有 `y == x`。

因为支持泛型编程被认为比通过其他方式（例如，使用广播或显式循环）实现的潜在性能优化更重要，因此像 `+=` 和 `*=` 这样的运算符通过重新绑定新值来工作。

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

虽然流 I/O API 是同步的，但底层实现是完全异步的。

请考虑以下内容的打印输出：

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

这是因为，虽然 `write` 调用是同步的，但在等待 I/O 的那部分完成时，每个参数的写入会让出控制权给其他任务。

`print` 和 `println` 在调用期间“锁定”流。因此，将上面的示例中的 `write` 更改为 `println` 会导致：

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

您可以像这样使用 `ReentrantLock` 锁定您的写入：

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

零维数组是形式为 `Array{T,0}` 的数组。它们的行为类似于标量，但存在重要的区别。它们值得特别提及，因为它们是一个特殊情况，考虑到数组的通用定义是合乎逻辑的，但最初可能有点不直观。以下行定义了一个零维数组：

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

在这个例子中，`A` 是一个可变容器，包含一个元素，可以通过 `A[] = 1.0` 设置，并通过 `A[]` 检索。所有零维数组的大小相同（`size(A) == ()`），长度（`length(A) == 1`）。特别地，零维数组并不是空的。如果你觉得这不直观，这里有一些想法可能有助于理解 Julia 的定义。

  * 零维数组是向量的“线”和矩阵的“平面”的“点”。就像一条线没有面积（但仍然代表一组事物），一个点没有长度或任何维度（但仍然代表一个事物）。
  * 我们定义 `prod(())` 为 1，数组中元素的总数是大小的乘积。零维数组的大小是 `()`，因此它的长度是 `1`。
  * 零维数组本身没有任何可以索引的维度——它们只是 `A[]`。我们可以对它们应用与所有其他数组维度相同的“尾随一”规则，因此你确实可以将它们索引为 `A[1]`、`A[1,1]` 等；请参见 [Omitted and extra indices](@ref)。

理解普通标量的差异也很重要。标量不是可变容器（尽管它们是可迭代的，并定义了诸如 `length`、`getindex` 等东西，例如 `1[] == 1`）。特别是，如果 `x = 0.0` 被定义为标量，则尝试通过 `x[] = 1.0` 更改其值是错误的。标量 `x` 可以通过 `fill(x)` 转换为包含它的零维数组，反之，零维数组 `a` 可以通过 `a[]` 转换为包含的标量。另一个区别是，标量可以参与线性代数运算，例如 `2 * rand(2,2)`，但与零维数组 `fill(2) * rand(2,2)` 的类似运算是错误的。

### Why are my Julia benchmarks for linear algebra operations different from other languages?

您可能会发现，线性代数构建块的简单基准测试，例如

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

与其他语言如 Matlab 或 R 相比，可能会有所不同。

由于此类操作只是相关 BLAS 函数的非常薄的封装，因此差异的原因很可能是

1. 每种语言使用的 BLAS 库，
2. 并发线程的数量。

Julia 编译并使用其自己的 OpenBLAS 副本，当前线程限制为 `8`（或您的核心数量）。

修改 OpenBLAS 设置或使用不同的 BLAS 库编译 Julia，例如 [Intel MKL](https://software.intel.com/en-us/mkl)，可能会提供性能提升。您可以使用 [MKL.jl](https://github.com/JuliaComputing/MKL.jl)，这是一个使 Julia 的线性代数使用 Intel MKL BLAS 和 LAPACK 而不是 OpenBLAS 的包，或者在讨论论坛中搜索有关如何手动设置的建议。请注意，Intel MKL 不能与 Julia 一起捆绑，因为它不是开源的。

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

在高性能计算（HPC）设施中使用 Julia 时，建议使用共享仓库（通过 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 环境变量）。自 Julia v1.10 起，多个在功能上相似的工作进程使用相同的仓库将通过 pidfile 锁进行协调，以便仅在一个进程上花费时间进行预编译，而其他进程则等待。预编译过程将指示该进程是否正在进行预编译或等待另一个正在进行预编译的进程。如果是非交互式，则消息通过 `@debug` 发送。

然而，由于二进制代码的缓存，自 v1.9 以来，缓存拒绝变得更加严格，用户可能需要适当地设置 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 环境变量，以获得一个在整个 HPC 环境中可用的单一缓存。

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

Julia的稳定版本是最新发布的Julia版本，这是大多数人希望运行的版本。它具有最新的功能，包括性能改进。Julia的稳定版本根据[SemVer](https://semver.org/)进行版本控制，标记为v1.x.y。每隔大约4-5个月，在经过几周的测试作为发布候选后，会发布一个新的次要版本的Julia，以对应新的稳定版本。与LTS版本不同，稳定版本在发布另一个稳定版本的Julia后通常不会收到错误修复。然而，升级到下一个稳定版本始终是可能的，因为每个Julia v1.x的版本将继续运行为早期版本编写的代码。

如果您正在寻找一个非常稳定的代码库，您可能更喜欢 Julia 的 LTS（长期支持）版本。目前的 Julia LTS 版本根据 SemVer 版本为 v1.6.x；在选择新的 LTS 分支之前，该分支将继续接收错误修复，此时 v1.6.x 系列将不再定期接收错误修复，除了最保守的用户外，所有用户都将被建议升级到新的 LTS 版本系列。作为一个包开发者，您可能更倾向于为 LTS 版本开发，以最大化能够使用您包的用户数量。根据 SemVer，为 v1.0 编写的代码将继续适用于所有未来的 LTS 和稳定版本。一般来说，即使以 LTS 为目标，开发者也可以在最新的稳定版本中开发和运行代码，以利用性能的提升；只要避免使用新特性（例如新增的库函数或新方法）。

如果您希望利用语言的最新更新，并且不介意今天可用的版本偶尔无法正常工作，您可能会更喜欢 Julia 的夜间版本。顾名思义，夜间版本的发布大约每晚进行一次（具体取决于构建基础设施的稳定性）。一般来说，夜间发布是相对安全的——您的代码不会着火。然而，它们可能会有偶尔的回归或问题，这些问题在更彻底的预发布测试之前不会被发现。您可能希望针对夜间版本进行测试，以确保在发布之前捕捉到影响您用例的回归。

最后，您也可以考虑自己从源代码构建 Julia。这个选项主要适合那些对命令行感到舒适或有兴趣学习的人。如果这描述了您，您可能也会对阅读我们的 [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md) 感兴趣。

每种下载类型的链接可以在下载页面找到，网址为 [https://julialang.org/downloads/](https://julialang.org/downloads/)。请注意，并非所有版本的 Julia 都适用于所有平台。

### How can I transfer the list of installed packages after updating my version of Julia?

每个小版本的 Julia 都有其默认的 [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1)。因此，在安装新的小版本 Julia 后，您使用先前小版本添加的包将默认不可用。给定 Julia 版本的环境由 `.julia/environments/` 中与版本号匹配的文件 `Project.toml` 和 `Manifest.toml` 定义，例如 `.julia/environments/v1.3`。

如果您安装了新的次要版本的 Julia，例如 `1.4`，并希望在其默认环境中使用与之前版本（例如 `1.3`）相同的包，您可以将 `1.3` 文件夹中的 `Project.toml` 文件的内容复制到 `1.4`。然后，在新的 Julia 版本的会话中，通过输入键 `]` 进入“包管理模式”，并运行命令 [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate)。

此操作将从复制的文件中解析出一组与目标 Julia 版本兼容的可行包，并在适当的情况下安装或更新它们。如果您想要重现的不仅是包的集合，还有您在之前的 Julia 版本中使用的版本，您还应该在运行 Pkg 命令 `instantiate` 之前复制 `Manifest.toml` 文件。然而，请注意，包可能定义了兼容性约束，这可能会受到更改 Julia 版本的影响，因此您在 `1.3` 中拥有的确切版本集合可能不适用于 `1.4`。

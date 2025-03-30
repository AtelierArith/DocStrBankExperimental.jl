# More about types

如果你使用Julia一段时间，你会理解类型所扮演的基本角色。在这里，我们试图深入探讨，特别关注[Parametric Types](@ref)。

## Types and sets (and `Any` and `Union{}`/`Bottom`)

也许最容易通过集合来理解Julia的类型系统。虽然程序操作单个值，但类型指的是一组值。这与集合不同；例如，[`Set`](@ref) 的值本身就是一个单一的 `Set` 值。相反，类型描述了一组*可能*的值，表达了我们对拥有哪个值的不确定性。

一个 *具体* 类型 `T` 描述了值的集合，其直接标签由 [`typeof`](@ref) 函数返回，为 `T`。一个 *抽象* 类型描述了一些可能更大的值集合。

[`Any`](@ref) 描述了所有可能值的整个宇宙。 [`Integer`](@ref) 是 `Any` 的一个子集，包括 `Int`、[`Int8`](@ref) 和其他具体类型。在内部，Julia 还大量使用另一种类型，称为 `Bottom`，也可以写作 `Union{}`。这对应于空集合。

Julia 的类型支持集合论的标准操作：你可以通过 `T1 <: T2` 来询问 `T1` 是否是 `T2` 的“子集”（子类型）。同样，你可以使用 [`typeintersect`](@ref) 交集两个类型，使用 [`Union`](@ref) 取它们的并集，并使用 [`typejoin`](@ref) 计算一个包含它们并集的类型：

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

虽然这些操作看起来可能很抽象，但它们是Julia的核心。例如，方法调度是通过遍历方法列表中的项来实现的，直到找到一个参数元组的类型是方法签名的子类型。为了使这个算法有效，重要的是方法按其特异性进行排序，并且搜索从最特异的方法开始。因此，Julia还在类型上实现了部分顺序；这通过类似于`<:`的功能实现，但有一些下面将讨论的不同之处。

## UnionAll types

Julia的类型系统还可以表达*迭代联合*类型：对某个变量的所有值的类型的联合。这对于描述参数类型是必要的，因为某些参数的值是未知的。

例如，[`Array`](@ref) 有两个参数，如 `Array{Int,2}` 中所示。如果我们不知道元素类型，我们可以写成 `Array{T,2} where T`，这是所有 `T` 值的 `Array{T,2}` 的并集：`Union{Array{Int8,2}, Array{Int16,2}, ...}`。

这种类型由一个 `UnionAll` 对象表示，该对象包含一个变量（在此示例中为 `T`，类型为 `TypeVar`）和一个包装类型（在此示例中为 `Array{T,2}`）。

考虑以下方法：

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

签名 - 如在 [Function calls](@ref Function-calls) 中描述 - 的 `f3` 是一个 `UnionAll` 类型，包装了一个元组类型：`Tuple{typeof(f3), Array{T}} where T`。除了 `f4` 之外，其他都可以用 `a = [1,2]` 调用；除了 `f2` 之外，其他都可以用 `b = Any[1,2]` 调用。

让我们更仔细地看看这些类型：

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

这表明 `Array` 实际上命名了一个 `UnionAll` 类型。每个参数都有一个嵌套的 `UnionAll` 类型。语法 `Array{Int,2}` 等价于 `Array{Int}{2}`；在内部，每个 `UnionAll` 都是用特定的变量值逐个实例化的，从外到内。这为省略尾部类型参数赋予了自然的意义；`Array{Int}` 给出了一个等价于 `Array{Int,N} where N` 的类型。

`TypeVar` 本身不是一个类型，而应该被视为 `UnionAll` 类型结构的一部分。类型变量对其值有下限和上限（在字段 `lb` 和 `ub` 中）。符号 `name` 纯粹是装饰性的。在内部，`TypeVar` 是通过地址进行比较的，因此它们被定义为可变类型，以确保可以区分“不同”的类型变量。然而，按照惯例，它们不应该被修改。

可以手动构造 `TypeVar`：

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

有一些方便的版本，允许您省略除 `name` 符号之外的任何参数。

语法 `Array{T} where T<:Integer` 被降低为

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

因此，手动构造 `TypeVar` 是很少必要的（实际上，这应该避免）。

## Free variables

*自由* 类型变量的概念在类型系统中极为重要。我们说变量 `V` 在类型 `T` 中是自由的，如果 `T` 不包含引入变量 `V` 的 `UnionAll`。例如，类型 `Array{Array{V} where V<:Integer}` 没有自由变量，但其中的 `Array{V}` 部分确实有一个自由变量 `V`。

一个具有自由变量的类型在某种意义上并不是真正的类型。考虑类型 `Array{Array{T}} where T`，它指的是所有同质的数组的数组。内部类型 `Array{T}`，单独来看，似乎可以指任何类型的数组。然而，外部数组的每个元素必须具有*相同*的数组类型，因此 `Array{T}` 不能仅仅指任何旧的数组。可以说，`Array{T}` 实际上“出现”了多次，并且 `T` 在每次“出现”时必须具有相同的值。

因此，C API 中的函数 `jl_has_free_typevars` 非常重要。对于返回 true 的类型，在子类型化和其他类型函数中将不会给出有意义的答案。

## TypeNames

以下两种 [`Array`](@ref) 类型在功能上是等效的，但打印结果不同：

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

这些可以通过检查类型的 `name` 字段来区分，该字段是 `TypeName` 类型的对象：

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

在这种情况下，相关字段是 `wrapper`，它持有对用于创建新 `Array` 类型的顶级类型的引用。

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

[`Array`](@ref) 的 `wrapper` 字段指向自身，但对于 `Array{TV,NV}` 它指回类型的原始定义。

其他字段呢？`hash` 为每种类型分配一个整数。要检查 `cache` 字段，选择一个使用频率低于数组的类型是有帮助的。让我们首先创建我们自己的类型：

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

当你实例化一个参数化类型时，每个具体类型都会保存在类型缓存中（`MyType.body.body.name.cache`）。然而，包含自由类型变量的实例不会被缓存。

## Tuple types

元组类型构成了一个有趣的特殊情况。为了使调度在像 `x::Tuple` 这样的声明上工作，该类型必须能够容纳任何元组。让我们检查一下参数：

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

与其他类型不同，元组类型在其参数中是协变的，因此此定义允许 `Tuple` 匹配任何类型的元组：

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

然而，如果一个可变参数（`Vararg`）元组类型具有自由变量，它可以描述不同种类的元组：

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

注意，当 `T` 在 `Tuple` 类型中是自由的（即其绑定的 `UnionAll` 类型在 `Tuple` 类型之外），整个类型中只能有一个 `T` 值有效。因此，异构元组不匹配。

最后，值得注意的是 `Tuple{}` 是不同的：

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

“主要”元组类型是什么？

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

所以 `Tuple == Tuple{Vararg{Any}}` 确实是主要类型。

## Diagonal types

考虑类型 `Tuple{T,T} where T`。具有此签名的方法如下所示：

```julia
f(x::T, y::T) where {T} = ...
```

根据对 `UnionAll` 类型的通常解释，这个 `T` 涉及所有类型，包括 `Any`，因此这个类型应该等同于 `Tuple{Any,Any}`。然而，这种解释会导致一些实际问题。

首先，`T` 的值需要在方法定义内部可用。对于像 `f(1, 1.0)` 这样的调用，`T` 应该是什么并不明确。它可以是 `Union{Int,Float64}`，或者可能是 [`Real`](@ref)。直观上，我们期望声明 `x::T` 意味着 `T === typeof(x)`。为了确保这个不变性成立，我们需要在这个方法中满足 `typeof(x) === typeof(y) === T`。这意味着该方法只能对完全相同类型的参数进行调用。

事实证明，能够判断两个值是否具有相同类型是非常有用的（例如，这被提升系统使用），因此我们有多个理由希望对 `Tuple{T,T} where T` 有不同的解释。为了使这项工作得以进行，我们向子类型添加了以下规则：如果一个变量在协变位置出现多次，则它被限制为仅在具体类型范围内。 (“协变位置”意味着在变量的一个出现和引入它的 `UnionAll` 类型之间仅出现 `Tuple` 和 `Union` 类型。）这样的变量被称为“对角变量”或“具体变量”。

例如，`Tuple{T,T} where T` 可以被视为 `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}`，其中 `T` 取遍所有具体类型。这产生了一些有趣的子类型结果。例如，`Tuple{Real,Real}` 不是 `Tuple{T,T} where T` 的子类型，因为它包含一些类型，如 `Tuple{Int8,Int16}`，其中两个元素具有不同的类型。`Tuple{Real,Real}` 和 `Tuple{T,T} where T` 具有非平凡的交集 `Tuple{T,T} where T<:Real`。然而，`Tuple{Real}` *是* `Tuple{T} where T` 的子类型，因为在这种情况下，`T` 只出现一次，因此不是对角线的。

接下来考虑如下签名：

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

在这种情况下，`T` 在 `Array{T}` 内部处于不变位置。这意味着传递的任何类型的数组都明确地确定了 `T` 的值——我们称 `T` 具有 *相等约束*。因此，在这种情况下，对角线规则并不是特别必要，因为数组确定了 `T`，然后我们可以允许 `x` 和 `y` 是 `T` 的任何子类型。因此，出现在不变位置的变量从不被视为对角线。这种行为的选择略显争议——一些人认为这个定义应该写成

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

澄清 `x` 和 `y` 是否需要具有相同的类型。在这个版本的签名中，它们需要相同，或者我们可以引入一个第三个变量来表示 `y` 的类型，如果 `x` 和 `y` 可以具有不同的类型。

下一个复杂性是联合和对角变量的交互，例如。

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

考虑这个声明的含义。`y` 的类型是 `T`。那么 `x` 可以是相同的类型 `T`，或者是类型 [`Nothing`](@ref)。因此，以下所有调用都应该匹配：

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

这些例子告诉我们一些事情：当 `x` 是 `nothing::Nothing` 时，`y` 没有额外的约束。就好像方法签名中有 `y::Any`。实际上，我们有以下类型等价：

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

一般规则是：在协变位置上的具体变量如果在子类型算法中只*使用*一次，就表现得像不是具体的。当 `x` 的类型为 `Nothing` 时，我们不需要在 `Union{Nothing,T}` 中使用 `T`；我们只在第二个位置使用它。这自然源于观察到在 `Tuple{T} where T` 中，将 `T` 限制为具体类型没有区别；无论哪种方式，类型都等于 `Tuple{Any}`。

然而，出现在 *不变* 位置会使变量失去具体性，无论该变量的出现是否被使用。否则，类型的行为可能会根据它们所比较的其他类型而有所不同，从而使得子类型关系不具备传递性。例如，考虑

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

如果 `Union` 内部的 `T` 被忽略，那么 `T` 是具体的，答案是“假”，因为前两种类型不相同。但考虑一下

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

现在我们不能忽视 `Union` 中的 `T`（我们必须有 `T == Any`），所以 `T` 不是具体的，答案是“真”。这将使 `T` 的具体性依赖于其他类型，这是不可接受的，因为一个类型必须有明确的独立含义。因此，`T` 在 `Vector` 中的出现被认为在两种情况下都是有效的。

## Subtyping diagonal variables

对角变量的子类型算法有两个组成部分：(1) 识别变量出现，(2) 确保对角变量仅在具体类型上取值。

第一个任务是通过在环境中为每个变量保持计数器 `occurs_inv` 和 `occurs_cov`（在 `src/subtype.c` 中）来完成的，分别跟踪不变和协变出现的次数。当 `occurs_inv == 0 && occurs_cov > 1` 时，变量是对角的。

第二个任务是通过对变量的下界施加条件来完成的。当子类型算法运行时，它会缩小每个变量的范围（提高下界和降低上界），以跟踪子类型关系成立的变量值范围。当我们完成对一个对角线变量的 `UnionAll` 类型的主体的评估时，我们查看边界的最终值。由于变量必须是具体的，如果它的下界不能是某个具体类型的子类型，就会发生矛盾。例如，像 [`AbstractArray`](@ref) 这样的抽象类型不能是具体类型的子类型，但像 `Int` 这样的具体类型可以，而空类型 `Bottom` 也可以。如果下界未通过此测试，算法将停止并返回 `false`。

例如，在问题 `Tuple{Int,String} <: Tuple{T,T} where T` 中，我们推导出如果 `T` 是 `Union{Int,String}` 的超类型，则这将成立。然而，`Union{Int,String}` 是一个抽象类型，因此该关系不成立。

这个具体性测试是通过函数 `is_leaf_bound` 完成的。请注意，这个测试与 `jl_is_leaf_type` 略有不同，因为它也会对 `Bottom` 返回 `true`。目前这个函数是启发式的，并不能捕捉所有可能的具体类型。困难在于，某个下界是否具体可能依赖于其他类型变量下界的值。例如，`Vector{T}` 仅在 `T` 的上下界都等于 `Int` 时才等同于具体类型 `Vector{Int}`。我们尚未制定出一个完整的算法来解决这个问题。

## Introduction to the internal machinery

大多数处理类型的操作都可以在文件 `jltypes.c` 和 `subtype.c` 中找到。一个好的开始方式是观察子类型的实际操作。使用 `make debug` 构建 Julia，并在调试器中启动 Julia。[gdb debugging tips](@ref gdb-debugging-tips) 提供了一些可能有用的提示。

因为子类型代码在 REPL 中被广泛使用——因此该代码中的断点经常被触发——如果您做出以下定义，将是最简单的：

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

然后在 `jl_breakpoint` 中设置一个断点。一旦这个断点被触发，您可以在其他函数中设置断点。

作为热身，尝试以下内容：

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

我们可以通过尝试一个更复杂的案例来使其更有趣：

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

`type_morespecific` 函数用于在方法表中的函数上施加部分顺序（从最具体到最不具体）。具体性是严格的；如果 `a` 比 `b` 更具体，则 `a` 不等于 `b`，并且 `b` 也不比 `a` 更具体。

如果 `a` 是 `b` 的严格子类型，那么它会被自动认为是更具体的。从这里开始，`type_morespecific` 使用一些不太正式的规则。例如，`subtype` 对参数的数量敏感，但 `type_morespecific` 可能不敏感。特别是，`Tuple{Int,AbstractFloat}` 比 `Tuple{Integer}` 更具体，尽管它不是一个子类型。（在 `Tuple{Int,AbstractFloat}` 和 `Tuple{Integer,Float64}` 之间，两个都不比另一个更具体。）同样，`Tuple{Int,Vararg{Int}}` 不是 `Tuple{Integer}` 的子类型，但它被认为更具体。然而，`morespecific` 在长度上会获得额外的加分：特别是，`Tuple{Int,Int}` 比 `Tuple{Int,Vararg{Int}}` 更具体。

如果您正在调试方法的排序方式，定义函数可能会很方便：

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

这允许你测试元组类型 `a` 是否比元组类型 `b` 更具体。

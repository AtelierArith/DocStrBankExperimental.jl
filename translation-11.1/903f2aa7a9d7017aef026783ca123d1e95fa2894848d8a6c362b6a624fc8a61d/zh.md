# [Scoped Values](@id scoped-values)

作用域值在Julia中提供了动态作用域的实现。

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables) 是 Julia 中的默认行为。在词法作用域下，变量的作用域由程序的词法（文本）结构决定。在动态作用域下，变量绑定到程序执行期间最近赋值的值。


作用域值的状态依赖于程序的执行路径。这意味着对于一个作用域值，您可能会同时观察到多个不同的值。

!!! compat "Julia 1.11"
    Scoped values 在 Julia 1.11 中引入。在 Julia 1.8+ 中，可以通过包 ScopedValues.jl 获得兼容的实现。


在其最简单的形式中，您可以创建一个 [`ScopedValue`](@ref Base.ScopedValues.ScopedValue)，并使用默认值，然后使用 [`with`](@ref Base.ScopedValues.with) 或 [`@with`](@ref Base.ScopedValues.@with) 进入一个新的动态作用域。新的作用域将继承父作用域中的所有值（并递归地从所有外部作用域中继承），提供的作用域值将优先于先前的定义。

让我们首先看一个**词法**作用域的例子。一个 `let` 语句开始一个新的词法作用域，在这个作用域内，外部定义的 `x` 被内部定义所遮蔽。

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

在以下示例中，由于 Julia 使用词法作用域，`f` 的主体中的变量 `x` 指的是在全局作用域中定义的 `x`，而进入 `let` 作用域并不会改变 `f` 观察到的值。

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

现在使用 `ScopedValue` 我们可以使用 **动态** 作用域。

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

请注意，`ScopedValue` 的观察值依赖于程序的执行路径。

通常使用 `const` 变量指向一个作用域值是有意义的，并且您可以通过一次调用 `with` 来设置多个 `ScopedValue` 的值。

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues` 提供了 `with` 的宏版本。表达式 `@with var=>val expr` 在一个新的动态作用域中评估 `expr`，其中 `var` 被设置为 `val`。`@with var=>val expr` 等价于 `with(var=>val) do expr end`。然而，`with` 需要一个零参数的闭包或函数，这会导致额外的调用帧。作为一个例子，考虑以下函数 `f`：

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

如果您希望在动态作用域中运行 `f`，并将 `a` 设置为 `2`，则可以使用 `with`：

```julia
with(() -> f(10), a=>2)
```

然而，这需要将 `f` 包裹在一个零参数函数中。如果您希望避免额外的调用帧，那么您可以使用 `@with` 宏：

```julia
@with a=>2 f(10)
```

!!! note
    动态作用域在任务创建时由 [`Task`](@ref) 继承。动态作用域 **不** 会通过 `Distributed.jl` 操作传播。


在下面的示例中，我们在启动任务之前打开一个新的动态作用域。父任务和两个子任务同时观察同一作用域值的独立值。

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

作用域值在整个作用域内是常量，但您可以在作用域值中存储可变状态。请记住，在并发编程的上下文中，全球变量的常见注意事项仍然适用。

在存储对可变状态的引用于作用域值时也需要小心。您可能希望在进入新的动态作用域时显式地 [unshare mutable state](@ref unshare_mutable_state)。

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

在下面的示例中，我们使用作用域值在 web 应用程序中实现权限检查。在确定请求的权限后，进入一个新的动态作用域并设置作用域值 `LEVEL`。应用程序的其他部分可以查询作用域值，并将收到适当的值。其他替代方案，如任务本地存储和全局变量，并不适合这种传播；我们唯一的替代方案是通过整个调用链传递一个值。

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

为了访问作用域值的值，作用域值本身必须在（词法）作用域内。这意味着您最常希望将作用域值用作常量全局变量。

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

确实，可以将作用域值视为隐藏的函数参数。

这并不排除它们作为非全局变量的使用。

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

但在这些情况下，直接传递函数参数可能会更简单。

### Very many ScopedValues

如果你发现自己为一个给定模块创建了许多 `ScopedValue`，那么使用一个专门的结构体来保存它们可能更好。

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

`Scope` 使用持久字典。查找和插入的时间复杂度为 `O(log(32, n))`，在动态作用域进入时，会复制少量数据，而未更改的数据则在其他作用域之间共享。

`Scope` 对象本身并不是面向用户的，并且可能在未来的 Julia 版本中发生更改。

## Design inspiration

这个设计深受 [JEPS-429](https://openjdk.org/jeps/429) 的启发，而该设计又受到许多 Lisp 方言中动态作用域自由变量的启发。特别是 Interlisp-D 及其深绑定策略。

先前讨论的设计是上下文变量，例如 [PEPS-567](https://peps.python.org/pep-0567/)，并在 Julia 中实现为 [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl)。

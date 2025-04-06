# [Missing Values](@id missing)

Julia 提供了在统计意义上表示缺失值的支持。这适用于观察中某个变量没有可用值的情况，但理论上存在有效值。缺失值通过 [`missing`](@ref) 对象表示，该对象是类型 [`Missing`](@ref) 的单例实例。`missing` 等同于 [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) 和 [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling)，并在大多数情况下表现得像它们。

## Propagation of Missing Values

`missing` 值 *自动传播* 当传递给标准数学运算符和函数时。对于这些函数，关于一个操作数值的不确定性会引起对结果的不确定性。在实践中，这意味着涉及 `missing` 值的数学运算通常返回 `missing`：

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

由于 `missing` 是一个普通的 Julia 对象，因此此传播规则仅适用于选择实现此行为的函数。这可以通过以下方式实现：

  * 为类型为 `Missing` 的参数添加特定方法，
  * 接受这种类型的参数，并将它们传递给传播它们的函数（如标准数学运算符）。

包应该考虑在定义新函数时传播缺失值是否有意义，并在这种情况下适当地定义方法。将 `missing` 值传递给一个没有接受 `Missing` 类型参数的方法的函数会抛出 [`MethodError`](@ref)，就像对于任何其他类型一样。

不传播 `missing` 值的函数可以通过将它们包装在 [Missings.jl](https://github.com/JuliaData/Missings.jl) 包提供的 `passmissing` 函数中来实现。例如，`f(x)` 变为 `passmissing(f)(x)`。

## Equality and Comparison Operators

标准的相等和比较运算符遵循上述传播规则：如果任何一个操作数是 `missing`，结果就是 `missing`。以下是一些示例：

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

特别注意，`missing == missing` 返回 `missing`，因此不能使用 `==` 来测试一个值是否缺失。要测试 `x` 是否为 `missing`，请使用 [`ismissing(x)`](@ref)。

特殊比较运算符 [`isequal`](@ref) 和 [`===`](@ref) 是传播规则的例外。即使在存在 `missing` 值的情况下，它们也会始终返回 `Bool` 值，将 `missing` 视为等于 `missing`，并与任何其他值不同。因此，它们可以用于测试一个值是否为 `missing`：

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

[`isless`](@ref) 运算符是另一个例外：`missing` 被视为大于任何其他值。这个运算符被 [`sort!`](@ref) 使用，因此将 `missing` 值放在所有其他值之后：

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

逻辑（或布尔）运算符 [`|`](@ref)、[`&`](@ref) 和 [`xor`](@ref) 是另一种特殊情况，因为它们仅在逻辑上需要时传播 `missing` 值。对于这些运算符，结果是否不确定取决于特定的操作。这遵循了 [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic) 的成熟规则，这些规则在 SQL 中由 `NULL` 和在 R 中由 `NA` 实现。这个抽象定义对应于一种相对自然的行为，最好通过具体示例来解释。

让我们用逻辑“或”运算符 [`|`](@ref) 来说明这个原则。根据布尔逻辑的规则，如果其中一个操作数为 `true`，另一个操作数的值对结果没有影响，结果将始终为 `true`：

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

基于这一观察，我们可以得出结论：如果一个操作数为 `true` 而另一个为 `missing`，我们知道结果为 `true`，尽管对其中一个操作数的实际值存在不确定性。如果我们能够观察到第二个操作数的实际值，它只能是 `true` 或 `false`，在这两种情况下，结果都是 `true`。因此，在这个特定情况下，缺失性并不会 *传播*：

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

相反，如果其中一个操作数为 `false`，则结果可能是 `true` 或 `false`，这取决于另一个操作数的值。因此，如果该操作数是 `missing`，结果也必须是 `missing`：

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

逻辑“与”运算符 [`&`](@ref) 的行为类似于 `|` 运算符，不同之处在于当其中一个操作数为 `false` 时，缺失值不会传播。例如，当第一个操作数为 `false` 时：

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

另一方面，当其中一个操作数为 `true` 时，缺失值会传播，例如第一个：

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

最后，“异或”逻辑运算符 [`xor`](@ref) 始终传播 `missing` 值，因为两个操作数始终对结果产生影响。还要注意，否定运算符 [`!`](@ref) 在操作数为 `missing` 时返回 `missing`，就像其他一元运算符一样。

## Control Flow and Short-Circuiting Operators

控制流运算符包括 [`if`](@ref)、[`while`](@ref) 和 [ternary operator](@ref man-conditional-evaluation) `x ? y : z` 不允许缺失值。这是因为我们无法确定如果能够观察到实际值，它是 `true` 还是 `false`。这意味着我们不知道程序应该如何行为。在这种情况下，一旦在此上下文中遇到 `missing` 值，就会抛出 [`TypeError`](@ref)。

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

出于同样的原因，与上述逻辑运算符相反，短路布尔运算符 [`&&`](@ref) 和 [`||`](@ref) 在操作数的值决定是否评估下一个操作数的情况下，不允许存在 `missing` 值。例如：

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

相反，当结果可以在没有 `missing` 值的情况下确定时，不会抛出错误。这种情况发生在代码在评估 `missing` 操作数之前短路时，以及当 `missing` 操作数是最后一个操作数时：

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

包含缺失值的数组可以像其他数组一样创建：

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

如这个例子所示，这种数组的元素类型是 `Union{Missing, T}`，其中 `T` 是非缺失值的类型。这反映了数组条目可以是类型 `T`（这里是 `Int64`）或类型 `Missing`。这种数组使用一种高效的内存存储，相当于一个 `Array{T}` 来保存实际值，结合一个 `Array{UInt8}` 来指示条目的类型（即它是 `Missing` 还是 `T`）。

可以使用标准语法构造允许缺失值的数组。使用 `Array{Union{Missing, T}}(missing, dims)` 创建填充缺失值的数组：

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    使用 `undef` 或 `similar` 可能会当前给出一个填充了 `missing` 的数组，但这并不是获得此类数组的正确方法。请使用上面所示的 `missing` 构造函数。


一个允许 `missing` 条目的元素类型的数组（例如 `Vector{Union{Missing, T}}`）如果不包含任何 `missing` 条目，可以使用 [`convert`](@ref) 转换为不允许 `missing` 条目的数组类型（例如 `Vector{T}`）。如果数组包含 `missing` 值，在转换过程中会抛出 `MethodError`：

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

由于 `missing` 值在标准数学运算符中会传播，因此当在包含缺失值的数组上调用归约函数时，它们会返回 `missing`：

```jldoctest
julia> sum([1, missing])
missing
```

在这种情况下，使用 [`skipmissing`](@ref) 函数来跳过缺失值：

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

这个便利函数返回一个迭代器，它有效地过滤掉 `missing` 值。因此，它可以与任何支持迭代器的函数一起使用：

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

通过在数组上调用 `skipmissing` 创建的对象可以使用来自父数组的索引进行索引。对应于缺失值的索引对于这些对象无效，尝试使用它们时会抛出错误（它们也会被 `keys` 和 `eachindex` 跳过）：

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

这允许操作于索引的函数与 `skipmissing` 结合使用。这尤其适用于搜索和查找函数。这些函数返回对 `skipmissing` 返回的对象有效的索引，并且也是*在父数组*中匹配条目的索引：

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

使用 [`collect`](@ref) 提取非 `missing` 值并将它们存储在一个数组中：

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

上述描述的三值逻辑也适用于应用于数组的逻辑函数。因此，使用 [`==`](@ref) 运算符的数组相等性测试在无法确定结果的情况下会返回 `missing`，而不需要知道 `missing` 条目的实际值。实际上，这意味着如果被比较数组的所有非缺失值相等，但一个或两个数组包含缺失值（可能在不同的位置），则返回 `missing`：

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

对于单个值，使用 [`isequal`](@ref) 将 `missing` 值视为与其他 `missing` 值相等，但与非 `missing` 值不同：

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

函数 [`any`](@ref) 和 [`all`](@ref) 也遵循三值逻辑的规则。因此，当结果无法确定时返回 `missing`：

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```

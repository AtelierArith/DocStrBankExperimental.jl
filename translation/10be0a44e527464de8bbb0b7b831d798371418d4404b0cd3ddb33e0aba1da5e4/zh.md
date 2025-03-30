```
=
```

`=` 是赋值运算符。

  * 对于变量 `a` 和表达式 `b`，`a = b` 使 `a` 指向 `b` 的值。
  * 对于函数 `f(x)`，`f(x) = x` 定义了一个新的函数常量 `f`，或者如果 `f` 已经定义，则向 `f` 添加一个新方法；这种用法等同于 `function f(x); x; end`。
  * `a[i] = v` 调用 [`setindex!`](@ref)`(a,v,i)`。
  * `a.b = c` 调用 [`setproperty!`](@ref)`(a,:b,c)`。
  * 在函数调用内部，`f(a=b)` 将 `b` 作为关键字参数 `a` 的值传递。
  * 在带逗号的括号内，`(a=1,)` 构造一个 [`NamedTuple`](@ref)。

# 示例

将 `a` 赋值为 `b` 并不会创建 `b` 的副本；相反，使用 [`copy`](@ref) 或 [`deepcopy`](@ref)。

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

传递给函数的集合也不会被复制。函数可以修改（变更）其参数所指向对象的内容。（执行此操作的函数名称通常以 '!' 结尾。）

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generic function with 1 method)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

赋值可以并行操作多个变量，从可迭代对象中获取值：

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

赋值可以串行操作多个变量，并将返回最右侧表达式的值：

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

在越界索引处的赋值不会扩展集合。如果集合是 [`Vector`](@ref)，则可以使用 [`push!`](@ref) 或 [`append!`](@ref) 来扩展。

```jldoctest
julia> a = [1, 1]; a[3] = 2
ERROR: BoundsError: attempt to access 2-element Array{Int64, 1} at index [3]
[...]

julia> push!(a, 2, 3)
4-element Array{Int64, 1}:
 1
 1
 2
 3

```

赋值 `[]` 不会从集合中删除元素；相反，使用 [`filter!`](@ref)。

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
ERROR: DimensionMismatch: tried to assign 0 elements to 1 destinations
[...]

julia> filter!(x -> x > 1, a) # in-place & thus more efficient than a = a[a .> 1]
2-element Array{Int64, 1}:
 2
 3

```

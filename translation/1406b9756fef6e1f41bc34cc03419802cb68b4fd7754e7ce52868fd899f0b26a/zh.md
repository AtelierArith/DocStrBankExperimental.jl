```
Ref{T}
```

一个安全引用类型为 `T` 的数据的对象。该类型保证指向有效的、由 Julia 分配的正确类型的内存。只要 `Ref` 本身被引用，底层数据就会受到垃圾收集器的保护，避免被释放。

在 Julia 中，`Ref` 对象通过 `[]` 进行解引用（加载或存储）。

创建一个指向类型为 `T` 的值 `x` 的 `Ref` 通常写作 `Ref(x)`。此外，对于创建指向容器（如 Array 或 Ptr）的内部指针，可以写作 `Ref(a, i)`，用于创建对 `a` 的第 `i` 个元素的引用。

`Ref{T}()` 创建一个未初始化的类型为 `T` 的值的引用。对于位类型 `T`，该值将是当前在分配的内存中存在的任何内容。对于非位类型 `T`，引用将是未定义的，尝试解引用将导致错误，"UndefRefError: access to undefined reference"。

要检查一个 `Ref` 是否是未定义的引用，可以使用 [`isassigned(ref::RefValue)`](@ref)。例如，如果 `T` 不是位类型，则 `isassigned(Ref{T}())` 为 `false`。如果 `T` 是位类型，则 `isassigned(Ref{T}())` 将始终为 true。

当作为 `ccall` 参数传递（作为 `Ptr` 或 `Ref` 类型）时，`Ref` 对象将被转换为指向其引用的数据的本机指针。对于大多数 `T`，或者当转换为 `Ptr{Cvoid}` 时，这是指向对象数据的指针。当 `T` 是 `isbits` 类型时，该值可以安全地被修改，否则修改将严格是未定义行为。

作为特例，设置 `T = Any` 将导致在转换为 `Ptr{Any}` 时创建指向引用本身的指针（如果 T 是不可变的，则为 `jl_value_t const* const*`，否则为 `jl_value_t *const *`）。当转换为 `Ptr{Cvoid}` 时，它仍将返回指向数据区域的指针，与任何其他 `T` 相同。

可以将 `Ptr` 的 `C_NULL` 实例传递给 `ccall` 的 `Ref` 参数以初始化它。

# 在广播中的使用

`Ref` 有时在广播中使用，以将引用的值视为标量。

# 示例

```jldoctest
julia> r = Ref(5) # 创建一个具有初始值的 Ref
Base.RefValue{Int64}(5)

julia> r[] # 从 Ref 获取值
5

julia> r[] = 7 # 在 Ref 中存储新值
7

julia> r # Ref 现在包含 7
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # 在广播期间将引用值视为标量
3-element BitVector:
 1
 0
 0

julia> Ref{Function}()  # 对非位类型 Function 的未定义引用
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # 解引用未定义引用将导致错误
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # 对位类型的引用如果未给出则引用一个未确定的值

julia> isassigned(Ref{Int64}()) # 对位类型的引用始终被赋值
true
```

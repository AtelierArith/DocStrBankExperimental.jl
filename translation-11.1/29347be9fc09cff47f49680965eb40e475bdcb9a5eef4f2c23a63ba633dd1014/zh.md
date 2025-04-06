`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle` 是与 `AbstractArray` 类型相关的任何样式的抽象超类型。`N` 参数是维度，这对于仅支持特定维度的 AbstractArray 类型非常方便：

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

对于支持任意维度的 `AbstractArray` 类型，`N` 可以设置为 `Any`：

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

在您希望能够混合多个 `AbstractArrayStyle` 并跟踪维度的情况下，您的样式需要支持 [`Val`](@ref) 构造函数：

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

请注意，如果两个或多个 `AbstractArrayStyle` 子类型发生冲突，广播机制将回退到生成 `Array`。如果这不可取，您可能需要定义二元 [`BroadcastStyle`](@ref) 规则来控制输出类型。

另请参见 [`Broadcast.DefaultArrayStyle`](@ref)。

```
x::EscapeInfo
```

一个用于逃逸信息的格，它具有以下属性：

  * `x.Analyzed::Bool`：并不是格的正式部分，仅指示 `x` 是否已被分析
  * `x.ReturnEscape::Bool`：指示 `x` 可以通过返回逃逸到调用者
  * `x.ThrownEscape::BitSet`：记录 `x` 可以作为异常抛出的 SSA 语句编号：

      * `isempty(x.ThrownEscape)`：`x` 在此调用帧中永远不会被抛出（底部）
      * `pc ∈ x.ThrownEscape`：`x` 可能在 `pc` 的 SSA 语句处被抛出
      * `-1 ∈ x.ThrownEscape`：`x` 可能在此调用帧的任意点被抛出（顶部）

    这些信息将被 `escape_exception!` 用于通过异常传播潜在的逃逸。
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`：维护所有可能被别名化为 `x` 的字段或数组元素的值：

      * `x.AliasInfo === false` 表示 `x` 的字段/元素尚未被分析
      * `x.AliasInfo === true` 表示 `x` 的字段/元素无法被分析，例如 `x` 的类型未知或不具体，因此其字段/元素无法被精确知道
      * `x.AliasInfo::IndexableFields` 记录所有可能被别名化为对象 `x` 字段的值，并具有精确的索引信息
      * `x.AliasInfo::IndexableElements` 记录所有可能被别名化为数组 `x` 元素的值，并具有精确的索引信息
      * `x.AliasInfo::Unindexable` 记录所有可能被别名化为 `x` 的字段/元素的值，但没有精确的索引信息
  * `x.Liveness::BitSet`：记录 `x` 应该是活跃的 SSA 语句编号，例如，用作调用参数、返回给调用者或为 `:foreigncall` 保留：

      * `isempty(x.Liveness)`：`x` 在此调用帧中从未被使用（底部）
      * `0 ∈ x.Liveness` 也具有特殊含义，即它是当前分析的调用帧的调用参数（因此它从调用者那里立即可见）。
      * `pc ∈ x.Liveness`：`x` 可能在 `pc` 的 SSA 语句处被使用
      * `-1 ∈ x.Liveness`：`x` 可能在此调用帧的任意点被使用（顶部）

有实用的构造函数来创建常见的 `EscapeInfo`，例如：

  * `NoEscape()`：此格的底部（类似）元素，意味着它不会逃逸到任何地方
  * `AllEscape()`：此格的最顶部元素，意味着它会逃逸到任何地方

`analyze_escapes` 将这些元素从底部过渡到顶部，方向与 Julia 的原生类型推断例程相同。一个抽象状态将使用底部（类似）元素进行初始化：

  * 调用参数初始化为 `ArgEscape()`，其 `Liveness` 属性包括 `0`，以指示它作为调用参数传递并立即从调用者可见
  * 其他状态初始化为 `NotAnalyzed()`，这是一个特殊的格元素，略低于 `NoEscape`，但同时不代表任何意义，除了它尚未被分析（因此它并不是格的正式部分）

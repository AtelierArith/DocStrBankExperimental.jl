一个 [`Face`](@ref) 是用于显示文本的图形属性的集合。Faces 控制文本在终端以及可能的其他地方的显示方式。

大多数情况下，一个 [`Face`](@ref) 将作为与 *face name* 符号的唯一关联存储在全局 faces 字典中，并且通常会通过这个名称而不是 [`Face`](@ref) 对象本身来引用。

# 属性

所有属性都可以通过关键字构造函数设置，默认值为 `nothing`。

  * `height`（一个 `Int` 或 `Float64`）：高度，以十分之一磅（当为 `Int` 时）或作为基本大小的因子（当为 `Float64` 时）。
  * `weight`（一个 `Symbol`）：从最细到最粗的符号之一 `:thin`、`:extralight`、`:light`、`:semilight`、`:normal`、`:medium`、`:semibold`、`:bold`、`:extrabold` 或 `:black`。在终端中，任何大于 `:normal` 的权重都显示为粗体，而在支持可变亮度文本的终端中，任何小于 `:normal` 的权重都显示为细体。
  * `slant`（一个 `Symbol`）：符号之一 `:italic`、`:oblique` 或 `:normal`。
  * `foreground`（一个 `SimpleColor`）：文本前景色。
  * `background`（一个 `SimpleColor`）：文本背景色。
  * `underline`，文本下划线，可以采取以下形式之一：

      * 一个 `Bool`：文本是否应该被下划线。
      * 一个 `SimpleColor`：文本应该用此颜色下划线。
      * 一个 `Tuple{Nothing, Symbol}`：文本应该使用符号设置的样式下划线，样式之一为 `:straight`、`:double`、`:curly`、`:dotted` 或 `:dashed`。
      * 一个 `Tuple{SimpleColor, Symbol}`：文本应该用指定的 SimpleColor 下划线，并使用之前指定的符号样式。
  * `strikethrough`（一个 `Bool`）：文本是否应该被划线。
  * `inverse`（一个 `Bool`）：前景色和背景色是否应该被反转。
  * `inherit`（一个 `Vector{Symbol}`）：要继承的 faces 名称，较早的 faces 优先。所有 faces 都继承自 `:default` face。

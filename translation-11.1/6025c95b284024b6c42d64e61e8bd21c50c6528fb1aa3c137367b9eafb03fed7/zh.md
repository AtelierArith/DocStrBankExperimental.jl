# Noteworthy Differences from other Languages

## Noteworthy differences from MATLAB

尽管MATLAB用户可能会发现Julia的语法熟悉，但Julia并不是MATLAB的克隆。两者之间存在主要的语法和功能差异。以下是一些值得注意的差异，这些差异可能会让习惯于MATLAB的Julia用户感到困惑：

  * Julia 数组使用方括号进行索引，`A[i,j]`。
  * Julia 数组在赋值给另一个变量时不会被复制。在 `A = B` 之后，改变 `B` 的元素也会修改 `A`。为了避免这种情况，请使用 `A = copy(B)`。
  * Julia 的值在传递给函数时不会被复制。如果一个函数修改了一个数组，变化将在调用者中可见。
  * Julia 不会在赋值语句中自动扩展数组。而在 MATLAB 中，`a(4) = 3.2` 可以创建数组 `a = [0 0 0 3.2]`，而 `a(5) = 7` 可以将其扩展为 `a = [0 0 0 3.2 7]`，对应的 Julia 语句 `a[5] = 7` 如果 `a` 的长度小于 5 或者该语句是标识符 `a` 的第一次使用，则会抛出错误。Julia 有 [`push!`](@ref) 和 [`append!`](@ref)，它们比 MATLAB 的 `a(end+1) = val` 更有效地扩展 `Vector`。
  * 虚数单位 `sqrt(-1)` 在 Julia 中表示为 [`im`](@ref)，而不是像 MATLAB 中的 `i` 或 `j`。
  * 在 Julia 中，没有小数点的字面数字（例如 `42`）会创建整数而不是浮点数。因此，如果某些操作期望一个浮点数，则可能会抛出域错误；例如，`julia> a = -1; 2^a` 会抛出域错误，因为结果不是一个整数（有关详细信息，请参见 [the FAQ entry on domain errors](@ref faq-domain-errors)）。
  * 在Julia中，多个值以元组的形式返回并赋值，例如`(a, b) = (1, 2)`或`a, b = 1, 2`。MATLAB的`nargout`，通常用于根据返回值的数量进行可选操作，在Julia中并不存在。相反，用户可以使用可选参数和关键字参数来实现类似的功能。
  * 朱莉亚拥有真正的一维数组。列向量的大小为 `N`，而不是 `Nx1`。例如，[`rand(N)`](@ref) 生成一个一维数组。
  * 在 Julia 中，`[x,y,z]` 将始终构造一个包含 `x`、`y` 和 `z` 的 3 元素数组。

      * 在第一个（“垂直”）维度中连接使用 [`vcat(x,y,z)`](@ref) 或用分号分隔（`[x; y; z]`）。
      * 要在第二个（“水平”）维度上连接，可以使用 [`hcat(x,y,z)`](@ref) 或用空格分隔（`[x y z]`）。
      * 要构造块矩阵（在前两个维度上连接），可以使用 [`hvcat`](@ref) 或者结合空格和分号（`[a b; c d]`）。
  * 在 Julia 中，`a:b` 和 `a:b:c` 构造 `AbstractRange` 对象。要像在 MATLAB 中那样构造一个完整的向量，请使用 [`collect(a:b)`](@ref)。通常情况下，不需要调用 `collect`。`AbstractRange` 对象在大多数情况下会像普通数组一样工作，但由于它懒惰地计算其值，因此更高效。这种创建专用对象而不是完整数组的模式被频繁使用，并且在诸如 [`range`](@ref) 的函数中，或与迭代器如 `enumerate` 和 `zip` 一起使用。特殊对象大多数情况下可以像普通数组一样使用。
  * 在Julia中，函数从其最后一个表达式或`return`关键字返回值，而不是在函数定义中列出要返回的变量名称（有关详细信息，请参见[The return Keyword](@ref)）。
  * 一个 Julia 脚本可以包含任意数量的函数，所有定义在文件加载时都会对外可见。函数定义可以从当前工作目录之外的文件中加载。
  * 在 Julia 中，当使用单个参数调用时，例如 `sum(A)`，即使 `A` 具有多个维度，像 [`sum`](@ref)、[`prod`](@ref) 和 [`maximum`](@ref) 这样的归约操作会对数组的每个元素执行。
  * 在Julia中，调用一个没有参数的函数时必须使用括号，例如在[`rand()`](@ref)中。
  * Julia 不鼓励在语句末尾使用分号。语句的结果不会自动打印（除非在交互提示符下），代码行不需要以分号结束。 [`println`](@ref) 或 [`@printf`](@ref) 可用于打印特定输出。
  * 在 Julia 中，如果 `A` 和 `B` 是数组，逻辑比较操作如 `A == B` 不会返回布尔数组。相反，使用 `A .== B`，其他布尔运算符也类似，如 [`<`](@ref)，[`>`](@ref)。
  * 在Julia中，运算符 [`&`](@ref)、[`|`](@ref) 和 [`⊻`](@ref xor)（[`xor`](@ref)）分别执行与MATLAB中 `and`、`or` 和 `xor` 相当的按位操作，并且具有类似于Python的按位运算符的优先级（与C不同）。它们可以对标量进行操作或在数组中逐元素操作，并可以用于组合逻辑数组，但请注意运算顺序的差异：可能需要使用括号（例如，要选择 `A` 中等于1或2的元素，请使用 `(A .== 1) .| (A .== 2)`）。
  * 在 Julia 中，集合的元素可以使用展开运算符 `...` 作为参数传递给函数，例如 `xs=[1,2]; f(xs...)`。
  * Julia的 [`svd`](@ref) 返回奇异值作为向量，而不是作为稠密对角矩阵。
  * 在 Julia 中，`...` 并不用于继续代码行。相反，不完整的表达式会自动继续到下一行。
  * 在Julia和MATLAB中，变量`ans`被设置为在交互式会话中发出的最后一个表达式的值。在Julia中，与MATLAB不同，当在非交互模式下运行Julia代码时，`ans`不会被设置。
  * Julia的`struct`不支持在运行时动态添加字段，这与MATLAB的`class`不同。相反，使用一个[`Dict`](@ref)。在Julia中，Dict是无序的。
  * 在Julia中，每个模块都有自己的全局作用域/命名空间，而在MATLAB中只有一个全局作用域。
  * 在 MATLAB 中，删除不需要的值的惯用方法是使用逻辑索引，例如表达式 `x(x>3)` 或语句 `x(x>3) = []` 来就地修改 `x`。相比之下，Julia 提供了高阶函数 [`filter`](@ref) 和 [`filter!`](@ref)，允许用户写 `filter(z->z>3, x)` 和 `filter!(z->z>3, x)` 作为对应的音译 `x[x.>3]` 和 `x = x[x.>3]` 的替代方案。使用 `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` 减少了临时数组的使用。
  * 提取（或“解引用”）单元数组中所有元素的类似操作，例如在 MATLAB 中的 `vertcat(A{:})`，在 Julia 中使用展开运算符编写，例如 `vcat(A...)`。
  * 在Julia中，`adjoint`函数执行共轭转置；在MATLAB中，`adjoint`提供“伴随”或经典伴随，即余子式矩阵的转置。
  * 在Julia中，a^b^c被计算为a^(b^c)，而在MATLAB中则是(a^b)^c。

## Noteworthy differences from R

Julia的目标之一是提供一种有效的数据分析和统计编程语言。对于从R转向Julia的用户，这里有一些值得注意的区别：

  * Julia 的单引号用于包围字符，而不是字符串。
  * Julia 可以通过索引字符串来创建子字符串。在 R 中，字符串必须先转换为字符向量，然后才能创建子字符串。
  * 在Julia中，像Python一样但与R不同，字符串可以使用三重引号 `""" ... """` 创建。这种语法方便构造包含换行符的字符串。
  * 在Julia中，变长参数使用展开运算符 `...` 指定，该运算符总是跟在特定变量的名称后面，这与R不同，在R中 `...` 可以单独出现。
  * 在Julia中，模运算是`mod(a, b)`，而不是`a %% b`。`%`在Julia中是余数运算符。
  * Julia使用方括号构造向量。Julia的`[1, 2, 3]`相当于R的`c(1, 2, 3)`。
  * 在Julia中，并非所有数据结构都支持逻辑索引。此外，Julia中的逻辑索引仅支持与被索引对象长度相等的向量。例如：

      * 在 R 中，`c(1, 2, 3, 4)[c(TRUE, FALSE)]` 等价于 `c(1, 3)`。
      * 在 R 中，`c(1, 2, 3, 4)[c(TRUE, FALSE, TRUE, FALSE)]` 等价于 `c(1, 3)`。
      * 在 Julia 中，`[1, 2, 3, 4][[true, false]]` 会抛出一个 [`BoundsError`](@ref)。
      * 在 Julia 中，`[1, 2, 3, 4][[true, false, true, false]]` 产生 `[1, 3]`。
  * 像许多语言一样，Julia 并不总是允许对不同长度的向量进行操作，而 R 只需要向量共享一个公共索引范围。例如，`c(1, 2, 3, 4) + c(1, 2)` 在 R 中是有效的，但等效的 `[1, 2, 3, 4] + [1, 2]` 在 Julia 中会抛出错误。
  * Julia 允许在不改变代码含义的情况下使用可选的尾随逗号。这可能会导致 R 用户在索引数组时感到困惑。例如，R 中的 `x[1,]` 会返回矩阵的第一行；然而在 Julia 中，逗号会被忽略，因此 `x[1,] == x[1]`，并将返回第一个元素。要提取一行，请确保使用 `:`，如 `x[1,:]`。
  * Julia的 [`map`](@ref) 首先接受函数，然后是它的参数，这与R中的 `lapply(<structure>, function, ...)` 不同。类似地，Julia中与R的 `apply(X, MARGIN, FUN, ...)` 等价的函数是 [`mapslices`](@ref)，其中函数是第一个参数。
  * 在 R 中的多变量应用，例如 `mapply(choose, 11:13, 1:3)`，可以在 Julia 中写成 `broadcast(binomial, 11:13, 1:3)`。同样，Julia 提供了一个更简短的点语法来向量化函数 `binomial.(11:13, 1:3)`。
  * Julia 使用 `end` 来表示条件块的结束，例如 `if`、循环块，例如 `while`/ `for` 和函数。作为单行 `if ( cond ) statement` 的替代，Julia 允许使用 `if cond; statement; end`、`cond && statement` 和 `!cond || statement` 这样的语句。在后两种语法中，赋值语句必须显式地用括号括起来，例如 `cond && (x = value)`。
  * 在 Julia 中，`<-`、`<<-` 和 `->` 不是赋值运算符。
  * Julia的`->`创建一个匿名函数。
  * Julia的 [`*`](@ref) 运算符可以执行矩阵乘法，这与R不同。如果 `A` 和 `B` 是矩阵，则 `A * B` 表示在Julia中的矩阵乘法，相当于R中的 `A %*% B`。在R中，这种相同的符号将执行逐元素（哈达玛）乘法。要获得逐元素乘法操作，您需要在Julia中写 `A .* B`。
  * Julia 使用 `transpose` 函数进行矩阵转置，使用 `'` 运算符或 `adjoint` 函数进行共轭转置。因此，Julia 的 `transpose(A)` 相当于 R 的 `t(A)`。此外，Julia 还提供了一个非递归转置功能，通过 `permutedims` 函数实现。
  * Julia 在编写 `if` 语句或 `for`/`while` 循环时不需要括号：使用 `for i in [1, 2, 3]` 而不是 `for (i in c(1, 2, 3))`，以及 `if i == 1` 而不是 `if (i == 1)`。
  * Julia 不将数字 `0` 和 `1` 视为布尔值。你不能在 Julia 中写 `if (1)`，因为 `if` 语句只接受布尔值。相反，你可以写 `if true`、`if Bool(1)` 或 `if 1==1`。
  * Julia 不提供 `nrow` 和 `ncol`。相反，使用 `size(M, 1)` 替代 `nrow(M)`，使用 `size(M, 2)` 替代 `ncol(M)`。
  * Julia 小心地区分标量、向量和矩阵。在 R 中，`1` 和 `c(1)` 是相同的。在 Julia 中，它们不能互换使用。
  * 朱莉亚的 [`diag`](@ref) 和 [`diagm`](@ref) 与 R 的不同。
  * Julia 不能将函数调用的结果赋值给赋值操作的左侧：你不能写 `diag(M) = fill(1, n)`。
  * Julia 不鼓励在主命名空间中填充函数。大多数 Julia 的统计功能可以在 [packages](https://pkg.julialang.org/) 下的 [JuliaStats organization](https://github.com/JuliaStats) 中找到。例如：

      * 与概率分布相关的函数由 [Distributions package](https://github.com/JuliaStats/Distributions.jl) 提供。
      * [DataFrames package](https://github.com/JuliaData/DataFrames.jl) 提供数据框。
      * 广义线性模型由 [GLM package](https://github.com/JuliaStats/GLM.jl) 提供。
  * Julia 提供元组和真实哈希表，但不提供 R 风格的列表。当返回多个项目时，通常应使用元组或命名元组：使用 `(1, 2)` 或 `(a=1, b=2)`，而不是 `list(a = 1, b = 2)`。
  * Julia 鼓励用户编写自己的类型，这比 R 中的 S3 或 S4 对象更易于使用。Julia 的多重分发系统意味着 `table(x::TypeA)` 和 `table(x::TypeB)` 的行为类似于 R 的 `table.TypeA(x)` 和 `table.TypeB(x)`。
  * 在Julia中，赋值或传递给函数时，值不会被复制。如果一个函数修改了一个数组，调用者将能看到这些变化。这与R有很大不同，使得新函数能够更高效地操作大型数据结构。
  * 在 Julia 中，向量和矩阵的连接使用 [`hcat`](@ref)、[`vcat`](@ref) 和 [`hvcat`](@ref)，而不是像 R 中的 `c`、`rbind` 和 `cbind`。
  * 在 Julia 中，像 `a:b` 这样的范围并不是像 R 中那样的向量简写，而是一个专门的 `AbstractRange` 对象，用于迭代。要将范围转换为向量，请使用 [`collect(a:b)`](@ref)。
  * `:` 运算符在 R 和 Julia 中具有不同的优先级。特别地，在 Julia 中，算术运算符的优先级高于 `:` 运算符，而在 R 中则相反。例如，Julia 中的 `1:n-1` 相当于 R 中的 `1:(n-1)`。
  * Julia的 [`max`](@ref) 和 [`min`](@ref) 分别是 R 中 `pmax` 和 `pmin` 的等价物，但两个参数需要具有相同的维度。而 [`maximum`](@ref) 和 [`minimum`](@ref) 则替代了 R 中的 `max` 和 `min`，但存在重要的区别。
  * Julia的 [`sum`](@ref)、[`prod`](@ref)、[`maximum`](@ref) 和 [`minimum`](@ref) 与它们在R中的对应函数不同。它们都接受一个可选的关键字参数 `dims`，该参数指示操作所执行的维度。例如，在Julia中设 `A = [1 2; 3 4]`，在R中设 `B <- rbind(c(1,2),c(3,4))` 为相同的矩阵。那么 `sum(A)` 的结果与 `sum(B)` 相同，但 `sum(A, dims=1)` 是一个包含每列和的行向量，而 `sum(A, dims=2)` 是一个包含每行和的列向量。这与R的行为形成对比，在R中，单独的 `colSums(B)` 和 `rowSums(B)` 函数提供这些功能。如果 `dims` 关键字参数是一个向量，则它指定执行求和的所有维度，同时保留被求和数组的维度，例如 `sum(A, dims=(1,2)) == hcat(10)`。需要注意的是，第二个参数没有错误检查。
  * 朱莉亚有几个可以改变其参数的函数。例如，它有 [`sort`](@ref) 和 [`sort!`](@ref)。
  * 在 R 中，性能需要向量化。在 Julia 中，几乎相反：最佳性能的代码通常是通过使用去向量化的循环来实现的。
  * Julia 是急切求值的，不支持 R 风格的惰性求值。对于大多数用户来说，这意味着几乎没有未引用的表达式或列名。
  * Julia 不支持 `NULL` 类型。最接近的等价物是 [`nothing`](@ref)，但它的行为更像是标量值而不是列表。请使用 `x === nothing` 代替 `is.null(x)`。
  * 在 Julia 中，缺失值由 [`missing`](@ref) 对象表示，而不是 `NA`。请使用 [`ismissing(x)`](@ref)（或对向量进行逐元素操作时使用 `ismissing.(x)`）而不是 `is.na(x)`。通常使用 [`skipmissing`](@ref) 函数，而不是 `na.rm=TRUE`（尽管在某些特定情况下，函数会接受 `skipmissing` 参数）。
  * Julia 缺乏 R 的 `assign` 或 `get` 的等效功能。
  * 在Julia中，`return`不需要括号。
  * 在 R 中，去除不需要的值的惯用方法是使用逻辑索引，例如表达式 `x[x>3]` 或语句 `x = x[x>3]` 来就地修改 `x`。相比之下，Julia 提供了高阶函数 [`filter`](@ref) 和 [`filter!`](@ref)，允许用户写 `filter(z->z>3, x)` 和 `filter!(z->z>3, x)` 作为对应的音译 `x[x.>3]` 和 `x = x[x.>3]` 的替代方案。使用 `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` 减少了临时数组的使用。

## Noteworthy differences from Python

  * Julia 的 `for`、`if`、`while` 等块通过 `end` 关键字结束。缩进级别并不像 Python 中那样重要。与 Python 不同，Julia 没有 `pass` 关键字。
  * 字符串在Julia中用双引号（`"text"`）表示（多行字符串用三个双引号表示），而在Python中可以用单引号（`'text'`）或双引号（`"text"`）表示。单引号在Julia中用于表示字符（`'c'`）。
  * 字符串连接在 Julia 中使用 `*`，而不是像 Python 中那样使用 `+`。类似地，字符串重复使用 `^`，而不是 `*`。在 Julia 中不支持像 Python 中那样的字符串字面量的隐式连接（例如，`'ab' 'cd' == 'abcd'`）。
  * Python 列表——灵活但较慢——对应于 Julia 的 `Vector{Any}` 类型或更一般的 `Vector{T}`，其中 `T` 是某种非具体元素类型。像 NumPy 数组这样的“快速”数组，它们在原地存储元素（即 `dtype` 是 `np.float64`，`[('f1', np.uint64), ('f2', np.int32)]` 等）可以用 `Array{T}` 表示，其中 `T` 是具体的、不可变的元素类型。这包括内置类型，如 `Float64`、`Int32`、`Int64`，还包括更复杂的类型，如 `Tuple{UInt64,Float64}` 和许多用户定义的类型。
  * 在Julia中，数组、字符串等的索引是从1开始的，而不是从0开始的。
  * Julia的切片索引包括最后一个元素，这与Python不同。在Julia中，`a[2:3]` 在Python中是 `a[1:3]`。
  * 与 Python 不同，Julia 允许 [AbstractArrays with arbitrary indexes](https://julialang.org/blog/2017/04/offset-arrays/)。Python 对负索引的特殊解释 `a[-1]` 和 `a[-2]` 应在 Julia 中写作 `a[end]` 和 `a[end-1]`。
  * Julia需要`end`来索引到最后一个元素。在Python中，`x[1:]`相当于Julia中的`x[2:end]`。
  * 在 Julia 中，`:` 在任何对象之前会创建一个 [`Symbol`](@ref) 或者 *引用* 一个表达式；因此，`x[:5]` 与 `x[5]` 是相同的。如果你想获取数组的前 `n` 个元素，那么使用范围索引。
  * Julia的范围索引格式为 `x[start:step:stop]`，而Python的格式为 `x[start:(stop+1):step]`。因此，Python中的 `x[0:10:2]` 相当于Julia中的 `x[1:2:10]`。类似地，Python中的 `x[::-1]`，表示反转数组，相当于Julia中的 `x[end:-1:1]`。
  * 在 Julia 中，范围可以独立构造为 `start:step:stop`，与数组索引中使用的语法相同。`range` 函数也被支持。
  * 在Julia中，使用数组对矩阵进行索引，如`X[[1,2], [1,3]]`，指的是一个子矩阵，该子矩阵包含第一和第二行与第一和第三列的交集。在Python中，`X[[1,2], [1,3]]`指的是一个向量，该向量包含矩阵中单元格`[1,1]`和`[2,3]`的值。在Julia中，`X[[1,2], [1,3]]`等同于Python中的`X[np.ix_([0,1],[0,2])]`。在Python中，`X[[0,1], [0,2]]`等同于Julia中的`X[[CartesianIndex(1,1), CartesianIndex(2,3)]]`。
  * Julia 没有行续写语法：如果在行末，当前输入是一个完整的表达式，则被视为完成；否则输入将继续。强制表达式继续的一种方法是将其包裹在括号中。
  * Julia 数组是列主序（Fortran 排序），而 NumPy 数组默认是行主序（C 排序）。为了在循环遍历数组时获得最佳性能，Julia 中的循环顺序应该相对于 NumPy 进行反转（请参见 [relevant section of Performance Tips](@ref man-performance-column-major)）。
  * Julia 的更新操作符（例如 `+=`、`-=` 等）*不是就地操作*，而 NumPy 的是。这意味着 `A = [1, 1]; B = A; B += [3, 3]` 不会改变 `A` 中的值，而是将名称 `B` 重新绑定到右侧结果 `B = B + 3`，这实际上是一个新数组。对于就地操作，请使用 `B .+= 3`（另见 [dot operators](@ref man-dot-operators)）、显式循环或 `InplaceOps.jl`。
  * Julia 每次调用方法时都会评估函数参数的默认值，这与 Python 不同，后者在函数定义时只评估一次默认值。例如，函数 `f(x=rand()) = x` 每次在没有参数的情况下调用时都会返回一个新的随机数。另一方面，函数 `g(x=[1,2]) = push!(x,3)` 每次调用 `g()` 时都会返回 `[1,2,3]`。
  * 在Julia中，关键字参数必须使用关键字传递，这与Python不同，后者通常可以通过位置传递它们。尝试通过位置传递关键字参数会改变方法签名，从而导致`MethodError`或调用错误的方法。
  * 在Julia中，`%`是余数运算符，而在Python中它是模运算符。
  * 在 Julia 中，常用的 `Int` 类型对应于机器整数类型（`Int32` 或 `Int64`），与 Python 中的 `int`（任意长度整数）不同。这意味着在 Julia 中，`Int` 类型会溢出，例如 `2^64 == 0`。如果需要更大的值，请使用其他适当的类型，例如 `Int128`、[`BigInt`](@ref) 或浮点类型如 `Float64`。
  * 虚数单位 `sqrt(-1)` 在 Julia 中表示为 `im`，而不是像 Python 中的 `j`。
  * 在Julia中，指数运算符是`^`，而不是像Python中的`**`。
  * Julia 使用类型为 `Nothing` 的 `nothing` 来表示空值，而 Python 使用类型为 `NoneType` 的 `None`。
  * 在Julia中，矩阵类型的标准运算符是矩阵运算，而在Python中，标准运算符是逐元素运算。当`A`和`B`都是矩阵时，Julia中的`A * B`执行矩阵乘法，而不是像Python中的逐元素乘法。Julia中的`A * B`相当于Python中的`A @ B`，而Python中的`A * B`相当于Julia中的`A .* B`。
  * 在Julia中，伴随算子`'`返回一个向量的伴随（行向量的惰性表示），而在Python中，转置算子`.T`对一个向量返回原始向量（无操作）。
  * 在Julia中，一个函数可以包含多个具体实现（称为*方法*），这些实现通过多重分发根据调用中所有参数的类型进行选择，而与Python中的函数不同，后者只有一个实现且没有多态性（与Python方法调用不同，后者使用不同的语法并允许根据方法的接收者进行分发）。
  * 在Julia中没有类。相反，有结构（可变或不可变），包含数据但没有方法。
  * 在Python中调用类实例的方法（`x = MyClass(*args); x.f(y)`）对应于Julia中的函数调用，例如`x = MyType(args...); f(x, y)`。一般来说，多重派发比Python的类系统更灵活、更强大。
  * Julia 结构可以有一个抽象超类型，而 Python 类可以从一个或多个（抽象或具体）超类继承。
  * 逻辑上的Julia程序结构（包和模块）与文件结构无关，而Python代码结构则由目录（包）和文件（模块）定义。
  * 在Julia中，将大型模块的文本拆分成多个文件是惯用的做法，而不需要为每个文件引入一个新模块。代码在主文件中通过`include`重新组合到一个单一模块内。虽然Python中的等效方法（`exec`）在这种用法中并不典型（它会默默覆盖之前的定义），但Julia程序在`module`级别上被定义为一个单元，使用`using`或`import`，这些只会在首次需要时执行一次——就像Python中的`include`一样。在这些模块内，构成该模块的各个文件通过`include`按预定顺序列出并加载。
  * 三元运算符 `x > 0 ? 1 : -1` 在 Julia 中对应于 Python 中的条件表达式 `1 if x > 0 else -1`。
  * 在Julia中，`@`符号指的是宏，而在Python中，它指的是装饰器。
  * 在Julia中，异常处理使用`try` — `catch` — `finally`，而不是`try` — `except` — `finally`。与Python相比，不建议在Julia中将异常处理作为正常工作流程的一部分（与Python相比，Julia在普通控制流中更快，但在捕获异常时较慢）。
  * 在Julia中，循环是快速的，出于性能原因没有必要编写“向量化”的代码。
  * 在 Julia 中，特别是在紧密循环中，要小心非恒定的全局变量。由于您可以在 Julia 中编写接近底层的代码（与 Python 不同），全局变量的影响可能是巨大的（请参见 [Performance Tips](@ref man-performance-tips)）。
  * 在Julia中，舍入和截断是显式的。Python的`int(3.7)`应该是`floor(Int, 3.7)`或`Int(floor(3.7))`，并且与`round(Int, 3.7)`有所区别。`floor(x)`和`round(x)`本身返回与`x`相同类型的整数值，而不是总是返回`Int`。
  * 在Julia中，解析是显式的。Python的 `float("3.7")` 在Julia中将是 `parse(Float64, "3.7")`。
  * 在 Python 中，大多数值可以在逻辑上下文中使用（例如 `if "a":` 意味着执行以下代码块，而 `if "":` 意味着不执行）。在 Julia 中，你需要显式转换为 `Bool`（例如 `if "a"` 会抛出异常）。如果你想在 Julia 中测试一个非空字符串，你需要显式写成 `if !isempty("")`。也许令人惊讶的是，在 Python 中 `if "False"` 和 `bool("False")` 都评估为 `True`（因为 `"False"` 是一个非空字符串）；而在 Julia 中，`parse(Bool, "false")` 返回 `false`。
  * 在 Julia 中，大多数代码块（包括循环和 `try` — `catch` — `finally`）引入了一个新的局部作用域。请注意，推导式（列表、生成器等）在 Python 和 Julia 中都引入了一个新的局部作用域，而 `if` 块在这两种语言中都不会引入新的局部作用域。

## Noteworthy differences from C/C++

  * Julia 数组使用方括号进行索引，并且可以具有多个维度 `A[i,j]`。这种语法不仅仅是 C/C++ 中对指针或地址的引用的语法糖。请参见 [the manual entry about array construction](@ref man-multi-dim-arrays)。
  * 在Julia中，数组、字符串等的索引是从1开始的，而不是从0开始的。
  * Julia 数组在赋值给另一个变量时不会被复制。在 `A = B` 之后，修改 `B` 的元素也会修改 `A`。更新操作符如 `+=` 并不是就地操作，它们等同于 `A = A + B`，这会将左侧重新绑定到右侧表达式的结果。
  * Julia 数组是列主序（Fortran 排序），而 C/C++ 数组默认是行主序。为了在循环遍历数组时获得最佳性能，Julia 中的循环顺序应该相对于 C/C++ 进行反转（参见 [relevant section of Performance Tips](@ref man-performance-column-major)）。
  * Julia 的值在赋值或传递给函数时不会被复制。如果一个函数修改了一个数组，变化将在调用者中可见。
  * 在Julia中，空白是重要的，这与C/C++不同，因此在向Julia程序中添加/删除空白时必须小心。
  * 在 Julia 中，没有小数点的字面数字（例如 `42`）会创建有符号整数，类型为 `Int`，但过大以至于无法适应机器字大小的字面量会自动提升为更大尺寸的类型，例如 `Int64`（如果 `Int` 是 `Int32`）、`Int128` 或任意大的 `BigInt` 类型。没有数字字面量后缀，例如 `L`、`LL`、`U`、`UL`、`ULL` 来指示有符号和/或无符号。十进制字面量总是有符号的，而十六进制字面量（以 `0x` 开头，如 C/C++）是无符号的，除非它们编码超过 128 位，在这种情况下它们的类型为 `BigInt`。与 C/C++/Java 不同，且与 Julia 中的十进制字面量不同，十六进制字面量的类型基于字面量的 *长度*，包括前导 0。例如，`0x0` 和 `0x00` 的类型为 [`UInt8`](@ref)，`0x000` 和 `0x0000` 的类型为 [`UInt16`](@ref)，然后 5 到 8 个十六进制数字的字面量类型为 `UInt32`，9 到 16 个十六进制数字的类型为 `UInt64`，17 到 32 个十六进制数字的类型为 `UInt128`，超过 32 个十六进制数字的类型为 `BigInt`。在定义十六进制掩码时需要考虑这一点，例如 `~0xf == 0xf0` 与 `~0x000f == 0xfff0` 是非常不同的。64 位 `Float64` 和 32 位 [`Float32`](@ref) 位字面量分别表示为 `1.0` 和 `1.0f0`。如果浮点字面量无法被精确表示，则会被四舍五入（而不是提升为 `BigFloat` 类型）。浮点字面量的行为更接近于 C/C++。八进制（以 `0o` 为前缀）和二进制（以 `0b` 为前缀）字面量也被视为无符号（或对于超过 128 位的情况为 `BigInt`）。
  * 在Julia中，当两个操作数都是整数类型时，除法运算符 [`/`](@ref) 返回一个浮点数。要执行整数除法，请使用 [`div`](@ref) 或 [`÷`](@ref div)。
  * 在Julia中，使用浮点类型对`Array`进行索引通常是一个错误。C表达式`a[i / 2]`的Julia等价表达式是`a[i ÷ 2 + 1]`，其中`i`是整数类型。
  * 字符串字面量可以用 `"` 或 `"""` 来定界，`"""` 定界的字面量可以包含 `"` 字符而无需引用，例如 `"\""`。字符串字面量可以插入其他变量或表达式的值，使用 `$variablename` 或 `$(expression)` 表示，这将在函数的上下文中评估变量名或表达式。
  * `//` 表示一个 [`Rational`](@ref) 数字，而不是单行注释（在 Julia 中是 `#`）
  * `#=` 表示多行注释的开始， `=#` 表示结束。
  * 在Julia中，函数从其最后一个表达式或`return`关键字返回值。可以从函数返回多个值并将其作为元组赋值，例如`(a, b) = myfunction()`或`a, b = myfunction()`，而不必像在C/C++中那样传递指向值的指针（即`a = myfunction(&b)`）。
  * Julia 不需要使用分号来结束语句。表达式的结果不会自动打印（除非在交互提示符下，即 REPL），代码行不需要以分号结束。[`println`](@ref) 或 [`@printf`](@ref) 可以用来打印特定的输出。在 REPL 中，可以使用 `;` 来抑制输出。`；` 在 `[ ]` 中也有不同的含义，这一点需要注意。`；` 可以用来在单行中分隔表达式，但在许多情况下并不是严格必要的，更像是提高可读性的辅助工具。
  * 在Julia中，运算符 [`⊻`](@ref xor) ([`xor`](@ref)) 执行按位异或操作，即在C/C++中为 [`^`](@ref)。此外，按位运算符的优先级与C/C++不同，因此可能需要使用括号。
  * 朱莉亚的 [`^`](@ref) 是指数运算（pow），而不是像 C/C++ 中的按位异或（使用 [`⊻`](@ref xor) 或 [`xor`](@ref)，在朱莉亚中）。
  * Julia 有两个右移操作符，`>>` 和 `>>>`。 `>>` 执行算术右移，`>>>` 始终执行逻辑右移，这与 C/C++ 不同，在 C/C++ 中，`>>` 的含义取决于被移位值的类型。
  * Julia 的 `->` 创建一个匿名函数，它并不通过指针访问成员。
  * Julia 在编写 `if` 语句或 `for`/`while` 循环时不需要括号：使用 `for i in [1, 2, 3]` 而不是 `for (int i=1; i <= 3; i++)`，以及 `if i == 1` 而不是 `if (i == 1)`。
  * Julia 不将数字 `0` 和 `1` 视为布尔值。你不能在 Julia 中写 `if (1)`，因为 `if` 语句只接受布尔值。相反，你可以写 `if true`、`if Bool(1)` 或 `if 1==1`。
  * Julia 使用 `end` 来表示条件块的结束，例如 `if`、循环块，例如 `while`/ `for` 和函数。作为单行 `if ( cond ) statement` 的替代，Julia 允许使用 `if cond; statement; end`、`cond && statement` 和 `!cond || statement` 这样的语句。在后两种语法中，赋值语句必须显式地用括号包裹，例如 `cond && (x = value)`，这是因为运算符优先级的原因。
  * Julia 没有行续写语法：如果在行末，当前输入是一个完整的表达式，则被视为完成；否则，输入将继续。强制表达式继续的一种方法是将其包裹在括号中。
  * Julia 宏操作于解析后的表达式，而不是程序的文本，这使得它们能够对 Julia 代码进行复杂的转换。宏名称以 `@` 字符开头，具有类似函数的语法 `@mymacro(arg1, arg2, arg3)` 和类似语句的语法 `@mymacro arg1 arg2 arg3`。这两种形式是可以互换的；类似函数的形式在宏出现在另一个表达式中时特别有用，并且通常更清晰。类似语句的形式通常用于注释块，例如在分布式 `for` 构造中：`@distributed for i in 1:n; #= body =#; end`。如果宏构造的结束可能不清楚，请使用类似函数的形式。
  * Julia 有一个枚举类型，使用宏 `@enum(name, value1, value2, ...)` 表达。例如：`@enum(Fruit, banana=1, apple, pear)`
  * 根据约定，修改其参数的函数名称末尾有一个 `!`，例如 `push!`。
  * 在 C++ 中，默认情况下，你有静态调度，即你需要将一个函数标记为虚拟，以便实现动态调度。另一方面，在 Julia 中，每个方法都是“虚拟的”（尽管这更为广泛，因为方法是基于每个参数类型进行调度的，而不仅仅是 `this`，使用的是最特定声明规则）。

### Julia ⇔ C/C++: Namespaces

  * C/C++ `namespace`s 与 Julia `module`s 大致对应。
  * 在Julia中没有私有全局变量或字段。所有内容都可以通过完全限定路径（或相对路径，如果需要的话）公开访问。
  * `using MyNamespace::myfun` (C++) 大致对应于 `import MyModule: myfun` (Julia)。
  * `using namespace MyNamespace` (C++) 大致对应于 `using MyModule` (Julia)

      * 在 Julia 中，只有 `export` 的符号才会对调用模块可用。
      * 在 C++ 中，只有在包含的（公共）头文件中找到的元素才会被提供。
  * 警告：`import`/`using` 关键字（Julia）也会 *加载* 模块（见下文）。
  * 警告：`import`/`using`（Julia）仅在全局作用域级别（`module`）中有效。

      * 在 C++ 中，`using namespace X` 可以在任意作用域内工作（例如：函数作用域）。

### Julia ⇔ C/C++: Module loading

  * 当你想到 C/C++ 的 "**库**" 时，你可能在寻找 Julia 的 "**包**"。

      * 警告：C/C++ 库通常包含多个“软件模块”，而 Julia “包” 通常只包含一个。
      * 提醒：Julia `module` 是全局作用域（不一定是“软件模块”）。
  * **而不是构建/`make`脚本**，Julia 使用“项目环境”（有时称为“项目”或“环境”）。

      * 构建脚本仅在更复杂的应用程序中需要（例如那些需要编译或下载 C/C++ 可执行文件的应用程序）。
      * 要在Julia中开发应用程序或项目，您可以将其根目录初始化为“项目环境”，并在其中存放特定于应用程序的代码/包。这提供了对项目依赖项的良好控制，以及未来的可重复性。
      * 可用的包通过 `Pkg.add()` 函数或 Pkg REPL 模式添加到“项目环境”中。（不过，这并不会**加载**该包）。
      * 可用包（直接依赖）的列表保存在“项目环境”的 `Project.toml` 文件中。
      * “项目环境”的*完整*依赖信息由`Pkg.resolve()`自动生成并保存在其`Manifest.toml`文件中。
  * 可用于“项目环境”的软件包（“软件模块”）通过 `import` 或 `using` 加载。

      * 在 C/C++ 中，您使用 `#include <moduleheader>` 来获取对象/函数声明，并在构建可执行文件时链接库。
      * 在Julia中，再次调用using/import只会将现有模块引入作用域，但不会重新加载它（类似于在C/C++中添加非标准的`#pragma once`）。
  * **基于目录的包仓库**（Julia）可以通过将仓库路径添加到 `Base.LOAD_PATH` 数组中来实现。

      * 来自基于目录的仓库的包在使用 `import` 或 `using` 之前不需要使用 `Pkg.add()` 工具。它们对项目是直接可用的。
      * 基于目录的包存储库是开发“软件模块”本地库的**最快解决方案**。

### Julia ⇔ C/C++: Assembling modules

  * 在 C/C++ 中，`.c`/`.cpp` 文件通过构建/`make` 脚本进行编译并添加到库中。

      * 在 Julia 中，`import [PkgName]`/`using [PkgName]` 语句加载位于包的 `[PkgName]/src/` 子目录中的 `[PkgName].jl` 文件。
      * 反过来，`[PkgName].jl` 通常通过调用 `include "[someotherfile].jl"` 来加载相关的源文件。
  * `include "./path/to/somefile.jl"`（Julia）与`#include "./path/to/somefile.jl"`（C/C++）非常相似。

      * 然而 `include "..."`（Julia）并不是用来包含头文件的（不需要）。
      * **不要使用** `include "..."`（Julia）从其他“软件模块”加载代码（请改用 `import`/`using`）。
      * `include "path/to/some/module.jl"`（Julia）会在不同的模块中实例化相同代码的多个版本（创建具有*相同*名称的*不同*类型等）。
      * `include "somefile.jl"` 通常用于在 *同一个 Julia 包*（“软件模块”）内组合多个文件。因此，确保文件仅被 `include` 一次相对简单（没有 `#ifdef` 的混淆）。

### Julia ⇔ C/C++: Module interface

  * C++ 通过 "public" `.h`/`.hpp` 文件暴露接口，而 Julia `module` 通过将特定符号标记为 `public` 或 `export` 来标识其用户。

      * 通常，Julia `module` 通过为现有函数生成新的“方法”来简单地添加功能（例如：`Base.push!`）。
      * 因此，Julia 包的开发者不能依赖头文件来进行接口文档的编写。
      * Julia 包的接口通常使用文档字符串、README.md、静态网页等进行描述。
  * 一些开发者选择不 `export` 所有使用其包/模块所需的符号，但仍应将未导出的用户可见符号标记为 `public`。

      * 用户可能需要通过使用包/模块名称来限定函数/结构体/... 来访问这些组件（例如：`MyModule.run_this_task(...)`）。

### Julia ⇔ C/C++: Quick reference

| Software Concept               | Julia                                                                          | C/C++                                                     |
|:------------------------------ |:------------------------------------------------------------------------------ |:--------------------------------------------------------- |
| unnamed scope                  | `begin` ... `end`                                                              | `{` ... `}`                                               |
| function scope                 | `function x()` ... `end`                                                       | `int x() {` ... `}`                                       |
| global scope                   | `module MyMod` ... `end`                                                       | `namespace MyNS {` ... `}`                                |
| software module                | A Julia "package"                                                              | `.h`/`.hpp` files<br>+compiled `somelib.a`                |
| assembling<br>software modules | `SomePkg.jl`: ...<br>`import("subfile1.jl")`<br>`import("subfile2.jl")`<br>... | `$(AR) *.o` &rArr; `somelib.a`                            |
| import<br>software module      | `import SomePkg`                                                               | `#include <somelib>`<br>+link in `somelib.a`              |
| module library                 | `LOAD_PATH[]`, *Git repository,<br>**custom package registry                   | more `.h`/`.hpp` files<br>+bigger compiled `somebiglib.a` |

* The Julia package manager supports registering multiple packages from a single Git repository.<br> * This allows users to house a library of related packages in a single repository.<br> ** Julia registries are primarily designed to provide versioning \& distribution of packages.<br> ** Custom package registries can be used to create a type of module library.

## Noteworthy differences from Common Lisp

  * Julia 默认使用 1 基索引来处理数组，并且它还可以处理任意 [index offsets](@ref man-custom-indices)。
  * 函数和变量共享相同的命名空间（“Lisp-1”）。
  * 有一个 [`Pair`](@ref) 类型，但它并不打算用作 `COMMON-LISP:CONS`。在语言的大多数部分，可以互换使用各种可迭代集合（例如展开、元组等）。`Tuple` 是与 Common Lisp 列表最接近的 *短* 异构元素集合。使用 `NamedTuple` 替代关联列表。对于更大的同构类型集合，应使用 `Array` 和 `Dict`。
  * 典型的 Julia 原型工作流程还使用图像的连续操作，使用 [Revise.jl](https://github.com/timholy/Revise.jl) 包实现。
  * 为了性能，Julia 更倾向于操作具有 [type stability](@ref man-type-stability)。而 Common Lisp 抽象了底层机器操作，Julia 则更贴近这些操作。例如：

      * 整数除法使用 `/` 总是返回浮点结果，即使计算是精确的。

          * `//` 总是返回一个有理结果
          * `÷` 总是返回一个（截断的）整数结果
      * 大数被支持，但转换不是自动的；普通整数 [overflow](@ref faq-integer-arithmetic)。
      * 复数是支持的，但要获得复杂的结果，[you need complex inputs](@ref faq-domain-errors)。
      * 有多种复数和有理数类型，具有不同的组件类型。
  * 模块（命名空间）可以是层次化的。 [`import`](@ref) 和 [`using`](@ref) 具有双重角色：它们加载代码并使其在命名空间中可用。 仅使用模块名称的 `import` 是可能的（大致相当于 `ASDF:LOAD-OP`）。 插槽名称不需要单独导出。 全局变量不能从模块外部进行赋值（除了使用 `eval(mod, :(var = val))` 作为逃生口）。
  * 宏以 `@` 开头，并且没有像 Common Lisp 那样无缝集成到语言中；因此，宏的使用并不像后者那样普遍。语言支持 [macros](@ref Metaprogramming) 的一种卫生形式。由于不同的表面语法，没有与 `COMMON-LISP:&BODY` 等价的东西。
  * *所有*函数都是通用的，并使用多重分发。参数列表不必遵循相同的模板，这导致了一种强大的习惯用法（见 [`do`](@ref)）。可选参数和关键字参数的处理方式不同。方法的模糊性不像在通用 Lisp 对象系统中那样得到解决，因此需要为交集定义一个更具体的方法。
  * 符号不属于任何包，也不包含任何值 *per se*。 `M.var` 在模块 `M` 中评估符号 `var`。
  * A functional programming style is fully supported by the language, including closures, but isn't always the idiomatic solution for Julia. Some [workarounds](@ref man-performance-captured) may be necessary for performance when modifying captured variables.

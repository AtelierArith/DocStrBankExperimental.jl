# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

Julia，像大多数技术计算语言一样，提供了一流的数组实现。大多数技术计算语言在其数组实现上投入了大量精力，而牺牲了其他容器。Julia 并没有以任何特殊方式对待数组。数组库几乎完全用 Julia 本身实现，其性能来自编译器，就像用 Julia 编写的任何其他代码一样。因此，也可以通过继承 [`AbstractArray`](@ref) 来定义自定义数组类型。有关实现自定义数组类型的更多详细信息，请参见 [manual section on the AbstractArray interface](@ref man-interface-array)。

数组是存储在多维网格中的对象集合。允许使用零维数组，参见 [this FAQ entry](@ref faq-array-0dim)。在最一般的情况下，数组可以包含类型为 [`Any`](@ref) 的对象。对于大多数计算目的，数组应包含更具体类型的对象，例如 [`Float64`](@ref) 或 [`Int32`](@ref)。

一般来说，与许多其他技术计算语言不同，Julia 并不期望程序以向量化风格编写以提高性能。Julia 的编译器使用类型推断，并为标量数组索引生成优化代码，允许以方便且可读的风格编写程序，而不牺牲性能，有时还可以使用更少的内存。

在 Julia 中，所有函数的参数都是 [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing)（即通过指针传递）。一些技术计算语言按值传递数组，虽然这可以防止被调用者意外修改调用者中的值，但这使得避免不必要的数组复制变得困难。根据约定，以 `!` 结尾的函数名称表示它将改变或销毁一个或多个参数的值（例如，比较 [`sort`](@ref) 和 [`sort!`](@ref)）。被调用者必须显式地进行复制，以确保他们不会修改不打算更改的输入。许多非变异函数是通过在输入的显式副本上调用同名函数并在末尾添加 `!` 来实现的，并返回该副本。

## Basic Functions

| Function               | Description                                                                      |
|:---------------------- |:-------------------------------------------------------------------------------- |
| [`eltype(A)`](@ref)    | the type of the elements contained in `A`                                        |
| [`length(A)`](@ref)    | the number of elements in `A`                                                    |
| [`ndims(A)`](@ref)     | the number of dimensions of `A`                                                  |
| [`size(A)`](@ref)      | a tuple containing the dimensions of `A`                                         |
| [`size(A,n)`](@ref)    | the size of `A` along dimension `n`                                              |
| [`axes(A)`](@ref)      | a tuple containing the valid indices of `A`                                      |
| [`axes(A,n)`](@ref)    | a range expressing the valid indices along dimension `n`                         |
| [`eachindex(A)`](@ref) | an efficient iterator for visiting each position in `A`                          |
| [`stride(A,k)`](@ref)  | the stride (linear index distance between adjacent elements) along dimension `k` |
| [`strides(A)`](@ref)   | a tuple of the strides in each dimension                                         |

## Construction and Initialization

许多用于构造和初始化数组的函数可用。在以下这些函数的列表中，带有 `dims...` 参数的调用可以接受一个维度大小的元组，或者作为可变数量的参数传递的一系列维度大小。大多数这些函数还接受第一个输入 `T`，这是数组的元素类型。如果省略类型 `T`，则默认为 [`Float64`](@ref)。

| Function                           | Description                                                                                                                                                                                                                                  |
|:---------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Array{T}(undef, dims...)`](@ref) | an uninitialized dense [`Array`](@ref)                                                                                                                                                                                                       |
| [`zeros(T, dims...)`](@ref)        | an `Array` of all zeros                                                                                                                                                                                                                      |
| [`ones(T, dims...)`](@ref)         | an `Array` of all ones                                                                                                                                                                                                                       |
| [`trues(dims...)`](@ref)           | a [`BitArray`](@ref) with all values `true`                                                                                                                                                                                                  |
| [`falses(dims...)`](@ref)          | a `BitArray` with all values `false`                                                                                                                                                                                                         |
| [`reshape(A, dims...)`](@ref)      | an array containing the same data as `A`, but with different dimensions                                                                                                                                                                      |
| [`copy(A)`](@ref)                  | copy `A`                                                                                                                                                                                                                                     |
| [`deepcopy(A)`](@ref)              | copy `A`, recursively copying its elements                                                                                                                                                                                                   |
| [`similar(A, T, dims...)`](@ref)   | an uninitialized array of the same type as `A` (dense, sparse, etc.), but with the specified element type and dimensions. The second and third arguments are both optional, defaulting to the element type and dimensions of `A` if omitted. |
| [`reinterpret(T, A)`](@ref)        | an array with the same binary data as `A`, but with element type `T`                                                                                                                                                                         |
| [`rand(T, dims...)`](@ref)         | an `Array` with random, iid [^1] and uniformly distributed values. For floating point types `T`, the values lie in the half-open interval $[0, 1)$.                                                                                          |
| [`randn(T, dims...)`](@ref)        | an `Array` with random, iid and standard normally distributed values                                                                                                                                                                         |
| [`Matrix{T}(I, m, n)`](@ref)       | `m`-by-`n` identity matrix. Requires `using LinearAlgebra` for [`I`](@ref).                                                                                                                                                                  |
| [`range(start, stop, n)`](@ref)    | a range of `n` linearly spaced elements from `start` to `stop`                                                                                                                                                                               |
| [`fill!(A, x)`](@ref)              | fill the array `A` with the value `x`                                                                                                                                                                                                        |
| [`fill(x, dims...)`](@ref)         | an `Array` filled with the value `x`. In particular, `fill(x)` constructs a zero-dimensional `Array` containing `x`.                                                                                                                         |

[^1]: *iid*, independently and identically distributed.

要查看我们可以以各种方式将维度传递给这些函数，请考虑以下示例：

```jldoctest
julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros(Int8, (2, 3))
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros((2, 3))
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
```

这里，`(2, 3)` 是一个 [`Tuple`](@ref)，第一个参数——元素类型——是可选的，默认为 `Float64`。

## [Array literals](@id man-array-literals)

数组也可以直接用方括号构造；语法 `[A, B, C, ...]` 创建一个一维数组（即向量），其中包含以逗号分隔的参数作为其元素。结果数组的元素类型 ([`eltype`](@ref)) 是根据大括号内参数的类型自动确定的。如果所有参数都是相同类型，那么这就是它的 `eltype`。如果它们都有一个共同的 [promotion type](@ref conversion-and-promotion)，那么它们会被转换为该类型，使用 [`convert`](@ref)，并且该类型就是数组的 `eltype`。否则，将构造一个可以容纳任何内容的异构数组——一个 `Vector{Any}`；这包括字面量 `[]`，当没有给出参数时。[Array literal can be typed](@ref man-array-typed-literal) 的语法为 `T[A, B, C, ...]`，其中 `T` 是一个类型。

```jldoctest
julia> [1, 2, 3] # An array of `Int`s
3-element Vector{Int64}:
 1
 2
 3

julia> promote(1, 2.3, 4//5) # This combination of Int, Float64 and Rational promotes to Float64
(1.0, 2.3, 0.8)

julia> [1, 2.3, 4//5] # Thus that's the element type of this Array
3-element Vector{Float64}:
 1.0
 2.3
 0.8

julia> Float32[1, 2.3, 4//5] # Specify element type manually
3-element Vector{Float32}:
 1.0
 2.3
 0.8

julia> []
Any[]
```

### [Concatenation](@id man-array-concatenation)

如果方括号内的参数用单个分号（`;`）或换行符分隔，而不是用逗号，则它们的内容会*垂直连接*在一起，而不是将参数作为元素本身使用。

```jldoctest
julia> [1:2, 4:5] # Has a comma, so no concatenation occurs. The ranges are themselves the elements
2-element Vector{UnitRange{Int64}}:
 1:2
 4:5

julia> [1:2; 4:5]
4-element Vector{Int64}:
 1
 2
 4
 5

julia> [1:2
        4:5
        6]
5-element Vector{Int64}:
 1
 2
 4
 5
 6
```

同样，如果参数由制表符、空格或双分号分隔，则它们的内容会*水平连接*在一起。

```jldoctest
julia> [1:2  4:5  7:8]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [[1,2]  [4,5]  [7,8]]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [1 2 3] # Numbers can also be horizontally concatenated
1×3 Matrix{Int64}:
 1  2  3

julia> [1;; 2;; 3;; 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

单个分号（或换行符）和空格（或制表符）可以组合在一起，同时进行水平和垂直的连接。

```jldoctest
julia> [1 2
        3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [zeros(Int, 2, 2) [1; 2]
        [3 4]            5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [[1 1]; 2 3; [4 4]]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

空格（和制表符）具有比分号更高的优先级，首先执行任何水平连接，然后再连接结果。另一方面，使用双分号进行水平连接时，会在水平连接结果之前执行任何垂直连接。

```jldoctest
julia> [zeros(Int, 2, 2) ; [3 4] ;; [1; 2] ; 5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [1:2; 4;; 1; 3:4]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

就像 `;` 和 `;;` 在第一和第二维中连接一样，使用更多的分号扩展了这个相同的一般方案。分隔符中的分号数量指定了特定的维度，因此 `;;;` 在第三维中连接，`;;;;` 在第四维中，依此类推。较少的分号具有优先权，因此较低的维度通常会首先连接。

```jldoctest
julia> [1; 2;; 3; 4;; 5; 6;;;
        7; 8;; 9; 10;; 11; 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

像之前一样，水平连接的空格（和制表符）优先级高于任何数量的分号。因此，更高维的数组也可以通过首先指定它们的行来编写，其元素以类似于它们布局的方式文本排列：

```jldoctest
julia> [1 3 5
        2 4 6;;;
        7 9 11
        8 10 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> [1 2;;; 3 4;;;; 5 6;;; 7 8]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8

julia> [[1 2;;; 3 4];;;; [5 6];;; [7 8]]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8
```

尽管它们在第二维中都表示连接，但空格（或制表符）和 `;;` 不能出现在同一个数组表达式中，除非双分号仅作为“行续字符”。这允许单个水平连接跨越多行（而不会将换行符解释为垂直连接）。

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

终止分号也可以用于添加尾随长度为 1 的维度。

```jldoctest
julia> [1;;]
1×1 Matrix{Int64}:
 1

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3
```

更一般地，连接可以通过 [`cat`](@ref) 函数来完成。这些语法是函数调用的简写，它们本身是便利函数：

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

可以使用语法 `T[A, B, C, ...]` 构造具有特定元素类型的数组。这将构造一个一维数组，元素类型为 `T`，并初始化为包含元素 `A`、`B`、`C` 等。例如，`Any[x, y, z]` 构造一个可以包含任何值的异构数组。

连接语法同样可以以类型为前缀，以指定结果的元素类型。

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

理解提供了一种通用而强大的方式来构造数组。理解语法类似于数学中的集合构造符号：

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

此形式的含义是 `F(x,y,...)` 在变量 `x`、`y` 等取其给定值列表中的每个值时被评估。值可以指定为任何可迭代对象，但通常是像 `1:n` 或 `2:(n-1)` 这样的范围，或像 `[1.2, 3.4, 5.7]` 这样的显式值数组。结果是一个 N 维的稠密数组，其维度是变量范围 `rx`、`ry` 等的维度的连接，每个 `F(x,y,...)` 的评估返回一个标量。

以下示例计算当前元素及其左邻居和右邻居在一维网格上的加权平均值。

```julia-repl
julia> x = rand(8)
8-element Array{Float64,1}:
 0.843025
 0.869052
 0.365105
 0.699456
 0.977653
 0.994953
 0.41084
 0.809411

julia> [ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
6-element Array{Float64,1}:
 0.736559
 0.57468
 0.685417
 0.912429
 0.8446
 0.656511
```

结果数组的类型取决于计算元素的类型，就像 [array literals](@ref man-array-literals) 所做的那样。为了显式控制类型，可以在推导式前添加一个类型。例如，我们可以通过编写来请求单精度的结果：

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

推导式也可以在不使用方括号的情况下编写，生成一个称为生成器的对象。这个对象可以被迭代以按需生成值，而不是提前分配数组并存储它们（参见 [Iteration](@ref)）。例如，以下表达式在不分配内存的情况下对一系列进行求和：

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

在参数列表中编写具有多个维度的生成器表达式时，需要使用括号将生成器与后续参数分开：

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

所有在 `for` 后面的以逗号分隔的表达式都被解释为范围。添加括号可以让我们为 [`map`](@ref) 添加第三个参数：

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

生成器是通过内部函数实现的。就像语言中其他地方使用的内部函数一样，来自封闭作用域的变量可以在内部函数中“捕获”。例如，`sum(p[i] - q[i] for i=1:n)` 从封闭作用域中捕获了三个变量 `p`、`q` 和 `n`。被捕获的变量可能会带来性能挑战；请参见 [performance tips](@ref man-performance-captured)。

生成器和推导式中的范围可以通过编写多个 `for` 关键字来依赖于先前的范围：

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i]
6-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)
 (3, 1)
 (3, 2)
 (3, 3)
```

在这种情况下，结果总是 1-d。

生成的值可以使用 `if` 关键字进行过滤：

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

对 n 维数组 `A` 进行索引的一般语法是：

```
X = A[I_1, I_2, ..., I_n]
```

每个 `I_k` 可以是一个标量整数、一个整数数组或任何其他 [supported index](@ref man-supported-index-types)。这包括 [`Colon`](@ref) (`:`) 以选择整个维度内的所有索引，形式为 `a:c` 或 `a:b:c` 的范围以选择连续或跨步的子部分，以及布尔数组以选择其 `true` 索引处的元素。

如果所有索引都是标量，则结果 `X` 是数组 `A` 中的一个单一元素。否则，`X` 是一个数组，其维度数量与所有索引的维度总和相同。

如果所有索引 `I_k` 都是向量，例如，`X` 的形状将是 `(length(I_1), length(I_2), ..., length(I_n))`，其中 `X` 的位置 `i_1, i_2, ..., i_n` 包含值 `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]`。

示例：

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[1, 2, 1, 1] # all scalar indices
3

julia> A[[1, 2], [1], [1, 2], [1]] # all vector indices
2×1×2×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1
 2

[:, :, 2, 1] =
 5
 6

julia> A[[1, 2], [1], [1, 2], 1] # a mix of index types
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 5
 6
```

注意最后两种情况中结果数组的大小是不同的。

如果 `I_1` 被更改为一个二维矩阵，则 `X` 变成一个形状为 `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))` 的 `n+1` 维数组。这个矩阵增加了一个维度。

示例：

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2));

julia> A[[1 2; 1 2]]
2×2 Matrix{Int64}:
 1  2
 1  2

julia> A[[1 2; 1 2], 1, 2, 1]
2×2 Matrix{Int64}:
 5  6
 5  6
```

位置 `i_1, i_2, i_3, ..., i_{n+1}` 包含值 `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]`。所有用标量索引的维度都被丢弃。例如，如果 `J` 是一个索引数组，则 `A[2, J, 3]` 的结果是一个大小为 `size(J)` 的数组。它的第 `j` 个元素由 `A[2, J[j], 3]` 填充。

作为这种语法的一个特殊部分，`end` 关键字可以用来表示索引括号内每个维度的最后一个索引，这由被索引的最内层数组的大小决定。没有 `end` 关键字的索引语法等同于对 [`getindex`](@ref) 的调用：

```
X = getindex(A, I_1, I_2, ..., I_n)
```

示例：

```jldoctest
julia> x = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> x[2:3, 2:end-1]
2×2 Matrix{Int64}:
 6  10
 7  11

julia> x[1, [2 3; 4 1]]
2×2 Matrix{Int64}:
  5  9
 13  1
```

## [Indexed Assignment](@id man-indexed-assignment)

在 n 维数组 `A` 中赋值的一般语法是：

```
A[I_1, I_2, ..., I_n] = X
```

每个 `I_k` 可以是一个标量整数、一个整数数组或任何其他 [supported index](@ref man-supported-index-types)。这包括 [`Colon`](@ref) (`:`) 以选择整个维度内的所有索引，形式为 `a:c` 或 `a:b:c` 的范围以选择连续或跨步的子部分，以及布尔数组以选择其 `true` 索引处的元素。

如果所有索引 `I_k` 都是整数，则 `A` 中位置 `I_1, I_2, ..., I_n` 的值将被 `X` 的值覆盖，[`convert`](@ref) 如果必要的话，将其写入 `A` 的 [`eltype`](@ref)。

如果任何索引 `I_k` 本身是一个数组，则右侧的 `X` 也必须是一个与索引 `A[I_1, I_2, ..., I_n]` 结果具有相同形状的数组，或者是一个具有相同元素数量的向量。在 `A` 的位置 `I_1[i_1], I_2[i_2], ..., I_n[i_n]` 中的值将被 `X[i_1, i_2, ..., i_n]` 的值覆盖，如有必要则进行转换。逐元素赋值运算符 `.=` 可用于在选定位置上 [broadcast](@ref Broadcasting) `X`：

```
A[I_1, I_2, ..., I_n] .= X
```

就像在 [Indexing](@ref man-array-indexing) 中，`end` 关键字可以用来表示索引括号内每个维度的最后索引，这由被赋值的数组的大小决定。没有 `end` 关键字的索引赋值语法等同于对 [`setindex!`](@ref) 的调用：

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

示例：

```jldoctest
julia> x = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> x[3, 3] = -9;

julia> x[1:2, 1:2] = [-1 -4; -2 -5];

julia> x
3×3 Matrix{Int64}:
 -1  -4   7
 -2  -5   8
  3   6  -9
```

## [Supported index types](@id man-supported-index-types)

在表达式 `A[I_1, I_2, ..., I_n]` 中，每个 `I_k` 可以是一个标量索引、一个标量索引的数组，或者是一个表示标量索引数组的对象，并且可以通过 [`to_indices`](@ref) 转换为这样的对象：

1. 一个标量索引。默认情况下，这包括：

      * 非布尔整数
      * [`CartesianIndex{N}`](@ref)，其行为类似于跨多个维度的 `N`-元组整数（详见下文）
2. 一个标量索引的数组。这包括：

      * 整数的向量和多维数组
      * 空数组如 `[]`，选择不包含任何元素，例如 `A[[]]`（不要与 `A[]` 混淆）
      * 范围如 `a:c` 或 `a:b:c`，用于选择从 `a` 到 `c`（包括 `c`）的连续或间隔子部分。
      * 任何自定义的标量索引数组，只要是 `AbstractArray` 的子类型
      * `CartesianIndex{N}` 的数组（详见下文）
3. 一个表示标量索引数组的对象，可以通过 [`to_indices`](@ref) 转换为这样的对象。默认情况下，这包括：

      * [`Colon()`](@ref) (`:`)，表示整个维度内或整个数组中的所有索引
      * 布尔数组，选择其 `true` 索引处的元素（详见下文）

一些例子：

```jldoctest
julia> A = reshape(collect(1:2:18), (3, 3))
3×3 Matrix{Int64}:
 1   7  13
 3   9  15
 5  11  17

julia> A[4]
7

julia> A[[2, 5, 8]]
3-element Vector{Int64}:
  3
  9
 15

julia> A[[1 4; 3 8]]
2×2 Matrix{Int64}:
 1   7
 5  15

julia> A[[]]
Int64[]

julia> A[1:2:5]
3-element Vector{Int64}:
 1
 5
 9

julia> A[2, :]
3-element Vector{Int64}:
  3
  9
 15

julia> A[:, 3]
3-element Vector{Int64}:
 13
 15
 17

julia> A[:, 3:3]
3×1 Matrix{Int64}:
 13
 15
 17
```

### Cartesian indices

特殊的 `CartesianIndex{N}` 对象表示一个标量索引，它的行为类似于一个跨越多个维度的 `N` 元组整数。例如：

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

单独考虑，这可能看起来相对微不足道；`CartesianIndex` 只是将多个整数聚集到一个对象中，该对象表示单个多维索引。然而，当与其他索引形式和生成 `CartesianIndex` 的迭代器结合使用时，这可以产生非常优雅和高效的代码。请参见下面的 [Iteration](@ref)，以及一些更高级的示例，参见 [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration)。

`CartesianIndex{N}` 数组也受到支持。它们表示一组标量索引，每个索引跨越 `N` 个维度，从而实现一种有时称为逐点索引的索引形式。例如，它使得能够从上面访问 `A` 的第一个“页面”的对角元素：

```jldoctest cartesianindex
julia> page = A[:, :, 1]
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> page[[CartesianIndex(1, 1),
             CartesianIndex(2, 2),
             CartesianIndex(3, 3),
             CartesianIndex(4, 4)]]
4-element Vector{Int64}:
  1
  6
 11
 16
```

这可以用 [dot broadcasting](@ref man-vectorized) 更简单地表达，并通过将其与正常的整数索引结合（而不是将 `A` 的第一个 `page` 作为单独步骤提取）来实现。它甚至可以与 `:` 结合，以同时从两个页面提取两个对角线：

```jldoctest cartesianindex
julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), 1]
4-element Vector{Int64}:
  1
  6
 11
 16

julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), :]
4×2 Matrix{Int64}:
  1  17
  6  22
 11  27
 16  32
```

!!! warning
    `CartesianIndex` 和 `CartesianIndex` 数组与 `end` 关键字不兼容，无法表示维度的最后一个索引。请勿在可能包含 `CartesianIndex` 或其数组的索引表达式中使用 `end`。


### Logical indexing

通常被称为逻辑索引或使用逻辑掩码的索引，通过布尔数组索引选择其值为 `true` 的索引处的元素。通过布尔向量 `B` 进行索引实际上与通过 [`findall(B)`](@ref) 返回的整数向量进行索引是相同的。类似地，通过 `N` 维布尔数组进行索引实际上与通过其值为 `true` 的 `CartesianIndex{N}` 向量进行索引是相同的。逻辑索引必须是与其索引的维度形状相同的数组，或者它必须是提供的唯一索引，并且与其索引的数组的一维重塑视图的形状匹配。通常，直接使用布尔数组作为索引比先调用 [`findall`](@ref) 更有效。

```jldoctest
julia> x = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> x[:, [true false; false true; true false]]
2×3 Matrix{Int64}:
 1  5   9
 2  6  10

julia> mask = map(ispow2, x)
2×3×2 Array{Bool, 3}:
[:, :, 1] =
 1  0  0
 1  1  0

[:, :, 2] =
 0  0  0
 1  0  0

julia> x[mask]
4-element Vector{Int64}:
 1
 2
 4
 8

julia> x[vec(mask)] == x[mask] # we can also index with a single Boolean vector
true
```

### Number of indices

#### Cartesian indexing

索引一个 `N` 维数组的普通方法是使用恰好 `N` 个索引；每个索引选择其特定维度中的位置。例如，在三维数组 `A = rand(4, 3, 2)` 中，`A[2, 3, 1]` 将选择数组第一“页”中第三列的第二行的数字。这通常被称为 *笛卡尔索引*。

#### Linear indexing

当仅提供一个索引 `i` 时，该索引不再表示数组某一特定维度中的位置。相反，它使用列优先迭代顺序选择第 `i` 个元素，该顺序线性地遍历整个数组。这被称为 *线性索引*。它本质上将数组视为已被重塑为一个一维向量，内容为 [`vec`](@ref)。

```jldoctest linindexing
julia> A = [2 6; 4 7; 3 1]
3×2 Matrix{Int64}:
 2  6
 4  7
 3  1

julia> A[5]
7

julia> vec(A)[5]
7
```

一个线性索引可以通过 `CartesianIndices(A)[i]` 转换为 `CartesianIndex` 以进行笛卡尔索引（参见 [`CartesianIndices`](@ref)），而一组 `N` 个笛卡尔索引可以通过 `LinearIndices(A)[i_1, i_2, ..., i_N]` 转换为线性索引（参见 [`LinearIndices`](@ref)）。

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

重要的是要注意，这些转换的性能存在很大的不对称性。将线性索引转换为一组笛卡尔索引需要进行除法和取余，而反向操作只需乘法和加法。在现代处理器中，整数除法的速度可能比乘法慢10到50倍。虽然一些数组——如 [`Array`](@ref) 本身——是使用线性内存块实现的，并在其实现中直接使用线性索引，但其他数组——如 [`Diagonal`](@ref)——需要完整的笛卡尔索引集来进行查找（请参见 [`IndexStyle`](@ref) 以检查哪个是哪个）。

!!! warning
    当遍历数组的所有索引时，最好遍历 [`eachindex(A)`](@ref) 而不是 `1:length(A)`。在 `A` 是 `IndexCartesian` 的情况下，这样做不仅会更快，而且还会支持具有自定义索引的数组，例如 [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl)。如果只需要值，那么最好直接遍历数组，即 `for a in A`。


#### Omitted and extra indices

除了线性索引，`N` 维数组在某些情况下可以用少于或多于 `N` 个索引进行索引。

索引可以省略，如果未被索引的尾部维度的长度都是一。换句话说，只有在那些被省略的索引对于一个有效的索引表达式只有一个可能的值时，才能省略尾部索引。例如，一个大小为 `(3, 4, 2, 1)` 的四维数组可以仅用三个索引进行索引，因为被跳过的维度（第四维）的长度为一。请注意，线性索引优先于此规则。

```jldoctest
julia> A = reshape(1:24, 3, 4, 2, 1)
3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64:
[:, :, 1, 1] =
 1  4  7  10
 2  5  8  11
 3  6  9  12

[:, :, 2, 1] =
 13  16  19  22
 14  17  20  23
 15  18  21  24

julia> A[1, 3, 2] # Omits the fourth dimension (length 1)
19

julia> A[1, 3] # Attempts to omit dimensions 3 & 4 (lengths 2 and 1)
ERROR: BoundsError: attempt to access 3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64 at index [1, 3]

julia> A[19] # Linear indexing
19
```

当省略 `A[]` 中的 *所有* 索引时，这种语义提供了一种简单的习惯用法，可以检索数组中的唯一元素，同时确保数组中只有一个元素。

类似地，如果所有超出数组维度的索引都是 `1`（或更一般地说，是 `axes(A, d)` 的第一个也是唯一的元素，其中 `d` 是特定的维度编号），则可以提供超过 `N` 的索引。这允许像一列矩阵那样对向量进行索引，例如：

```jldoctest
julia> A = [8, 6, 7]
3-element Vector{Int64}:
 8
 6
 7

julia> A[2, 1]
6
```

## Iteration

遍历整个数组的推荐方法是

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

第一个构造用于当你需要每个元素的值，但不需要索引时。在第二个构造中，如果 `A` 是具有快速线性索引的数组类型，则 `i` 将是 `Int`；否则，它将是 `CartesianIndex`：

```jldoctest
julia> A = rand(4, 3);

julia> B = view(A, 1:3, 2:3);

julia> for i in eachindex(B)
           @show i
       end
i = CartesianIndex(1, 1)
i = CartesianIndex(2, 1)
i = CartesianIndex(3, 1)
i = CartesianIndex(1, 2)
i = CartesianIndex(2, 2)
i = CartesianIndex(3, 2)
```

!!! note
    与 `for i = 1:length(A)` 相比，使用 [`eachindex`](@ref) 迭代提供了一种高效的方式来遍历任何数组类型。此外，这还支持具有自定义索引的通用数组，例如 [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl)。


## Array traits

如果您编写一个自定义 [`AbstractArray`](@ref) 类型，您可以指定它具有快速线性索引，使用

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

此设置将导致对 `MyArray` 的 `eachindex` 迭代使用整数。如果您不指定此特性，将使用默认值 `IndexCartesian()`。

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

以下运算符支持数组：

1. 一元算术 – `-`, `+`
2. 二进制算术 – `-`、`+`、`*`、`/`、`\`、`^`
3. 比较 – `==`，`!=`，`≈` ([`isapprox`](@ref))，`≉`

为了方便数学和其他操作的向量化，Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)`，例如 `sin.(x)` 或 `min.(x, y)`，用于对数组或数组与标量的混合进行逐元素操作（一个 [Broadcasting](@ref) 操作）；这些操作在与其他点调用结合时具有“融合”成单个循环的额外优势，例如 `sin.(cos.(x))`。

此外，*每个* 二元运算符都支持一个 [dot version](@ref man-dot-operators)，可以应用于数组（以及数组和标量的组合）中，如 [fused broadcasting operations](@ref man-vectorized)，例如 `z .== sin.(x .* y)`。

请注意，比较运算符如 `==` 在整个数组上操作，给出一个布尔值答案。使用点运算符，如 `.==` 进行逐元素比较。（对于比较操作，如 `<`，*仅* 逐元素的 `.<` 版本适用于数组。）

Also notice the difference between `max.(a,b)`, which [`broadcast`](@ref)s [`max`](@ref) elementwise over `a` and `b`, and [`maximum(a)`](@ref), which finds the largest value within `a`. The same relationship holds for `min.(a, b)` and `minimum(a)`.

## Broadcasting

有时对不同大小的数组执行逐元素的二元操作是有用的，例如将一个向量添加到矩阵的每一列。一个低效的方法是将向量复制到矩阵的大小：

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

当维度变大时，这会造成浪费，因此 Julia 提供了 [`broadcast`](@ref)，它在数组参数中扩展单例维度以匹配另一个数组中的相应维度，而不使用额外的内存，并逐元素应用给定的函数：

```julia-repl
julia> broadcast(+, a, A)
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846

julia> b = rand(1,2)
1×2 Array{Float64,2}:
 0.867535  0.00457906

julia> broadcast(+, a, b)
2×2 Array{Float64,2}:
 1.71056  0.847604
 1.73659  0.873631
```

[Dotted operators](@ref man-dot-operators) 例如 `.+` 和 `.*` 等价于 `broadcast` 调用（除了它们会融合，因为 [described above](@ref man-array-and-vectorized-operators-and-functions)）。还有一个 [`broadcast!`](@ref) 函数来指定一个明确的目标（也可以通过 `.=` 赋值以融合的方式访问）。事实上，`f.(args...)` 等价于 `broadcast(f, args...)`，提供了一种方便的语法来广播任何函数（[dot syntax](@ref man-vectorized)）。嵌套的 "点调用" `f.(...)`（包括对 `.+` 等的调用）[automatically fuse](@ref man-dot-operators) 被合并为一个 `broadcast` 调用。

此外，[`broadcast`](@ref) 并不限于数组（请参见函数文档）；它还处理标量、元组和其他集合。 默认情况下，仅某些参数类型被视为标量，包括（但不限于）`Number`、`String`、`Symbol`、`Type`、`Function` 和一些常见的单例，如 `missing` 和 `nothing`。 所有其他参数都按元素进行迭代或索引。

```jldoctest
julia> convert.(Float32, [1, 2])
2-element Vector{Float32}:
 1.0
 2.0

julia> ceil.(UInt8, [1.2 3.4; 5.6 6.7])
2×2 Matrix{UInt8}:
 0x02  0x04
 0x06  0x07

julia> string.(1:3, ". ", ["First", "Second", "Third"])
3-element Vector{String}:
 "1. First"
 "2. Second"
 "3. Third"
```

有时，您希望一个容器（如数组）在广播时能够“保护”自己，避免广播对其所有元素进行迭代的行为。通过将其放置在另一个容器中（如单个元素 [`Tuple`](@ref)），广播将把它视为一个单一的值。

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

在 Julia 中，基本数组类型是抽象类型 [`AbstractArray{T,N}`](@ref)。它由维度数量 `N` 和元素类型 `T` 参数化。[`AbstractVector`](@ref) 和 [`AbstractMatrix`](@ref) 是一维和二维情况的别名。对 `AbstractArray` 对象的操作是使用更高级的运算符和函数定义的，这种方式与底层存储无关。这些操作通常作为任何特定数组实现的后备，正确地工作。

`AbstractArray` 类型包括任何模糊的数组类型，其实现可能与传统数组有很大不同。例如，元素可能是按需计算而不是存储的。然而，任何具体的 `AbstractArray{T,N}` 类型通常应该至少实现 [`size(A)`](@ref)（返回一个 `Int` 元组）、[`getindex(A, i)`](@ref) 和 [`getindex(A, i1, ..., iN)`](@ref getindex)；可变数组还应该实现 [`setindex!`](@ref)。建议这些操作具有接近常数的时间复杂度，否则某些数组函数可能会意外地变得缓慢。具体类型通常还应该提供一个 [`similar(A, T=eltype(A), dims=size(A))`](@ref) 方法，该方法用于为 [`copy`](@ref) 和其他不在原地的操作分配一个类似的数组。无论 `AbstractArray{T,N}` 如何在内部表示，`T` 是通过 *整数* 索引（`A[1, ..., 1]`，当 `A` 不为空时）返回的对象类型，而 `N` 应该是 [`size`](@ref) 返回的元组的长度。有关定义自定义 `AbstractArray` 实现的更多详细信息，请参见 [array interface guide in the interfaces chapter](@ref man-interface-array)。

`DenseArray` 是 `AbstractArray` 的一个抽象子类型，旨在包括所有以列优先顺序连续存储元素的数组（参见 [additional notes in Performance Tips](@ref man-performance-column-major)）。[`Array`](@ref) 类型是 `DenseArray` 的一个特定实例； [`Vector`](@ref) 和 [`Matrix`](@ref) 是一维和二维情况的别名。 除了所有 `AbstractArray` 所需的操作外，专门为 `Array` 实现的操作非常少；数组库的大部分是以通用方式实现的，这使得所有自定义数组的行为相似。

`SubArray` 是 `AbstractArray` 的一种特化，它通过与原始数组共享内存而不是复制它来执行索引。`SubArray` 是通过 [`view`](@ref) 函数创建的，该函数的调用方式与 [`getindex`](@ref) 相同（带有一个数组和一系列索引参数）。`4d61726b646f776e2e436f64652822222c2022766965772229_40726566` 的结果看起来与 `4d61726b646f776e2e436f64652822222c2022676574696e6465782229_40726566` 的结果相同，除了数据保留在原地。`4d61726b646f776e2e436f64652822222c2022766965772229_40726566` 将输入索引向量存储在 `SubArray` 对象中，稍后可以用来间接索引原始数组。通过在表达式或代码块前放置 [`@views`](@ref) 宏，该表达式中的任何 `array[...]` 切片将被转换为创建 `SubArray` 视图。

[`BitArray`](@ref) 是空间高效的“打包”布尔数组，存储每个布尔值一个位。它们可以类似于 `Array{Bool}` 数组（每个布尔值存储一个字节）使用，并且可以通过 `Array(bitarray)` 和 `BitArray(array)` 分别进行相互转换。

一个数组被称为“跨步”（strided），如果它在内存中以元素之间有明确间隔（跨步）的方式存储。一个具有支持的元素类型的跨步数组可以通过简单地传递其 [`pointer`](@ref) 和每个维度的跨步值，传递给外部（非Julia）库，如BLAS或LAPACK。[`stride(A, d)`](@ref) 是沿维度 `d` 的元素之间的距离。例如，内置的 `Array` 由 `rand(5,7,2)` 返回，其元素以列主序连续排列。这意味着第一维的跨步——同一列中元素之间的间隔——是 `1`：

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

第二维的步幅是同一行中元素之间的间距，跳过与单列中元素数量相同的元素（`5`）。同样，在两个“页面”之间跳跃（在第三维）需要跳过 `5*7 == 35` 个元素。该数组的 [`strides`](@ref) 是这三个数字的元组：

```julia-repl
julia> strides(A)
(1, 5, 35)
```

在这个特定的情况下，跳过的元素数量 *在内存中* 与跳过的 *线性索引* 数量相匹配。这仅适用于像 `Array`（和其他 `DenseArray` 子类型）这样的连续数组，通常并不成立。带有范围索引的视图是 *非连续* 跨步数组的一个很好的例子；考虑 `V = @view A[1:3:4, 2:2:6, 2:-1:1]`。这个视图 `V` 引用与 `A` 相同的内存，但跳过并重新排列了其中的一些元素。`V` 的第一维的步幅是 `3`，因为我们只从原始数组中选择每第三行：

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

这个视图同样从我们原始的 `A` 中选择每隔一列 — 因此在第二维度的索引之间移动时，它需要跳过相当于两个五元素列的内容：

```julia-repl
julia> stride(V, 2)
10
```

第三维度很有趣，因为它的顺序是反向的！因此，从第一页到第二页必须在内存中*向后*移动，因此在这个维度中的步幅是负的！

```julia-repl
julia> stride(V, 3)
-35
```

这意味着 `V` 的 `pointer` 实际上指向 `A` 的内存块中间，并且它引用了内存中向前和向后的元素。有关定义您自己的跨步数组的更多详细信息，请参见 [interface guide for strided arrays](@ref man-interface-strided-arrays)。[`StridedVector`](@ref) 和 [`StridedMatrix`](@ref) 是许多被视为跨步数组的内置数组类型的方便别名，允许它们调度以选择专门的实现，这些实现使用仅指针和跨步调用高度调优和优化的 BLAS 和 LAPACK 函数。

值得强调的是，步幅是关于内存中的偏移量，而不是索引。如果您想在线性（单索引）索引和笛卡尔（多索引）索引之间进行转换，请参见 [`LinearIndices`](@ref) 和 [`CartesianIndices`](@ref)。

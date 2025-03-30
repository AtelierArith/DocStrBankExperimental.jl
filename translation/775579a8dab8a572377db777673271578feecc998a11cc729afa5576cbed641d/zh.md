```
;
```

`;` 在 Julia 中的作用与许多 C 类语言相似，用于分隔前一个语句的结束。

`;` 在行末并不是必需的，但可以用于在单行中分隔语句或将语句连接成一个表达式。

在 REPL 中，在行末添加 `;` 将抑制该表达式结果的打印。

在函数声明中，以及在调用中可选地，`;` 用于分隔常规参数和关键字参数。

在数组字面量中，用分号分隔的参数其内容会被连接在一起。由单个 `;` 组成的分隔符会垂直连接（即沿着第一个维度），`;;` 会水平连接（第二维度），`;;;` 会沿着第三维度连接，等等。这样的分隔符也可以在方括号的最后位置使用，以添加长度为 1 的尾随维度。

在括号内的首个位置的 `;` 可以用于构造命名元组。相同的 `(; ...)` 语法在赋值的左侧允许进行属性解构。

在标准 REPL 中，在空行上输入 `;` 将切换到 shell 模式。

# 示例

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # 如果没有 `;` 或尾随逗号，这将赋值给 x
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # 使用属性解构设置变量 b 和 x

julia> b, x
(2, 1)

julia> ; # 输入 `;` 后，提示符（就地）更改为: shell>
shell> echo hello
hello
```

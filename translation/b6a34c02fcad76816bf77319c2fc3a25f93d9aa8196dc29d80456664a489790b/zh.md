```
let
```

`let` 块创建一个新的硬作用域，并可选地引入新的局部绑定。

就像 [其他作用域构造](@ref man-scope-table) 一样，`let` 块定义了新引入的局部变量可访问的代码块。此外，语法对以逗号分隔的赋值和可能出现在与 `let` 同一行的变量名具有特殊含义：

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

在这一行引入的变量是 `let` 块的局部变量，赋值按顺序求值，每个右侧的值在不考虑左侧名称的作用域中求值。因此，写出 `let x = x` 这样的代码是有意义的，因为两个 `x` 变量是不同的，左侧的 `x` 在局部作用域中遮蔽了外部作用域的 `x`。这甚至可以成为一个有用的习惯用法，因为每次进入局部作用域时都会新创建局部变量，但这仅在通过闭包存活于其作用域的变量的情况下可观察到。没有赋值的 `let` 变量，例如上面示例中的 `var2`，声明了一个尚未绑定到值的新局部变量。

相比之下， [`begin`](@ref) 块也将多个表达式组合在一起，但不引入作用域或具有特殊的赋值语法。

### 示例

在下面的函数中，有一个单一的 `x` 被 `map` 迭代更新三次。返回的闭包都引用了那个 `x` 的最终值：

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generic function with 1 method)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

然而，如果我们添加一个引入 *新* 局部变量的 `let` 块，我们将得到三个不同的变量被捕获（每次迭代一个），即使我们选择使用（遮蔽）相同的名称。

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generic function with 1 method)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

所有引入新局部变量的作用域构造在重复运行时都表现得如此；`let` 的独特特征是其能够简洁地声明新的 `local`，这些 `local` 可能遮蔽同名的外部变量。例如，直接使用 `do` 函数的参数同样捕获了三个不同的变量：

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generic function with 1 method)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```

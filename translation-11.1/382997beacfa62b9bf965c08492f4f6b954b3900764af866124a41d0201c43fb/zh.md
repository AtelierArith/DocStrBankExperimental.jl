```
Base.@assume_effects 设置... [ex]
```

覆盖编译器的效果建模。此宏可以在几种上下文中使用：

1. 在方法定义之前立即使用，以覆盖应用方法的整个效果建模。
2. 在没有任何参数的函数体内使用，以覆盖封闭方法的整个效果建模。
3. 应用于代码块，以覆盖应用代码块的局部效果建模。

# 示例

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # 用法 1:
           # 这个 :terminates_locally 允许 `fact` 被常量折叠
           res = 1
           0 ≤ x < 20 || error("bad fact")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generic function with 1 method)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # 用法 2:
               # 这个 :terminates_locally 允许这个匿名函数被常量折叠
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("bad fact")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("bad fact")
               # 用法 3:
               # 使用这个 :terminates_locally 注释，编译器跳过在这个 `while` 块内的污点
               # `:terminates` 效果，允许父级匿名函数被常量折叠
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    使用 `Base.@assume_effects` 需要 Julia 版本 1.8。


!!! compat "Julia 1.10"
    在函数体内的使用至少需要 Julia 1.10。


!!! compat "Julia 1.11"
    代码块注释至少需要 Julia 1.11。


!!! warning
    不当使用此宏会导致未定义行为（包括崩溃、错误答案或其他难以追踪的错误）。请谨慎使用，并仅在绝对必要时作为最后手段使用。即使在这种情况下，您也应该采取一切可能的步骤来最小化效果断言的强度（例如，如果 `:nothrow` 足够，则不要使用 `:total`）。


一般来说，每个 `setting` 值对函数的行为做出断言，而不要求编译器证明这种行为确实为真。这些断言适用于所有世界年龄。因此，建议限制使用可能在以后扩展以使假设无效的通用函数（这将导致未定义行为）。

支持以下 `setting`。

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# 扩展帮助

---

## `:consistent`

`:consistent` 设置断言对于相等 (`===`) 的输入：

  * 终止的方式（返回值、异常、非终止）将始终相同。
  * 如果方法返回，结果将始终相等。

!!! note
    这特别意味着该方法不得返回新分配的可变对象。多次分配可变对象（即使内容相同）也不相等。


!!! note
    `:consistent`-cy 断言是按世界年龄进行的。更正式地说，写 $fᵢ$ 为在世界年龄 $i$ 中对 $f$ 的评估，则此设置要求：

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    然而，对于两个世界年龄 $i$ 和 $j$，使得 $i ≠ j$，我们可能有 $fᵢ(x) ≢ fⱼ(y)$。

    进一步的含义是 `:consistent` 函数不得使其返回值依赖于堆的状态或任何其他在给定世界年龄下不恒定的全局状态。


!!! note
    `:consistent`-cy 包括优化器执行的所有合法重写。例如，浮点快速数学操作不被视为 `:consistent`，因为优化器可能重写它们，导致输出在相同世界年龄下不 `:consistent`（例如，因为一个在解释器中运行，而另一个被优化了）。


!!! note
    如果 `:consistent` 函数通过抛出异常终止，则该异常本身不需要满足上述的相等性要求。


---

## `:effect_free`

`:effect_free` 设置断言该方法没有外部语义可见的副作用。以下是外部语义可见副作用的不完整列表：

  * 改变全局变量的值。
  * 变更堆（例如数组或可变值），除非如下所述
  * 改变方法表（例如通过调用 eval）
  * 文件/网络等 I/O
  * 任务切换

然而，以下内容显然不是语义可见的，即使它们可能是可观察的：

  * 内存分配（可变和不可变）
  * 经过的时间
  * 垃圾收集
  * 对于生命周期不超过方法的对象的堆变更（即在方法中分配且不逃逸的对象）。
  * 返回值（虽然是外部可见的，但不是副作用）

这里的经验法则是，外部可见的副作用是任何会影响程序其余部分执行的内容，如果该函数未被执行。

!!! note
    `:effect_free` 断言适用于方法本身以及方法执行的任何代码。请记住，该断言必须对所有世界年龄有效，并相应地限制使用此断言。


---

## `:nothrow`

`:nothrow` 设置断言该方法不会抛出异常（即将始终返回一个值或永不返回）。

!!! note
    允许 `:nothrow` 注释的方法在内部使用异常处理，只要异常不在方法本身中重新抛出。


!!! note
    如果方法的执行可能引发 `MethodError` 和类似异常，则该方法不被视为 `:nothrow`。但是，请注意，像 `StackOverflowError` 或 `InterruptException` 这样的环境依赖错误不被此效果建模，因此可能导致 `StackOverflowError` 的方法不一定需要 `!:nothrow`（尽管通常也应该是 `!:terminates`）。


---

## `:terminates_globally`

`:terminates_globally` 设置断言该方法最终会终止（无论是正常还是异常），即不会无限循环。

!!! note
    此 `:terminates_globally` 断言涵盖任何被注释方法调用的其他方法。


!!! note
    编译器将视此为该方法相对*快速*终止的强烈指示，并且可能（如果其他合法）在编译时调用此方法。即在一个*技术上*终止但*实际上*不终止的方法上注释此设置是个坏主意。


---

## `:terminates_locally`

`:terminates_locally` 设置类似于 `:terminates_globally`，但仅适用于注释方法内的语法控制流。因此，这是一个更弱（因此更安全）的断言，允许在方法调用其他不终止的方法时可能出现非终止的情况。

!!! note
    `:terminates_globally` 隐含 `:terminates_locally`。


---

## `:notaskstate`

`:notaskstate` 设置断言该方法不使用或修改本地任务状态（任务本地存储、随机数生成器状态等），因此可以安全地在任务之间移动而不会产生可观察的结果。

!!! note
    异常处理的实现使用存储在任务对象中的状态。然而，目前此状态不被视为 `:notaskstate` 的范围，并且使用 `:nothrow` 效果单独跟踪。


!!! note
    `:notaskstate` 断言涉及*当前运行任务*的状态。如果通过其他方式获得对 `Task` 对象的引用，而不考虑哪个任务是*当前*运行的，则 `:notaskstate` 效果不需要被污染。即使该任务对象恰好与当前运行的任务相等，这也是如此。


!!! note
    访问任务状态通常还会导致其他效果的污染，例如 `:effect_free`（如果修改了任务状态）或 `:consistent`（如果在计算结果时使用了任务状态）。特别是，代码不是 `:notaskstate`，但同时是 `:effect_free` 和 `:consistent` 的代码仍然可能被消除死代码，因此提升为 `:total`。


---

## `:inaccessiblememonly`

`:inaccessiblememonly` 设置断言该方法不访问或修改外部可访问的可变内存。这意味着该方法可以访问或修改新分配对象的可变内存，该内存在返回方法之前对其他方法或顶级执行不可访问，但不能访问或修改任何可变全局状态或其参数指向的可变内存。

!!! note
    以下是使此假设无效的不完整示例：

      * 访问可变全局变量的全局引用或 `getglobal` 调用
      * 对非常量全局变量执行赋值的全局赋值或 `setglobal!` 调用
      * 改变全局可变变量字段的 `setfield!` 调用


!!! note
    此 `:inaccessiblememonly` 断言涵盖任何被注释方法调用的其他方法。


---

## `:noub`

`:noub` 设置断言该方法不会执行任何未定义行为（对于任何输入）。请注意，未定义行为在技术上可能导致该方法违反任何其他效果断言（例如 `:consistent` 或 `:effect_free`），但我们不对其建模，并假设不存在未定义行为。

---

## `:nortcall`

`:nortcall` 设置断言该方法不调用 `Core.Compiler.return_type`，并且该方法可能调用的任何其他方法也不调用 `Core.Compiler.return_type`。

!!! note
    精确地说，当在运行时未调用 `Core.Compiler.return_type` 时，可以使用此断言；即，当 `Core.Compiler.return_type` 的结果在编译时已知并且调用被优化器消除时。然而，由于 `Core.Compiler.return_type` 的结果是否在编译时折叠在很大程度上取决于编译器的实现，因此如果相关方法以任何形式使用 `Core.Compiler.return_type`，则通常很危险地断言这一点。


---

## `:foldable`

此设置是编译器要求保证在编译时常量折叠调用的效果集合的便捷快捷方式。它目前等同于以下 `setting`：

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    此列表特别不包括 `:nothrow`。编译器仍将尝试常量传播并在编译时注意任何抛出的错误。然而，请注意，根据 `:consistent`-cy 的要求，任何此类注释调用必须在给定相同参数值时一致地抛出。


!!! note
    函数内部的显式 `@inbounds` 注释也将禁用常量折叠，并且不会被 `:foldable` 覆盖。


---

## `:removable`

此设置是编译器要求保证在编译时删除未使用结果的调用的效果集合的便捷快捷方式。它目前等同于以下 `setting`：

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

此 `setting` 是可能的最大效果集合。它目前隐含以下其他 `setting`：

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total` 是一个非常强的断言，并且在未来的 Julia 版本中可能会获得额外的语义（例如，如果添加了额外的效果并包含在 `:total` 的定义中）。因此，应该谨慎使用。尽可能地，优先使用特定应用所需的最小效果断言集合。在适用大量效果覆盖的函数集的情况下，建议使用自定义宏，而不是使用 `:total`。


---

## 否定效果

效果名称可以通过 `!` 前缀来表示该效果应从先前的元效果中移除。例如，`:total !:nothrow` 表示虽然调用通常是完全的，但它可能会抛出。

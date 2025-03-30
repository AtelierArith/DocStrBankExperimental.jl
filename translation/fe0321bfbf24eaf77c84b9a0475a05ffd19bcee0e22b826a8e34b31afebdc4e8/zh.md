```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

请阅读 [release notes](NEWS.md) 以查看自上次发布以来发生了什么变化。

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

以下是一些在学习和使用Julia编程语言时会有用的链接的非详尽列表。

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

科学计算传统上需要最高的性能，但领域专家在日常工作中大多转向了较慢的动态语言。我们认为有许多充分的理由在这些应用中优先选择动态语言，并且我们不期望它们的使用会减少。幸运的是，现代语言设计和编译技术使得几乎可以消除性能权衡，并提供一个足够高效的单一环境，既适合原型开发，又足够高效以部署性能密集型应用程序。Julia编程语言正好填补了这一角色：它是一种灵活的动态语言，适合科学和数值计算，其性能可与传统的静态类型语言相媲美。

因为Julia的编译器与Python或R等语言使用的解释器不同，您可能会发现Julia的性能在开始时并不直观。如果您发现某些东西运行缓慢，我们强烈建议您在尝试其他方法之前先阅读[Performance Tips](@ref man-performance-tips)部分。一旦您理解了Julia的工作原理，编写几乎与C一样快的代码就变得容易了。

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia features optional typing, multiple dispatch, and good performance, achieved using type inference and [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (and [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)), implemented using [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine). It is multi-paradigm, combining features of imperative, functional, and object-oriented programming. Julia provides ease and expressiveness for high-level numerical computing, in the same way as languages such as R, MATLAB, and Python, but also supports general programming. To achieve this, Julia builds upon the lineage of mathematical programming languages, but also borrows much from popular dynamic languages, including [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)), and [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)).

Julia与典型动态语言的最显著区别是：

  * 核心语言的限制非常少；Julia Base 和标准库都是用 Julia 本身编写的，包括整数运算等基本操作。
  * 一种丰富的类型语言，用于构造和描述对象，也可以选择性地用于进行类型声明。
  * 能够通过 [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch) 定义函数在多种参数类型组合下的行为。
  * 自动生成高效的、针对不同参数类型的专用代码
  * 良好的性能，接近于静态编译语言如 C 的水平

尽管有时人们会将动态语言称为“无类型”，但它们绝对不是。每个对象，无论是原始类型还是用户定义的类型，都有一个类型。然而，大多数动态语言缺乏类型声明，这意味着无法向编译器指示值的类型，并且通常无法明确讨论类型。另一方面，在静态语言中，虽然可以（通常必须）为编译器注释类型，但类型仅在编译时存在，无法在运行时进行操作或表达。在Julia中，类型本身就是运行时对象，也可以用来向编译器传达信息。

### [What Makes Julia, Julia?](@id man-what-makes-julia)

虽然普通程序员不需要显式使用类型或多重分发，但它们是Julia的核心统一特性：函数是在不同的参数类型组合上定义的，并通过调度到最具体的匹配定义来应用。这个模型非常适合数学编程，因为在传统的面向对象分发中，第一个参数“拥有”一个操作是不自然的。运算符只是具有特殊符号的函数——要将加法扩展到新的用户定义数据类型，您需要为`+`函数定义新的方法。现有代码随后无缝地应用于新的数据类型。

部分原因是运行时类型推断（辅以可选的类型注释），部分原因是项目从一开始就非常注重性能，Julia 的计算效率超过了其他动态语言，甚至与静态编译语言相媲美。对于大规模数值问题，速度一直是、现在仍然是，并且可能永远是至关重要的：过去几十年中，处理的数据量轻松跟上了摩尔定律。

### [Advantages of Julia](@id man-advantages-of-julia)

Julia旨在在单一语言中创造前所未有的易用性、强大功能和高效性。除了上述优点，Julia相较于可比系统的一些优势包括：

  * 自由和开源 ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * 用户定义的类型与内置类型一样快速且紧凑
  * 无需对代码进行向量化以提高性能；未向量化的代码也很快。
  * 旨在并行和分布式计算
  * 轻量级“绿色”线程 ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * 不干扰但强大的类型系统
  * 优雅且可扩展的数值及其他类型的转换和提升
  * 高效支持 [Unicode](https://en.wikipedia.org/wiki/Unicode)，包括但不限于 [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * 直接调用 C 函数（无需包装器或特殊 API）
  * 强大的类似于 shell 的功能，用于管理其他进程
  * Lisp 风格的宏和其他元编程工具

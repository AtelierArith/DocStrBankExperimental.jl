# Essentials

## Introduction

Julia Base 包含一系列适合进行科学和数值计算的函数和宏，但其范围也与许多通用编程语言一样广泛。 额外的功能来自于一个不断增长的集合 [available packages](https://julialang.org/packages/)。 函数按主题分组如下。

一些一般性备注：

  * 要使用模块函数，请使用 `import Module` 导入模块，并使用 `Module.fn(x)` 来使用这些函数。
  * 或者，`using Module` 将把所有导出的 `Module` 函数导入到当前命名空间。
  * 根据约定，以感叹号（`!`）结尾的函数名称会修改其参数。一些函数同时具有修改版本（例如，`sort!`）和非修改版本（`sort`）。

`Base` 和标准库的行为是稳定的，如 [SemVer](https://semver.org/) 中定义的，前提是它们是有文档记录的；即，包含在 [Julia documentation](https://docs.julialang.org/) 中，并且没有标记为不稳定。有关更多信息，请参见 [API FAQ](@ref man-api)。

## Getting Around

```@docs
Base.exit
Base.atexit
Base.isinteractive
Base.summarysize
Base.__precompile__
Base.include
Main.include
Base.include_string
Base.include_dependency
__init__
Base.which(::Any, ::Any)
Base.methods
Base.@show
ans
err
Base.active_project
Base.set_active_project
```

## [Keywords](@id Keywords)

这是Julia中保留关键字的列表：`baremodule`，`begin`，`break`，`catch`，`const`，`continue`，`do`，`else`，`elseif`，`end`，`export`，`false`，`finally`，`for`，`function`，`global`，`if`，`import`，`let`，`local`，`macro`，`module`，`quote`，`return`，`struct`，`true`，`try`，`using`，`while`。这些关键字不能用作变量名。

以下两个词序列是保留的：`abstract type`，`mutable struct`，`primitive type`。但是，您可以创建名为：`abstract`，`mutable`，`primitive` 和 `type` 的变量。

最后：`where` 被解析为用于编写参数化方法和类型定义的中缀运算符；`in` 和 `isa` 被解析为中缀运算符；`public` 在开始顶层语句时被解析为关键字；`outer` 在用于修改 `for` 循环的迭代规范中的变量作用域时被解析为关键字；而 `as` 被用作关键字，以重命名通过 `import` 或 `using` 引入作用域的标识符。不过，允许创建名为 `where`、`in`、`isa`、`outer` 和 `as` 的变量。

```@docs
module
export
public
import
using
as
baremodule
function
macro
return
do
begin
end
let
if
for
while
break
continue
try
finally
quote
local
global
outer
const
struct
mutable struct
@kwdef
abstract type
primitive type
where
...
;
=
?:
```

## Standard Modules

```@docs
Main
Core
Base
```

## Base Submodules

```@docs
Base.Broadcast
Base.Docs
Base.Iterators
Base.Libc
Base.Meta
Base.StackTraces
Base.Sys
Base.Threads
Base.GC
```

## All Objects

```@docs
Core.:(===)
Core.isa
Base.isequal
Base.isless
Base.isunordered
Base.ifelse
Core.typeassert
Core.typeof
Core.tuple
Base.ntuple
Base.objectid
Base.hash
Base.finalizer
Base.finalize
Base.copy
Base.deepcopy
Base.getproperty
Base.setproperty!
Base.replaceproperty!
Base.swapproperty!
Base.modifyproperty!
Base.setpropertyonce!
Base.propertynames
Base.hasproperty
Core.getfield
Core.setfield!
Core.modifyfield!
Core.replacefield!
Core.swapfield!
Core.setfieldonce!
Core.isdefined
Base.@isdefined
Base.convert
Base.promote
Base.oftype
Base.widen
Base.identity
Base.WeakRef
```

## Properties of Types

### Type relations

```@docs
Base.supertype
Core.Type
Core.DataType
Core.:(<:)
Base.:(>:)
Base.typejoin
Base.typeintersect
Base.promote_type
Base.promote_rule
Base.promote_typejoin
Base.isdispatchtuple
```

### Declared structure

```@docs
Base.ismutable
Base.isimmutable
Base.ismutabletype
Base.isabstracttype
Base.isprimitivetype
Base.issingletontype
Base.isstructtype
Base.nameof(::DataType)
Base.fieldnames
Base.fieldname
Core.fieldtype
Base.fieldtypes
Base.fieldcount
Base.hasfield
Core.nfields
Base.isconst
Base.isfieldatomic
```

### Memory layout

```@docs
Base.sizeof(::Type)
Base.isconcretetype
Base.isbits
Base.isbitstype
Base.fieldoffset
Base.datatype_alignment
Base.datatype_haspadding
Base.datatype_pointerfree
```

### Special values

```@docs
Base.typemin
Base.typemax
Base.floatmin
Base.floatmax
Base.maxintfloat
Base.eps(::Type{<:AbstractFloat})
Base.eps(::AbstractFloat)
Base.instances
```

## Special Types

```@docs
Core.Any
Core.Union
Union{}
Core.UnionAll
Core.Tuple
Core.NTuple
Core.NamedTuple
Base.@NamedTuple
Base.@Kwargs
Base.Val
Core.Vararg
Core.Nothing
Base.isnothing
Base.notnothing
Base.Some
Base.something
Base.@something
Base.Enums.Enum
Base.Enums.@enum
Core.Expr
Core.Symbol
Core.Symbol(x...)
Core.Module
```

## Generic Functions

```@docs
Core.Function
Base.hasmethod
Core.applicable
Base.isambiguous
Core.invoke
Base.@invoke
Base.invokelatest
Base.@invokelatest
new
Base.:(|>)
Base.:(∘)
Base.ComposedFunction
Base.splat
Base.Fix1
Base.Fix2
```

## Syntax

```@docs
Core.eval
Main.eval
Base.@eval
Base.evalfile
Base.esc
Base.@inbounds
Base.@boundscheck
Base.@propagate_inbounds
Base.@inline
Base.@noinline
Base.@nospecialize
Base.@specialize
Base.@nospecializeinfer
Base.@constprop
Base.gensym
Base.@gensym
var"name"
Base.@goto
Base.@label
Base.@simd
Base.@polly
Base.@generated
Base.@assume_effects
```

## Managing deprecations

```@docs
Base.@deprecate
Base.depwarn
```

## Missing Values

```@docs
Base.Missing
Base.missing
Base.coalesce
Base.@coalesce
Base.ismissing
Base.skipmissing
Base.nonmissingtype
```

## System

```@docs
Base.run
Base.devnull
Base.success
Base.process_running
Base.process_exited
Base.kill(::Base.Process, ::Integer)
Base.Sys.set_process_title
Base.Sys.get_process_title
Base.ignorestatus
Base.detach
Base.Cmd
Base.setenv
Base.addenv
Base.withenv
Base.setcpuaffinity
Base.pipeline(::Any, ::Any, ::Any, ::Any...)
Base.pipeline(::Base.AbstractCmd)
Base.Libc.gethostname
Base.Libc.getpid
Base.Libc.time()
Base.time_ns
Base.@time
Base.@showtime
Base.@timev
Base.@timed
Base.@elapsed
Base.@allocated
Base.@allocations
Base.@lock_conflicts
Base.EnvDict
Base.ENV
Base.Sys.STDLIB
Base.Sys.isunix
Base.Sys.isapple
Base.Sys.islinux
Base.Sys.isbsd
Base.Sys.isfreebsd
Base.Sys.isopenbsd
Base.Sys.isnetbsd
Base.Sys.isdragonfly
Base.Sys.iswindows
Base.Sys.windows_version
Base.Sys.free_memory
Base.Sys.total_memory
Base.Sys.free_physical_memory
Base.Sys.total_physical_memory
Base.Sys.uptime
Base.Sys.isjsvm
Base.Sys.loadavg
Base.Sys.isexecutable
Base.Sys.isreadable
Base.Sys.iswritable
Base.Sys.username
Base.@static
```

## Versioning

```@docs
Base.VersionNumber
Base.@v_str
```

## Errors

```@docs
Base.error
Core.throw
Base.rethrow
Base.backtrace
Base.catch_backtrace
Base.current_exceptions
Base.@assert
Base.Experimental.register_error_hint
Base.Experimental.show_error_hints
Base.ArgumentError
Base.AssertionError
Core.BoundsError
Base.CompositeException
Base.DimensionMismatch
Core.DivideError
Core.DomainError
Base.EOFError
Core.ErrorException
Core.InexactError
Core.InterruptException
Base.KeyError
Base.LoadError
Base.MethodError
Base.MissingException
Core.OutOfMemoryError
Core.ReadOnlyMemoryError
Core.OverflowError
Base.ProcessFailedException
Base.TaskFailedException
Core.StackOverflowError
Base.SystemError
Core.TypeError
Core.UndefKeywordError
Core.UndefRefError
Core.UndefVarError
Base.StringIndexError
Base.InitError
Base.retry
Base.ExponentialBackOff
```

## Events

```@docs
Base.Timer(::Function, ::Real)
Base.Timer
Base.AsyncCondition
Base.AsyncCondition(::Function)
```

## Reflection

```@docs
Base.nameof(::Module)
Base.parentmodule
Base.pathof(::Module)
Base.pkgdir(::Module)
Base.pkgversion(::Module)
Base.moduleroot
__module__
__source__
Base.@__MODULE__
Base.@__FILE__
Base.@__DIR__
Base.@__LINE__
Base.fullname
Base.names
Base.isexported
Base.ispublic
Base.nameof(::Function)
Base.functionloc(::Any, ::Any)
Base.functionloc(::Method)
Base.@locals
Core.getglobal
Core.setglobal!
Core.modifyglobal!
Core.swapglobal!
Core.setglobalonce!
Core.replaceglobal!
```

## Documentation

(另见 [documentation](@ref man-documentation) 章节。)

```@docs
Base.@doc
Docs.HTML
Docs.Text
Docs.hasdoc
Docs.undocumented_names
```

## Code loading

```@docs
Base.identify_package
Base.locate_package
Base.require
Base.compilecache
Base.isprecompiled
Base.get_extension
```

## Internals

```@docs
Base.GC.gc
Base.GC.enable
Base.GC.@preserve
Base.GC.safepoint
Base.GC.enable_logging
Base.GC.logging_enabled
Meta.lower
Meta.@lower
Meta.parse(::AbstractString, ::Int)
Meta.parse(::AbstractString)
Meta.ParseError
Core.QuoteNode
Base.macroexpand
Base.@macroexpand
Base.@macroexpand1
Base.code_lowered
Base.code_typed
Base.precompile
Base.jit_total_bytes
```

## Meta

```@docs
Meta.quot
Meta.isexpr
Meta.isidentifier
Meta.isoperator
Meta.isunaryoperator
Meta.isbinaryoperator
Meta.show_sexpr
```

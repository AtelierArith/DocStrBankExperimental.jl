# Essentials

## Introduction

Julia Base, bilimsel ve sayısal hesaplama yapmak için uygun bir dizi fonksiyon ve makro içerir, ancak birçok genel amaçlı programlama dilinin sunduğu kadar geniştir. Ek işlevsellik, büyüyen bir [available packages](https://julialang.org/packages/) koleksiyonundan mevcuttur. Fonksiyonlar aşağıda konu başlıklarına göre gruplandırılmıştır.

Bazı genel notlar:

  * Modül fonksiyonlarını kullanmak için, modülü içe aktarmak için `import Modül` kullanın ve fonksiyonları kullanmak için `Modül.fn(x)` kullanın.
  * Alternatif olarak, `using Module` mevcut ad alanına tüm dışa aktarılan `Module` işlevlerini içe aktarır.
  * Gelenek gereği, ünlem işareti (`!`) ile biten fonksiyon adları argümanlarını değiştirir. Bazı fonksiyonlar hem değiştiren (örneğin, `sort!`) hem de değiştirmeyen (`sort`) sürümlere sahiptir.

The behaviors of `Base` and standard libraries are stable as defined in [SemVer](https://semver.org/) only if they are documented; i.e., included in the [Julia documentation](https://docs.julialang.org/) and not marked as unstable. See [API FAQ](@ref man-api) for more information.

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

Bu, Julia'daki ayrılmış anahtar kelimelerin listesidir: `baremodule`, `begin`, `break`, `catch`, `const`, `continue`, `do`, `else`, `elseif`, `end`, `export`, `false`, `finally`, `for`, `function`, `global`, `if`, `import`, `let`, `local`, `macro`, `module`, `quote`, `return`, `struct`, `true`, `try`, `using`, `while`. Bu anahtar kelimeler, değişken adı olarak kullanılamaz.

Aşağıdaki iki kelimelik diziler ayrılmıştır: `abstract type`, `mutable struct`, `primitive type`. Ancak, şu isimlerle değişkenler oluşturabilirsiniz: `abstract`, `mutable`, `primitive` ve `type`.

Sonunda: `where`, parametreli yöntem ve tür tanımları yazmak için bir infiks operatör olarak ayrıştırılır; `in` ve `isa` infiks operatörler olarak ayrıştırılır; `public`, bir üst düzey ifadeye başladığında bir anahtar kelime olarak ayrıştırılır; `outer`, bir `for` döngüsündeki bir yineleme spesifikasyonunda bir değişkenin kapsamını değiştirmek için kullanıldığında bir anahtar kelime olarak ayrıştırılır; ve `as`, `import` veya `using` ile kapsam içine alınan bir tanımlayıcıyı yeniden adlandırmak için bir anahtar kelime olarak kullanılır. `where`, `in`, `isa`, `outer` ve `as` adında değişkenler oluşturulmasına izin verilmektedir, ancak.

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

(Bkz. [documentation](@ref man-documentation) bölümü.)

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

# Essentials

## Introduction

Julia Base는 과학 및 수치 계산을 수행하는 데 적합한 다양한 함수와 매크로를 포함하고 있지만, 많은 범용 프로그래밍 언어의 기능만큼 광범위합니다. 추가 기능은 증가하는 [available packages](https://julialang.org/packages/) 컬렉션에서 사용할 수 있습니다. 함수는 아래 주제별로 그룹화되어 있습니다.

일반적인 메모:

  * 모듈 함수를 사용하려면 `import Module`을 사용하여 모듈을 가져오고, `Module.fn(x)`을 사용하여 함수를 사용합니다.
  * 대신에, `using Module`은 모든 내보낸 `Module` 함수를 현재 네임스페이스로 가져옵니다.
  * 관례적으로, 느낌표(`!`)로 끝나는 함수 이름은 그 인수를 수정합니다. 일부 함수는 수정하는 버전(예: `sort!`)과 수정하지 않는 버전(`sort`)을 모두 가지고 있습니다.

`Base`와 표준 라이브러리의 동작은 [SemVer](https://semver.org/)에 정의된 대로 문서화된 경우에만 안정적입니다. 즉, [Julia documentation](https://docs.julialang.org/)에 포함되어 있고 불안정으로 표시되지 않아야 합니다. 자세한 내용은 [API FAQ](@ref man-api)를 참조하십시오.

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

이것은 Julia의 예약어 목록입니다: `baremodule`, `begin`, `break`, `catch`, `const`, `continue`, `do`, `else`, `elseif`, `end`, `export`, `false`, `finally`, `for`, `function`, `global`, `if`, `import`, `let`, `local`, `macro`, `module`, `quote`, `return`, `struct`, `true`, `try`, `using`, `while`. 이러한 키워드는 변수 이름으로 사용할 수 없습니다.

다음의 두 단어 시퀀스는 예약어입니다: `abstract type`, `mutable struct`, `primitive type`. 그러나 다음과 같은 이름으로 변수를 생성할 수 있습니다: `abstract`, `mutable`, `primitive` 및 `type`.

마지막으로: `where`는 매개변수화된 메서드 및 타입 정의를 작성하기 위한 중위 연산자로 파싱됩니다; `in`과 `isa`는 중위 연산자로 파싱됩니다; `public`은 최상위 문을 시작할 때 키워드로 파싱됩니다; `outer`는 `for` 루프의 반복 사양에서 변수의 범위를 수정하는 데 사용될 때 키워드로 파싱됩니다; 그리고 `as`는 `import` 또는 `using`에 의해 범위로 가져온 식별자를 이름 바꾸는 데 키워드로 사용됩니다. 그러나 `where`, `in`, `isa`, `outer` 및 `as`라는 이름의 변수를 생성하는 것은 허용됩니다.

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

(또한 [documentation](@ref man-documentation) 장을 참조하십시오.)

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

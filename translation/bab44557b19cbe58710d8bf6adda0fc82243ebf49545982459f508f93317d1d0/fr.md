# Essentials

## Introduction

Julia Base contient une gamme de fonctions et de macros appropriées pour effectuer des calculs scientifiques et numériques, mais est également aussi vaste que celles de nombreux langages de programmation à usage général. Une fonctionnalité supplémentaire est disponible à partir d'une collection croissante de [available packages](https://julialang.org/packages/). Les fonctions sont regroupées par sujet ci-dessous.

Quelques notes générales :

  * Pour utiliser les fonctions du module, utilisez `import Module` pour importer le module, et `Module.fn(x)` pour utiliser les fonctions.
  * Alternativement, `using Module` importera toutes les fonctions exportées de `Module` dans l'espace de noms actuel.
  * Par convention, les noms de fonction se terminant par un point d'exclamation (`!`) modifient leurs arguments. Certaines fonctions ont à la fois des versions modifiant (par exemple, `sort!`) et non modifiant (`sort`).

Le comportement de `Base` et des bibliothèques standard est stable tel que défini dans [SemVer](https://semver.org/) uniquement s'il est documenté ; c'est-à-dire inclus dans le [Julia documentation](https://docs.julialang.org/) et non marqué comme instable. Voir [API FAQ](@ref man-api) pour plus d'informations.

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

Voici la liste des mots-clés réservés en Julia : `baremodule`, `begin`, `break`, `catch`, `const`, `continue`, `do`, `else`, `elseif`, `end`, `export`, `false`, `finally`, `for`, `function`, `global`, `if`, `import`, `let`, `local`, `macro`, `module`, `quote`, `return`, `struct`, `true`, `try`, `using`, `while`. Ces mots-clés ne peuvent pas être utilisés comme noms de variables.

Les deux séquences de mots suivantes sont réservées : `abstract type`, `mutable struct`, `primitive type`. Cependant, vous pouvez créer des variables avec les noms : `abstract`, `mutable`, `primitive` et `type`.

Enfin : `where` est analysé comme un opérateur infixe pour écrire des définitions de méthodes et de types paramétriques ; `in` et `isa` sont analysés comme des opérateurs infixes ; `public` est analysé comme un mot-clé lorsqu'il commence une déclaration de niveau supérieur ; `outer` est analysé comme un mot-clé lorsqu'il est utilisé pour modifier la portée d'une variable dans une spécification d'itération d'une boucle `for` ; et `as` est utilisé comme un mot-clé pour renommer un identifiant introduit dans la portée par `import` ou `using`. La création de variables nommées `where`, `in`, `isa`, `outer` et `as` est cependant autorisée.

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

(Voir aussi le chapitre [documentation](@ref man-documentation).)

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

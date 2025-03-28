# Stack Traces

Le module `StackTraces` fournit des traces de pile simples qui sont à la fois lisibles par l'homme et faciles à utiliser de manière programmatique.

## Viewing a stack trace

La fonction principale utilisée pour obtenir une trace de pile est [`stacktrace`](@ref) :

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

Appeler [`stacktrace()`](@ref) renvoie un vecteur de [`StackTraces.StackFrame`](@ref) s. Pour plus de commodité, l'alias [`StackTraces.StackTrace`](@ref) peut être utilisé à la place de `Vector{StackFrame}`. (Les exemples avec `[...]` indiquent que la sortie peut varier en fonction de la façon dont le code est exécuté.)

```julia-repl
julia> example() = stacktrace()
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[1]:1
 top-level scope
 eval at boot.jl:317 [inlined]
[...]

julia> @noinline child() = stacktrace()
child (generic function with 1 method)

julia> @noinline parent() = child()
parent (generic function with 1 method)

julia> grandparent() = parent()
grandparent (generic function with 1 method)

julia> grandparent()
9-element Array{Base.StackTraces.StackFrame,1}:
 child() at REPL[3]:1
 parent() at REPL[4]:1
 grandparent() at REPL[5]:1
[...]
```

Notez que lorsque vous appelez [`stacktrace()`](@ref), vous verrez généralement une trame avec `eval at boot.jl`. Lorsque vous appelez `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566` depuis le REPL, vous aurez également quelques trames supplémentaires dans la pile provenant de `REPL.jl`, qui ressemblent généralement à ceci :

```julia-repl
julia> example() = stacktrace()
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[1]:1
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

## Extracting useful information

Chaque [`StackTraces.StackFrame`](@ref) contient le nom de la fonction, le nom du fichier, le numéro de ligne, les informations sur la lambda, un indicateur indiquant si la trame a été intégrée, un indicateur indiquant si c'est une fonction C (par défaut, les fonctions C n'apparaissent pas dans la trace de la pile), et une représentation entière du pointeur retourné par [`backtrace`](@ref) :

```julia-repl
julia> frame = stacktrace()[3]
eval(::Module, ::Expr) at REPL.jl:5

julia> frame.func
:eval

julia> frame.file
Symbol("~/julia/usr/share/julia/stdlib/v0.7/REPL/src/REPL.jl")

julia> frame.line
5

julia> frame.linfo
MethodInstance for eval(::Module, ::Expr)

julia> frame.inlined
false

julia> frame.from_c
false

julia> frame.pointer
0x00007f92d6293171
```

Cela rend les informations de trace de pile disponibles de manière programmatique pour la journalisation, la gestion des erreurs, et plus encore.

## Error handling

Bien qu'un accès facile à des informations sur l'état actuel de la pile d'appels puisse être utile dans de nombreux cas, l'application la plus évidente se trouve dans la gestion des erreurs et le débogage.

```julia-repl
julia> @noinline bad_function() = undeclared_variable
bad_function (generic function with 1 method)

julia> @noinline example() = try
           bad_function()
       catch
           stacktrace()
       end
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[2]:4
 top-level scope
 eval at boot.jl:317 [inlined]
[...]
```

Vous pouvez remarquer que dans l'exemple ci-dessus, le premier cadre de pile pointe à la ligne 4, où [`stacktrace`](@ref) est appelé, plutôt qu'à la ligne 2, où *bad_function* est appelé, et le cadre de `bad_function` est complètement absent. Cela est compréhensible, étant donné que `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` est appelé dans le contexte du *catch*. Bien que dans cet exemple, il soit assez facile de trouver la source réelle de l'erreur, dans des cas complexes, le suivi de la source de l'erreur devient non trivial.

Cela peut être remédié en passant le résultat de [`catch_backtrace`](@ref) à [`stacktrace`](@ref). Au lieu de renvoyer des informations sur la pile d'appels pour le contexte actuel, `4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566` renvoie des informations sur la pile pour le contexte de la dernière exception :

```julia-repl
julia> @noinline bad_function() = undeclared_variable
bad_function (generic function with 1 method)

julia> @noinline example() = try
           bad_function()
       catch
           stacktrace(catch_backtrace())
       end
example (generic function with 1 method)

julia> example()
8-element Array{Base.StackTraces.StackFrame,1}:
 bad_function() at REPL[1]:1
 example() at REPL[2]:2
[...]
```

Remarquez que la trace de la pile indique maintenant le numéro de ligne approprié et le cadre manquant.

```julia-repl
julia> @noinline child() = error("Whoops!")
child (generic function with 1 method)

julia> @noinline parent() = child()
parent (generic function with 1 method)

julia> @noinline function grandparent()
           try
               parent()
           catch err
               println("ERROR: ", err.msg)
               stacktrace(catch_backtrace())
           end
       end
grandparent (generic function with 1 method)

julia> grandparent()
ERROR: Whoops!
10-element Array{Base.StackTraces.StackFrame,1}:
 error at error.jl:33 [inlined]
 child() at REPL[1]:1
 parent() at REPL[2]:1
 grandparent() at REPL[3]:3
[...]
```

## Exception stacks and [`current_exceptions`](@ref)

!!! compat "Julia 1.1"
    Les piles d'exceptions nécessitent au moins Julia 1.1.


Lors de la gestion d'une exception, d'autres exceptions peuvent être levées. Il peut être utile d'examiner toutes ces exceptions pour identifier la cause profonde d'un problème. Le runtime Julia prend en charge cela en empilant chaque exception sur une *pile d'exceptions* interne au fur et à mesure qu'elle se produit. Lorsque le code sort normalement d'un `catch`, toutes les exceptions qui ont été empilées dans le `try` associé sont considérées comme ayant été traitées avec succès et sont retirées de la pile.

La pile des exceptions actuelles peut être accédée en utilisant la fonction [`current_exceptions`](@ref). Par exemple,

```julia-repl
julia> try
           error("(A) The root cause")
       catch
           try
               error("(B) An exception while handling the exception")
           catch
               for (exc, bt) in current_exceptions()
                   showerror(stdout, exc, bt)
                   println(stdout)
               end
           end
       end
(A) The root cause
Stacktrace:
 [1] error(::String) at error.jl:33
 [2] top-level scope at REPL[7]:2
 [3] eval(::Module, ::Any) at boot.jl:319
 [4] eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 [5] macro expansion at REPL.jl:117 [inlined]
 [6] (::getfield(REPL, Symbol("##26#27")){REPL.REPLBackend})() at task.jl:259
(B) An exception while handling the exception
Stacktrace:
 [1] error(::String) at error.jl:33
 [2] top-level scope at REPL[7]:5
 [3] eval(::Module, ::Any) at boot.jl:319
 [4] eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 [5] macro expansion at REPL.jl:117 [inlined]
 [6] (::getfield(REPL, Symbol("##26#27")){REPL.REPLBackend})() at task.jl:259
```

Dans cet exemple, l'exception de cause racine (A) est en premier sur la pile, avec une autre exception (B) la suivant. Après avoir quitté normalement les deux blocs catch (c'est-à-dire sans lancer une autre exception), toutes les exceptions sont supprimées de la pile et ne sont plus accessibles.

La pile d'exceptions est stockée sur le `Task` où les exceptions se sont produites. Lorsqu'une tâche échoue avec des exceptions non interceptées, `current_exceptions(task)` peut être utilisé pour inspecter la pile d'exceptions de cette tâche.

## Comparison with [`backtrace`](@ref)

Un appel à [`backtrace`](@ref) renvoie un vecteur de `Union{Ptr{Nothing}, Base.InterpreterIP}`, qui peut ensuite être passé à [`stacktrace`](@ref) pour traduction :

```julia-repl
julia> trace = backtrace()
18-element Array{Union{Ptr{Nothing}, Base.InterpreterIP},1}:
 Ptr{Nothing} @0x00007fd8734c6209
 Ptr{Nothing} @0x00007fd87362b342
 Ptr{Nothing} @0x00007fd87362c136
 Ptr{Nothing} @0x00007fd87362c986
 Ptr{Nothing} @0x00007fd87362d089
 Base.InterpreterIP(CodeInfo(:(begin
      Core.SSAValue(0) = backtrace()
      trace = Core.SSAValue(0)
      return Core.SSAValue(0)
  end)), 0x0000000000000000)
 Ptr{Nothing} @0x00007fd87362e4cf
[...]

julia> stacktrace(trace)
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

Remarquez que le vecteur retourné par [`backtrace`](@ref) avait 18 éléments, tandis que le vecteur retourné par [`stacktrace`](@ref) n'en a que 6. Cela est dû au fait que, par défaut, `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` supprime toutes les fonctions C de bas niveau de la pile. Si vous souhaitez inclure des frames de pile provenant d'appels C, vous pouvez le faire comme ceci :

```julia-repl
julia> stacktrace(trace, true)
21-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167
 do_call at interpreter.c:324
 eval_value at interpreter.c:416
 eval_body at interpreter.c:559
 jl_interpret_toplevel_thunk_callback at interpreter.c:798
 top-level scope
 jl_interpret_toplevel_thunk at interpreter.c:807
 jl_toplevel_eval_flex at toplevel.c:856
 jl_toplevel_eval_in at builtins.c:624
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 jl_apply_generic at gf.c:2167
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 jl_apply_generic at gf.c:2167
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
 jl_fptr_trampoline at gf.c:1838
 jl_apply_generic at gf.c:2167
 jl_apply at julia.h:1540 [inlined]
 start_task at task.c:268
 ip:0xffffffffffffffff
```

Les pointeurs individuels retournés par [`backtrace`](@ref) peuvent être traduits en [`StackTraces.StackFrame`](@ref) s en les passant dans [`StackTraces.lookup`](@ref) :

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```

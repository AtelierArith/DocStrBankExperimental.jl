# Stack Traces

El módulo `StackTraces` proporciona trazas de pila simples que son tanto legibles para humanos como fáciles de usar programáticamente.

## Viewing a stack trace

La función principal utilizada para obtener un rastreo de pila es [`stacktrace`](@ref):

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

Llamar a [`stacktrace()`](@ref) devuelve un vector de [`StackTraces.StackFrame`](@ref) s. Para facilitar su uso, se puede utilizar el alias [`StackTraces.StackTrace`](@ref) en lugar de `Vector{StackFrame}`. (Los ejemplos con `[...]` indican que la salida puede variar dependiendo de cómo se ejecute el código.)

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

Tenga en cuenta que al llamar a [`stacktrace()`](@ref) normalmente verá un marco con `eval at boot.jl`. Al llamar a `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566` desde el REPL, también tendrá algunos marcos adicionales en la pila de `REPL.jl`, que generalmente se ven algo así:

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

Cada [`StackTraces.StackFrame`](@ref) contiene el nombre de la función, el nombre del archivo, el número de línea, la información de la lambda, una bandera que indica si el marco ha sido inyectado, una bandera que indica si es una función C (por defecto, las funciones C no aparecen en el rastro de la pila) y una representación entera del puntero devuelto por [`backtrace`](@ref):

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

Esto hace que la información de la traza de pila esté disponible programáticamente para el registro, el manejo de errores y más.

## Error handling

Si bien tener acceso fácil a la información sobre el estado actual de la pila de llamadas puede ser útil en muchos lugares, la aplicación más obvia es en el manejo de errores y la depuración.

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

Es posible que notes que en el ejemplo anterior el primer marco de pila apunta a la línea 4, donde se llama a [`stacktrace`](@ref), en lugar de la línea 2, donde se llama a *bad_function*, y el marco de `bad_function` falta por completo. Esto es comprensible, dado que `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` se llama desde el contexto del *catch*. Mientras que en este ejemplo es bastante fácil encontrar la fuente real del error, en casos complejos rastrear la fuente del error se vuelve no trivial.

Esto se puede remediar pasando el resultado de [`catch_backtrace`](@ref) a [`stacktrace`](@ref). En lugar de devolver información de la pila de llamadas para el contexto actual, `4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566` devuelve información de la pila para el contexto de la excepción más reciente:

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

Tenga en cuenta que la traza de la pila ahora indica el número de línea apropiado y el marco faltante.

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
    Las pilas de excepciones requieren al menos Julia 1.1.


Mientras se maneja una excepción, pueden lanzarse más excepciones. Puede ser útil inspeccionar todas estas excepciones para identificar la causa raíz de un problema. El tiempo de ejecución de Julia admite esto al apilar cada excepción en una *pila de excepciones* interna a medida que ocurre. Cuando el código sale de un `catch` normalmente, cualquier excepción que se haya apilado en la `try` asociada se considera manejada con éxito y se elimina de la pila.

La pila de excepciones actuales se puede acceder utilizando la función [`current_exceptions`](@ref). Por ejemplo,

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

En este ejemplo, la excepción raíz (A) está primero en la pila, con una excepción adicional (B) siguiéndola. Después de salir normalmente de ambos bloques catch (es decir, sin lanzar una excepción adicional), todas las excepciones se eliminan de la pila y ya no son accesibles.

La pila de excepciones se almacena en la `Tarea` donde ocurrieron las excepciones. Cuando una tarea falla con excepciones no capturadas, se puede usar `current_exceptions(tarea)` para inspeccionar la pila de excepciones de esa tarea.

## Comparison with [`backtrace`](@ref)

Una llamada a [`backtrace`](@ref) devuelve un vector de `Union{Ptr{Nothing}, Base.InterpreterIP}`, que luego puede ser pasado a [`stacktrace`](@ref) para traducción:

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

Tenga en cuenta que el vector devuelto por [`backtrace`](@ref) tenía 18 elementos, mientras que el vector devuelto por [`stacktrace`](@ref) solo tiene 6. Esto se debe a que, por defecto, `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` elimina cualquier función de C de nivel inferior de la pila. Si desea incluir marcos de pila de llamadas de C, puede hacerlo así:

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

Los punteros individuales devueltos por [`backtrace`](@ref) se pueden traducir en [`StackTraces.StackFrame`](@ref) al pasarlos a [`StackTraces.lookup`](@ref):

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```

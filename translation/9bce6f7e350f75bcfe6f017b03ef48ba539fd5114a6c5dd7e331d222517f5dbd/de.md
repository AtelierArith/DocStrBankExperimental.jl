# Stack Traces

Das `StackTraces`-Modul bietet einfache Stack-Traces, die sowohl für Menschen lesbar als auch programmgesteuert leicht zu verwenden sind.

## Viewing a stack trace

Die primäre Funktion, die verwendet wird, um einen Stack-Trace zu erhalten, ist [`stacktrace`](@ref):

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

Der Aufruf von [`stacktrace()`](@ref) gibt einen Vektor von [`StackTraces.StackFrame`](@ref) zurück. Zur Vereinfachung kann das Alias [`StackTraces.StackTrace`](@ref) anstelle von `Vector{StackFrame}` verwendet werden. (Beispiele mit `[...]` deuten darauf hin, dass die Ausgabe je nach Ausführung des Codes variieren kann.)

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

Beachten Sie, dass Sie beim Aufrufen von [`stacktrace()`](@ref) typischerweise einen Frame mit `eval at boot.jl` sehen. Wenn Sie `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566` aus dem REPL aufrufen, haben Sie auch einige zusätzliche Frames im Stack von `REPL.jl`, die normalerweise so aussehen:

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

Jede [`StackTraces.StackFrame`](@ref) enthält den Funktionsnamen, den Dateinamen, die Zeilennummer, die Lambda-Informationen, ein Flag, das angibt, ob der Frame inline ist, ein Flag, das angibt, ob es sich um eine C-Funktion handelt (standardmäßig erscheinen C-Funktionen nicht im Stack-Trace), und eine ganzzahlige Darstellung des von [`backtrace`](@ref) zurückgegebenen Zeigers:

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

Dies macht Stack-Trace-Informationen programmgesteuert für Protokollierung, Fehlerbehandlung und mehr verfügbar.

## Error handling

Während der einfache Zugang zu Informationen über den aktuellen Zustand des Callstacks in vielen Bereichen hilfreich sein kann, ist die offensichtlichste Anwendung die Fehlerbehandlung und das Debugging.

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

Sie werden möglicherweise feststellen, dass im obigen Beispiel der erste Stack-Frame auf Zeile 4 zeigt, wo [`stacktrace`](@ref) aufgerufen wird, anstatt auf Zeile 2, wo *bad_function* aufgerufen wird, und der Frame von `bad_function` vollständig fehlt. Dies ist verständlich, da `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` im Kontext des *catch* aufgerufen wird. Während es in diesem Beispiel recht einfach ist, die tatsächliche Quelle des Fehlers zu finden, wird es in komplexen Fällen nicht trivial, die Quelle des Fehlers zu verfolgen.

Dies kann behoben werden, indem das Ergebnis von [`catch_backtrace`](@ref) an [`stacktrace`](@ref) übergeben wird. Anstatt Informationen zum Aufrufstapel für den aktuellen Kontext zurückzugeben, gibt `4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566` Informationen zum Stapel für den Kontext der letzten Ausnahme zurück:

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

Beachten Sie, dass der Stack-Trace jetzt die entsprechende Zeilennummer und den fehlenden Frame anzeigt.

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
    Ausnahme-Stacks erfordern mindestens Julia 1.1.


Während der Behandlung einer Ausnahme können weitere Ausnahmen ausgelöst werden. Es kann nützlich sein, all diese Ausnahmen zu inspizieren, um die Grundursache eines Problems zu identifizieren. Die Julia-Laufzeit unterstützt dies, indem jede Ausnahme, sobald sie auftritt, auf einen internen *Ausnahme-Stack* geschoben wird. Wenn der Code normal aus einem `catch` austritt, werden alle Ausnahmen, die im zugehörigen `try` auf den Stack geschoben wurden, als erfolgreich behandelt betrachtet und vom Stack entfernt.

Der Stapel der aktuellen Ausnahmen kann mit der Funktion [`current_exceptions`](@ref) zugegriffen werden. Zum Beispiel,

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

In diesem Beispiel steht die Grundursache-Ausnahme (A) zuerst im Stack, gefolgt von einer weiteren Ausnahme (B). Nachdem beide Catch-Blöcke normal verlassen wurden (d.h. ohne eine weitere Ausnahme auszulösen), werden alle Ausnahmen aus dem Stack entfernt und sind nicht mehr zugänglich.

Der Ausnahme-Stack wird auf dem `Task` gespeichert, wo die Ausnahmen aufgetreten sind. Wenn ein Task mit nicht abgefangenen Ausnahmen fehlschlägt, kann `current_exceptions(task)` verwendet werden, um den Ausnahme-Stack für diesen Task zu inspizieren.

## Comparison with [`backtrace`](@ref)

Ein Aufruf von [`backtrace`](@ref) gibt einen Vektor von `Union{Ptr{Nothing}, Base.InterpreterIP}` zurück, der dann in [`stacktrace`](@ref) zur Übersetzung übergeben werden kann:

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

Beachten Sie, dass der Vektor, der von [`backtrace`](@ref) zurückgegeben wurde, 18 Elemente hatte, während der Vektor, der von [`stacktrace`](@ref) zurückgegeben wurde, nur 6 hat. Dies liegt daran, dass `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` standardmäßig alle niedrigeren C-Funktionen vom Stack entfernt. Wenn Sie Stack-Frames von C-Aufrufen einbeziehen möchten, können Sie es so machen:

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

Individuelle Zeiger, die von [`backtrace`](@ref) zurückgegeben werden, können in [`StackTraces.StackFrame`](@ref) übersetzt werden, indem sie in [`StackTraces.lookup`](@ref) übergeben werden:

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```

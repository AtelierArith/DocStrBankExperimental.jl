# Stack Traces

`StackTraces` 모듈은 사람에게 읽기 쉽고 프로그래밍적으로 사용하기 쉬운 간단한 스택 트레이스를 제공합니다.

## Viewing a stack trace

주 스택 트레이스를 얻는 데 사용되는 기본 함수는 [`stacktrace`](@ref)입니다:

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

[`stacktrace()`](@ref)를 호출하면 [`StackTraces.StackFrame`](@ref)의 벡터가 반환됩니다. 사용의 편의를 위해 별칭 [`StackTraces.StackTrace`](@ref)를 `Vector{StackFrame}` 대신 사용할 수 있습니다. (예제에서 `[...]`는 코드 실행 방식에 따라 출력이 달라질 수 있음을 나타냅니다.)

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

[`stacktrace()`](@ref)를 호출할 때 일반적으로 `eval at boot.jl`이 있는 프레임을 볼 수 있습니다. REPL에서 `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566`를 호출하면 `REPL.jl`에서 몇 개의 추가 프레임이 스택에 나타나며, 보통 다음과 같은 형태로 보입니다:

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

각 [`StackTraces.StackFrame`](@ref)는 함수 이름, 파일 이름, 줄 번호, 람다 정보, 프레임이 인라인되었는지 여부를 나타내는 플래그, C 함수인지 여부를 나타내는 플래그(기본적으로 C 함수는 스택 추적에 나타나지 않음), 그리고 [`backtrace`](@ref)에 의해 반환된 포인터의 정수 표현을 포함합니다:

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

이것은 로깅, 오류 처리 등과 같은 목적으로 스택 추적 정보를 프로그래밍적으로 사용할 수 있게 합니다.

## Error handling

현재 호출 스택의 상태에 대한 정보에 쉽게 접근할 수 있는 것은 많은 곳에서 유용하지만, 가장 명백한 응용 프로그램은 오류 처리 및 디버깅입니다.

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

위의 예에서 첫 번째 스택 프레임이 `bad_function`이 호출된 2행이 아닌 [`stacktrace`](@ref)가 호출된 4행을 가리키고 있다는 점을 주목할 수 있습니다. `bad_function`의 프레임은 완전히 누락되어 있습니다. 이는 `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566`가 *catch*의 맥락에서 호출되기 때문에 이해할 수 있습니다. 이 예에서는 오류의 실제 출처를 찾는 것이 비교적 쉽지만, 복잡한 경우에는 오류의 출처를 추적하는 것이 간단하지 않습니다.

이 문제는 [`catch_backtrace`](@ref)의 결과를 [`stacktrace`](@ref)에 전달함으로써 해결할 수 있습니다. 현재 컨텍스트에 대한 호출 스택 정보를 반환하는 대신, `4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566`는 가장 최근의 예외 컨텍스트에 대한 스택 정보를 반환합니다:

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

스택 추적이 이제 적절한 줄 번호와 누락된 프레임을 나타낸다는 점에 유의하세요.

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
    예외 스택은 최소한 Julia 1.1이 필요합니다.


예외를 처리하는 동안 추가 예외가 발생할 수 있습니다. 이러한 모든 예외를 검사하여 문제의 근본 원인을 파악하는 것이 유용할 수 있습니다. 줄리아 런타임은 발생할 때마다 각 예외를 내부 *예외 스택*에 푸시하여 이를 지원합니다. 코드가 `catch`를 정상적으로 종료하면, 관련된 `try`에서 스택에 푸시된 모든 예외는 성공적으로 처리된 것으로 간주되어 스택에서 제거됩니다.

현재 예외 스택은 [`current_exceptions`](@ref) 함수를 사용하여 접근할 수 있습니다. 예를 들어,

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

이 예제에서 루트 원인 예외(A)는 스택의 맨 위에 있으며, 그 뒤에 추가 예외(B)가 있습니다. 두 개의 catch 블록을 정상적으로 종료한 후(즉, 추가 예외를 발생시키지 않고) 모든 예외는 스택에서 제거되며 더 이상 접근할 수 없습니다.

예외 스택은 예외가 발생한 `Task`에 저장됩니다. 작업이 처리되지 않은 예외로 실패할 때, `current_exceptions(task)`를 사용하여 해당 작업의 예외 스택을 검사할 수 있습니다.

## Comparison with [`backtrace`](@ref)

[`backtrace`](@ref)에 대한 호출은 `Union{Ptr{Nothing}, Base.InterpreterIP}`의 벡터를 반환하며, 이는 이후 [`stacktrace`](@ref)에 전달되어 번역될 수 있습니다:

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

[`backtrace`](@ref)가 18개의 요소를 반환한 반면, [`stacktrace`](@ref)는 6개만 반환했다는 점에 유의하세요. 이는 기본적으로 `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566`가 스택에서 모든 하위 수준 C 함수를 제거하기 때문입니다. C 호출에서 스택 프레임을 포함하려면 다음과 같이 할 수 있습니다:

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

[`backtrace`](@ref)에서 반환된 개별 포인터는 [`StackTraces.StackFrame`](@ref)로 변환될 수 있으며, 이를 [`StackTraces.lookup`](@ref)에 전달하여 처리할 수 있습니다.

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```

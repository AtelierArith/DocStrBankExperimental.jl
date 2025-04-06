# Stack Traces

`StackTraces` modülü, hem insan tarafından okunabilir hem de programatik olarak kullanımı kolay basit yığın izleri sağlar.

## Viewing a stack trace

Ana işlev, bir yığın izini elde etmek için kullanılan [`stacktrace`](@ref):`

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

[`stacktrace()`](@ref) çağrısı, [`StackTraces.StackFrame`](@ref) vektörünü döndürür. Kullanım kolaylığı için, `Vector{StackFrame}` yerine [`StackTraces.StackTrace`](@ref) takma adı kullanılabilir. (Örneklerdeki `[...]` çıktının kodun nasıl çalıştırıldığına bağlı olarak değişebileceğini gösterir.)

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

Not edin ki [`stacktrace()`](@ref) çağrıldığında genellikle `eval at boot.jl` ile bir çerçeve göreceksiniz. `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566`'yı REPL'den çağırdığınızda, genellikle `REPL.jl`'den birkaç ekstra çerçeve de yığın içinde olacaktır ve bunlar genellikle şöyle görünür:

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

Her [`StackTraces.StackFrame`](@ref) işlev adı, dosya adı, satır numarası, lambda bilgisi, çerçevenin iç içe geçmiş olup olmadığını belirten bir bayrak, bir C işlevi olup olmadığını belirten bir bayrak (varsayılan olarak C işlevleri yığın izinde görünmez) ve [`backtrace`](@ref) tarafından döndürülen işaretçinin tam sayı temsili içerir:

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

Bu, yığın izleme bilgilerini programatik olarak günlüğe kaydetme, hata işleme ve daha fazlası için kullanılabilir hale getirir.

## Error handling

Hata yönetimi ve hata ayıklama gibi birçok yerde çağrı yığınının mevcut durumu hakkında kolay erişim sağlamak faydalı olabilir, en belirgin uygulama budur.

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

Yukarıdaki örnekte, ilk yığın çerçevesinin `bad_function`'ın çağrıldığı 2. satır yerine [`stacktrace`](@ref)'nın çağrıldığı 4. satıra işaret ettiğini fark edebilirsiniz ve `bad_function`'ın çerçevesi tamamen kaybolmuştur. Bu, `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566`'nın *catch* bağlamından çağrıldığını göz önünde bulundurursak anlaşılabilir. Bu örnekte hatanın gerçek kaynağını bulmak oldukça kolayken, karmaşık durumlarda hatanın kaynağını izlemek zor hale gelir.

Bu, [`catch_backtrace`](@ref) sonucunu [`stacktrace`](@ref)'ya geçirerek düzeltilebilir. Mevcut bağlam için çağrı yığını bilgisi döndürmek yerine, `4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566`, en son istisnanın bağlamı için yığın bilgisi döndürür:

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

Yığın izinin artık uygun satır numarasını ve eksik çerçeveyi gösterdiğini unutmayın.

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
    Hata yığınları en az Julia 1.1 gerektirir.


Bir istisna işlenirken daha fazla istisna atılabilir. Bu istisnaların tümünü incelemek, bir sorunun kök nedenini belirlemek için faydalı olabilir. Julia çalışma zamanı, her istisna meydana geldiğinde bunları dahili bir *istisna yığınına* iterek bunu destekler. Kod bir `catch` ifadesinden normal olarak çıktığında, ilgili `try` içinde yığına itilen herhangi bir istisna başarılı bir şekilde işlenmiş olarak kabul edilir ve yığından kaldırılır.

Mevcut istisna yığını [`current_exceptions`](@ref) fonksiyonu kullanılarak erişilebilir. Örneğin,

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

Bu örnekte, kök neden istisnası (A) yığın üzerinde ilk sıradadır ve onu takip eden başka bir istisna (B) vardır. Her iki catch bloğundan normal bir şekilde çıkıldıktan sonra (yani, başka bir istisna atmadan) tüm istisnalar yığından kaldırılır ve artık erişilemez hale gelir.

İstisna yığını, istisnaların meydana geldiği `Task` üzerinde saklanır. Bir görev, yakalanmamış istisnalarla başarısız olduğunda, o görev için istisna yığınını incelemek üzere `current_exceptions(task)` kullanılabilir.

## Comparison with [`backtrace`](@ref)

[`backtrace`](@ref) çağrısı `Union{Ptr{Nothing}, Base.InterpreterIP}` vektörü döndürür, bu daha sonra [`stacktrace`](@ref) için çeviri yapmak üzere geçirilebilir:

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

Dikkat edin ki, [`backtrace`](@ref) tarafından döndürülen vektör 18 eleman içerirken, [`stacktrace`](@ref) tarafından döndürülen vektör yalnızca 6 eleman içermektedir. Bunun nedeni, varsayılan olarak `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566`'nın yığın üzerindeki herhangi bir alt seviye C fonksiyonunu kaldırmasıdır. C çağrılarından yığın çerçevelerini dahil etmek istiyorsanız, bunu şu şekilde yapabilirsiniz:

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

Bireysel işaretçiler [`backtrace`](@ref) tarafından döndürülen, [`StackTraces.StackFrame`](@ref) s'ye dönüştürülebilir. Bunu [`StackTraces.lookup`](@ref) içine geçirerek yapabilirsiniz:

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```

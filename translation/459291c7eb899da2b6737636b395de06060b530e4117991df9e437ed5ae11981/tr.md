# Initialization of the Julia runtime

Julia runtime, `julia -e 'println("Hello World!")'`, executes the command as follows:

## `main()`

Yürütme [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) ile başlar, bu da `jl_load_repl()` çağrısını [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c) içinde yapar, birkaç kütüphaneyi yükler ve nihayetinde [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) çağrısını yapar.

`jl_repl_entrypoint()` [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c) C kütüphanesi yerel ayarını ayarlamak ve "ios" kütüphanesini başlatmak için çağrılır (bkz. [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) ve [Legacy `ios.c` library](@ref Legacy-ios.c-library)).

Son [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c) komut satırı seçeneklerini işlemek için çağrılır. `jl_parse_opts()` yalnızca kod üretimi veya erken başlatmayı etkileyen seçeneklerle ilgilenir. Diğer seçenekler daha sonra [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) tarafından işlenir.

`jl_parse_opts()` komut satırı seçeneklerini [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h) içinde saklar.

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) `main()` tarafından çağrılır ve [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) çağrılır.

`_julia_init()` önce `libsupport_init()` çağrısı yapar (ikinci kez hiçbir şey yapmaz).

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) sinyal işleyici maskesini sıfırlamak için çağrılır.

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) temel sistem görüntüsü için yapılandırılmış yolları arar. [Building the Julia system image](@ref Building-the-Julia-system-image) için.

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) zayıf referanslar, korunmuş değerler ve sonlandırma için tahsis havuzları ve listeleri kurar.

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) bir tarayıcı/parsing içeren önceden derlenmiş bir femtolisp görüntüsünü yükler ve başlatır.

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) `jl_datatype_t` türü tanım nesneleri oluşturur [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h). örneğin.

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c) `jl_datatype_t* jl_task_type` nesnesini oluşturur; global `jl_root_task` yapısını başlatır; ve `jl_current_task`'ı kök göreve ayarlar.

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) [LLVM library](https://llvm.org) olarak başlatır.

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 8-bit serileştirme etiketlerini yerleşik `jl_value_t` değerleri için başlatır.

Eğer bir sysimg dosyası yoksa (`!jl_options.image_file`), o zaman `Core` ve `Main` modülleri oluşturulur ve `boot.jl` değerlendirilir:

`jl_core_module = jl_new_module(jl_symbol("Core"))` Julia `Core` modülünü oluşturur.

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) yeni bir Julia modülü `Intrinsics` oluşturur ve `jl_intrinsic_type` sabitlerini içerir. Bu sabitler, her bir [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) için bir tamsayı kodu tanımlar. [`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) bu sembolleri kod üretimi sırasında LLVM talimatlarına çevirir.

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) C fonksiyonlarını Julia fonksiyon sembollerine bağlar. Örneğin, `Core.:(===)()` sembolü, `add_builtin_func("===", jl_f_is)` çağrısı ile C fonksiyon işaretçisi `jl_f_is()`'e bağlanır.

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) global "Main" modülünü oluşturur ve `jl_current_task->current_module = jl_main_module` olarak ayarlar.

Not: `_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`. `jl_root_task` bu noktada `jl_current_task`'ın bir takma adıdır, bu nedenle yukarıda `jl_new_main_module()` tarafından ayarlanan `current_module` üzerine yazılır.

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c) çağrılır [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) bu da sürekli olarak çağrılır [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) çalıştırmak için [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl). <!– TODO – eval içine in? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) Julia globals'ı `boot.jl` dosyasında tanımlanan global C işaretçilerini başlatır.

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) global kutulu tam sayılar için 1024'e kadar değerler için önceden tahsis eder. Bu, daha sonra kutulu int'lerin tahsisatını hızlandırır. örn.:

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_core_module->bindings.table` üzerinde `jl_datatype_t` değerlerini arar ve tür adının modül ön ekini `jl_core_module` olarak ayarlar.

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) "Ana Modül" içinde "Base" kullanıyor.

Not: `_julia_init()` artık yukarıda `jl_core_module` olarak ayarlandığı gibi değil, `jl_root_task->current_module = jl_main_module` olarak geri dönmektedir.

Platform spesifik sinyal işleyicileri `SIGSEGV` (OSX, Linux) ve `SIGFPE` (Windows) için başlatılır.

Diğer sinyaller (`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` ve `SIGPIPE`), [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) ile bağlanmıştır ve bir geri izleme (backtrace) yazdırır.

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) her [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c) her her deserialized modül için `__init__()` fonksiyonunu çalıştırmak üzere çağrılır.

Sonunda [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) `SIGINT` ile bağlandı ve `jl_throw(jl_interrupt_exception)` çağrısı yapıyor.

`_julia_init()` ardından [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) ve `main()` `repl_entrypoint(argc, (char**)argv)` çağrısını yapar.

!!! sidebar "sysimg"
    Eğer bir sysimg dosyası varsa, bu `Core` ve `Main` modüllerinin (ve `boot.jl` tarafından oluşturulan diğer her şeyin) önceden hazırlanmış bir görüntüsünü içerir. [Building the Julia system image](@ref Building-the-Julia-system-image)'e bakın.

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) mevcut sysimg'i mevcut Julia çalışma zamanı ortamına serileştirir ve `jl_init_box_caches()`'ten sonra başlatma devam eder...

    Not: [`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) [Legacy `ios.c` library](@ref Legacy-ios.c-library).


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) `argv[]`'in içeriklerini [`Base.ARGS`](@ref)'ya yükler.

Eğer bir `.jl` "program" dosyası komut satırında sağlandıysa, o zaman [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) çağırır, bu da [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) çağırır, bu da sürekli olarak [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) çağırarak programı çalıştırır.

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) [`Core.eval(Main, ex)`](@ref Core.eval)

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval) çağrıları [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c), bu da [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) çağrısını yapar. `jl_toplevel_eval_flex`, verilen bir kod thunk'unu derleyip derlemeyeceğine veya yorumlayıcı tarafından çalıştırıp çalıştırmayacağına karar vermek için basit bir sezgi uygular. `println("Hello World!")` verildiğinde, genellikle kodu yorumlayıcı tarafından çalıştırmaya karar verir; bu durumda [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) çağrısını yapar, bu da [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) çağrısını yapar.

Aşağıdaki yığın dökümü, yorumlayıcının [`Base.println()`](@ref) ve [`Base.print()`](@ref) çeşitli yöntemleri aracılığıyla nasıl ilerlediğini göstermektedir ve [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl) ile sonuçlanır ve `ccall(jl_uv_write())` işlemini gerçekleştirir.

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c) `uv_write()`'i `JL_STDOUT`'a "Hello World!" yazmak için çağrılır. [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio).

```
Hello World!
```

| Stack frame                   | Source code     | Notes                                                |
|:----------------------------- |:--------------- |:---------------------------------------------------- |
| `jl_uv_write()`               | `jl_uv.c`       | called though [`ccall`](@ref)                        |
| `julia_write_282942`          | `stream.jl`     | function `write!(s::IO, a::Array{T}) where T`        |
| `julia_print_284639`          | `ascii.jl`      | `print(io::IO, s::String) = (write(io, s); nothing)` |
| `jlcall_print_284639`         |                 |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String)`                       |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String, Char, Char...)`        |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_f_apply()`                | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(Base.TTY, String, String...)`          |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(String,)`                              |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `do_call()`                   | `interpreter.c` |                                                      |
| `eval_body()`                 | `interpreter.c` |                                                      |
| `jl_interpret_toplevel_thunk` | `interpreter.c` |                                                      |
| `jl_toplevel_eval_flex`       | `toplevel.c`    |                                                      |
| `jl_toplevel_eval_in`         | `toplevel.c`    |                                                      |
| `Core.eval`                   | `boot.jl`       |                                                      |

Örneğimizde sadece bir fonksiyon çağrısı olduğu için, "Hello World!" yazdırma işini yaptıktan sonra, yığın hızla `main()`'e geri sarılır.

## `jl_atexit_hook()`

`main()` [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) çağrısını yapar. Bu `Base._atexit` çağrısını yapar, ardından [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) çağrısını yapar ve libuv handle'larını temizler.

## `julia_save()`

Sonunda, `main()` [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) çağrısını yapar; bu, komut satırında istendiğinde çalışma durumunu yeni bir sistem görüntüsüne kaydeder. [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) ve [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)'e bakın.

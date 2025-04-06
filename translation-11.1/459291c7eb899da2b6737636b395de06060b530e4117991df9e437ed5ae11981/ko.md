# Initialization of the Julia runtime

`julia -e 'println("Hello World!")'` 명령어는 Julia 런타임이 다음과 같은 방식으로 실행됩니다:

## `main()`

실행은 [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c)에서 시작되며, 이는 [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c)에서 `jl_load_repl()`을 호출합니다. 이는 몇 가지 라이브러리를 로드하고, 결국 [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c)을 호출합니다.

`jl_repl_entrypoint()`는 [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c)를 호출하여 C 라이브러리 로케일을 설정하고 "ios" 라이브러리를 초기화합니다(참조: [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) 및 [Legacy `ios.c` library](@ref Legacy-ios.c-library)).

다음 [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c)는 명령줄 옵션을 처리하기 위해 호출됩니다. `jl_parse_opts()`는 코드 생성 또는 초기화에 영향을 미치는 옵션만 처리합니다. 다른 옵션은 나중에 [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl)에 의해 처리됩니다.

`jl_parse_opts()`는 명령줄 옵션을 [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h)에 저장합니다.

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c)는 `main()`에 의해 호출되며 [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c)를 호출합니다.

`_julia_init()`는 `libsupport_init()`를 다시 호출하는 것으로 시작합니다(두 번째 호출에서는 아무 작업도 수행하지 않습니다).

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c)는 신호 처리기 마스크를 제로로 설정하는 데 사용됩니다.

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)는 기본 시스템 이미지를 위한 구성된 경로를 검색합니다. [Building the Julia system image](@ref Building-the-Julia-system-image)를 참조하십시오.

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c)는 약한 참조, 보존된 값 및 최종화를 위한 할당 풀과 목록을 설정합니다.

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)는 스캐너/파서를 포함하는 미리 컴파일된 펨토리프 이미지 로드 및 초기화를 수행합니다.

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c)는 `jl_datatype_t` 유형 설명 객체를 생성합니다. [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) 예:

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c)는 `jl_datatype_t* jl_task_type` 객체를 생성하고, 전역 `jl_root_task` 구조체를 초기화하며, `jl_current_task`를 루트 작업으로 설정합니다.

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp)는 [LLVM library](https://llvm.org)를 초기화합니다.

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)는 내장된 `jl_value_t` 값에 대한 8비트 직렬화 태그를 초기화합니다.

`sysimg` 파일이 없으면 (`!jl_options.image_file`) `Core` 및 `Main` 모듈이 생성되고 `boot.jl`이 평가됩니다:

`jl_core_module = jl_new_module(jl_symbol("Core"))`는 Julia `Core` 모듈을 생성합니다.

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)는 상수 `jl_intrinsic_type` 기호를 포함하는 새로운 Julia 모듈 `Intrinsics`를 생성합니다. 이들은 각 [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)에 대한 정수 코드를 정의합니다. [`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)는 코드 생성 중에 이러한 기호를 LLVM 명령어로 변환합니다.

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c)는 C 함수를 Julia 함수 기호에 연결합니다. 예를 들어, 기호 `Core.:(===)()`는 `add_builtin_func("===", jl_f_is)`를 호출하여 C 함수 포인터 `jl_f_is()`에 바인딩됩니다.

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)는 전역 "Main" 모듈을 생성하고 `jl_current_task->current_module = jl_main_module`를 설정합니다.

노트: `_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`. 이 시점에서 `jl_root_task`는 `jl_current_task`의 별칭이므로, 위에서 `jl_new_main_module()`에 의해 설정된 `current_module`이 덮어씌워집니다.

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c)는 [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)를 호출하며, 이는 반복적으로 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)를 호출하여 [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl)를 실행합니다. <!– TODO – eval을 자세히 살펴보세요? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)는 `boot.jl`에 정의된 Julia 전역 변수에 대한 전역 C 포인터를 초기화합니다.

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) 전역 박스 정수 값 객체를 1024까지의 값에 대해 미리 할당합니다. 이는 나중에 박스 정수의 할당 속도를 높입니다. 예:

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c)는 `jl_core_module->bindings.table`에서 `jl_datatype_t` 값을 찾고, 타입 이름의 모듈 접두사를 `jl_core_module`로 설정합니다.

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)는 "Main" 모듈에서 "using Base"를 사용합니다.

참고: `_julia_init()`는 이제 위에서 `jl_core_module`로 설정되기 전처럼 `jl_root_task->current_module = jl_main_module`로 되돌아갑니다.

플랫폼별 신호 처리기가 `SIGSEGV` (OSX, Linux) 및 `SIGFPE` (Windows)에 대해 초기화됩니다.

다른 신호들 (`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` 및 `SIGPIPE`)은 [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c)에 연결되어 있으며, 이는 백트레이스를 출력합니다.

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)는 각 역직렬화된 모듈에 대해 `__init__()` 함수를 실행하기 위해 [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c)를 호출합니다.

마침내 [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c)가 `SIGINT`에 연결되어 `jl_throw(jl_interrupt_exception)`을 호출합니다.

`_julia_init()`는 [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c)를 반환하고, `main()`은 `repl_entrypoint(argc, (char**)argv)`를 호출합니다.

!!! sidebar "sysimg"
    sysimg 파일이 있는 경우, 이는 `Core` 및 `Main` 모듈(및 `boot.jl`에 의해 생성된 기타 모든 것)의 미리 준비된 이미지를 포함합니다. [Building the Julia system image](@ref Building-the-Julia-system-image)를 참조하세요.

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)는 저장된 sysimg를 현재 Julia 런타임 환경으로 역직렬화하며, 초기화는 아래의 `jl_init_box_caches()` 이후에 계속됩니다...

    노트: [`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)는 [Legacy `ios.c` library](@ref Legacy-ios.c-library)를 사용합니다.


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c)는 `argv[]`의 내용을 [`Base.ARGS`](@ref)에 로드합니다.

만약 `.jl` "프로그램" 파일이 명령줄에 제공되었다면, [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c)는 [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)를 호출하고, 이는 [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)를 호출하며, 이는 반복적으로 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)를 호출하여 프로그램을 실행합니다.

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl)는 [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl)를 호출하고, 이는 [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)를 호출하여 표현식 객체를 생성하고, [`Core.eval(Main, ex)`](@ref Core.eval)를 호출하여 `Main`의 모듈 컨텍스트에서 파싱된 표현식 `ex`를 실행합니다.

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval)는 [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)를 호출하고, 이는 [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)를 호출합니다. `jl_toplevel_eval_flex`는 주어진 코드 덩어리를 컴파일할지 인터프리터로 실행할지를 결정하기 위한 간단한 휴리스틱을 구현합니다. `println("Hello World!")`가 주어지면, 일반적으로 코드를 인터프리터로 실행하기로 결정하며, 이 경우 [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c)를 호출하고, 이는 다시 [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c)를 호출합니다.

스택 덤프 아래는 인터프리터가 [`Base.println()`](@ref) 및 [`Base.print()`](@ref)의 다양한 메서드를 통해 어떻게 진행되는지를 보여줍니다. 최종적으로 [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl)에 도달하여 `ccall(jl_uv_write())`를 실행합니다.

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c)는 `JL_STDOUT`에 "Hello World!"를 쓰기 위해 `uv_write()`를 호출합니다. [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio)를 참조하십시오.

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

예제에는 단 하나의 함수 호출만 있으므로 "Hello World!"를 출력하는 작업을 완료한 후 스택은 이제 빠르게 `main()`으로 되돌아갑니다.

## `jl_atexit_hook()`

`main()`은 [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)를 호출합니다. 이는 `Base._atexit`를 호출한 다음 [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c)를 호출하고 libuv 핸들을 정리합니다.

## `julia_save()`

마지막으로, `main()`은 [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)를 호출합니다. 이는 명령줄에서 요청할 경우 런타임 상태를 새로운 시스템 이미지로 저장합니다. [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) 및 [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)를 참조하십시오.

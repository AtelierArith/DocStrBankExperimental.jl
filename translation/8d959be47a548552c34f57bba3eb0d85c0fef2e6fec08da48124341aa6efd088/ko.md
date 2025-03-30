# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

`gdb` 내에서 모든 `jl_value_t*` 객체 `obj`는 다음을 사용하여 표시할 수 있습니다.

```
(gdb) call jl_(obj)
```

객체는 `julia` 세션에서 표시되며, gdb 세션에서는 표시되지 않습니다. 이는 Julia의 C 코드에 의해 조작되는 객체의 유형과 값을 발견하는 유용한 방법입니다.

유사하게, Julia의 내부(예: `compiler.jl`)를 디버깅하는 경우 `obj`를 다음과 같이 출력할 수 있습니다.

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

이것은 줄리아의 출력 스트림이 초기화되는 순서로 인해 발생하는 문제를 우회하는 좋은 방법입니다.

줄리아의 플립스 인터프리터는 `value_t` 객체를 사용합니다. 이러한 객체는 `call fl_print(fl_ctx, ios_stdout, obj)`로 표시할 수 있습니다.

## Useful Julia variables for Inspecting

많은 변수의 주소, 예를 들어 싱글톤과 같은,는 많은 실패에 대해 출력하는 데 유용할 수 있지만, 훨씬 더 유용한 추가 변수들이 있습니다(전체 목록은 `julia.h`를 참조하십시오).

  * (when in `jl_apply_generic`) `mfunc` 및 `jl_uncompress_ast(mfunc->def, mfunc->code)` :: 호출 스택에 대한 정보를 파악하기 위해
  * `jl_lineno` 및 `jl_filename` :: 테스트에서 디버깅을 시작할 줄을 파악하거나 파일이 얼마나 파싱되었는지 확인하는 데 사용됩니다.
  * `$1` :: 실제로는 변수는 아니지만, 마지막 gdb 명령(예: `print`)의 결과를 참조하는 데 유용한 약어입니다.
  * `jl_options` :: 때때로 유용하며, 성공적으로 파싱된 모든 명령줄 옵션을 나열합니다.
  * `jl_uv_stderr` :: 누가 stdio와 상호작용할 수 있는 것을 싫어하겠어요?

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: gdb의 `thread apply all bt` 또는 lldb의 `thread backtrace all`과 유사합니다. 모든 스레드를 실행하면서 모든 기존 작업에 대한 백트레이스를 출력합니다.
  * `jl_gdblookup($pc)` :: 현재 함수와 라인을 찾기 위해 사용됩니다.
  * `jl_gdblookupinfo($pc)` :: 현재 메서드 인스턴스 객체를 찾기 위해 사용됩니다.
  * `jl_gdbdumpcode(mi)` :: REPL이 제대로 작동하지 않을 때 `code_typed/code_llvm/code_asm`의 모든 내용을 덤프하기 위한 것입니다.
  * `jlbacktrace()` :: 현재 Julia 백트레이스 스택을 stderr에 덤프하기 위한 것입니다. `record_backtrace()`가 호출된 후에만 사용할 수 있습니다.
  * `jl_dump_llvm_value(Value*)` :: GDB에서 기본적으로 작동하지 않는 `Value->dump()`를 호출하기 위해 사용됩니다. 예를 들어, `f->linfo->functionObject`, `f->linfo->specFunctionObject`, 및 `to_function(f->linfo)`가 있습니다.
  * `jl_dump_llvm_module(Module*)` :: GDB에서 기본적으로 작동하지 않는 `Module->dump()`를 호출하기 위해 사용됩니다.
  * `Type->dump()` :: lldb에서만 작동합니다. 참고: lldb가 출력 위에 프롬프트를 인쇄하지 않도록 `;1`과 같은 것을 추가하세요.
  * `jl_eval_string("expr")` :: 현재 상태를 수정하거나 기호를 조회하기 위해 부작용을 호출하는 데 사용됩니다.
  * `jl_typeof(jl_value_t*)` :: 줄리아 값의 타입 태그를 추출하기 위해 (gdb에서 먼저 `macro define jl_typeof jl_typeof`를 호출하거나, 첫 번째 인수에 대해 짧은 이름인 `ty`와 같은 것을 선택하세요)

## Inserting breakpoints for inspection from gdb

`gdb` 세션에서 `jl_breakpoint`에 중단점을 다음과 같이 설정하세요:

```
(gdb) break jl_breakpoint
```

그런 다음 Julia 코드 내에 `jl_breakpoint` 호출을 추가하여

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

`obj`는 중단점에서 접근할 수 있는 원하는 변수나 튜플이 될 수 있습니다.

`jl_apply` 프레임으로 백업하는 것은 특히 유용하며, 이를 통해 예를 들어 함수에 대한 인수를 표시할 수 있습니다.

```
(gdb) call jl_(args[0])
```

또 다른 유용한 프레임은 `to_function(jl_method_instance_t *li, bool cstyle)`입니다. `jl_method_instance_t*` 인자는 컴파일러에 전달된 최종 AST에 대한 참조가 있는 구조체입니다. 그러나 이 시점에서 AST는 일반적으로 압축되어 있습니다. AST를 보려면 `jl_uncompress_ast`를 호출한 다음 결과를 `jl_`에 전달하십시오:

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

파일 이름은 `sysimg.jl`입니다:

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

이 함수가 모든 호출에 사용되기 때문에, 이렇게 하면 모든 것이 1000배 느려질 것입니다.

## Dealing with signals

Julia는 제대로 작동하기 위해 몇 가지 신호가 필요합니다. 프로파일러는 샘플링을 위해 `SIGUSR2`를 사용하고, 가비지 컬렉터는 스레드 동기화를 위해 `SIGSEGV`를 사용합니다. 프로파일러나 여러 스레드를 사용하는 코드를 디버깅하는 경우, 이러한 신호가 정상 작동 중에 매우 자주 발생할 수 있으므로 디버거가 이러한 신호를 무시하도록 설정할 수 있습니다. GDB에서 이를 수행하는 명령은 다음과 같습니다(무시하려는 신호로 `SIGSEGV`를 `SIGUSR2` 또는 다른 신호로 교체하십시오):

```
(gdb) handle SIGSEGV noprint nostop pass
```

해당 LLDB 명령은 (프로세스가 시작된 후):

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

스레드 코드에서 세그멘테이션 오류를 디버깅하는 경우, GC 동기화 지점이 아닌 실제 세그멘테이션 오류만 포착하기 위해 `jl_critical_error`에 중단점을 설정할 수 있습니다 (`sigdie_handler`는 Linux 및 BSD에서도 작동해야 합니다).

## Debugging during Julia's build process (bootstrap)

`make` 중 발생하는 오류는 특별한 처리가 필요합니다. Julia는 두 단계로 빌드되며, `sys0`와 `sys.ji`를 구성합니다. 실패 시 어떤 명령이 실행되고 있는지 보려면 `make VERBOSE=1`을 사용하세요.

이 글을 작성하는 시점에서, `base` 디렉토리에서 `sys0` 단계 동안 빌드 오류를 디버깅할 수 있습니다:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

`usr/lib/julia/`의 모든 파일을 삭제해야 이 작업이 제대로 작동할 수 있습니다.

`sys.ji` 단계는 다음을 사용하여 디버깅할 수 있습니다:

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

기본적으로, 어떤 오류도 Julia가 종료되게 합니다. gdb 하에서도 마찬가지입니다. 오류를 "현장에서" 잡으려면 `jl_error`에 중단점을 설정하세요 (특정 종류의 실패를 위한 여러 유용한 지점이 있습니다. 예를 들어: `jl_too_few_args`, `jl_too_many_args`, 및 `jl_throw`).

오류가 포착되면 유용한 기술은 스택을 따라 올라가면서 관련된 `jl_apply` 호출을 검사하여 함수를 살펴보는 것입니다. 실제 사례를 들어보면:

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

가장 최근의 `jl_apply`는 프레임 #3에 있으므로, 거기로 돌아가서 함수 `julia_convert_16886`의 AST를 살펴볼 수 있습니다. 이것은 `convert`의 일부 메서드에 대한 고유한 이름입니다. 이 프레임의 `f`는 `jl_function_t*`이므로, `specTypes` 필드에서 타입 시그니처가 있다면 살펴볼 수 있습니다:

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

그럼, 이 함수의 AST를 살펴볼 수 있습니다:

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

마지막으로, 아마도 가장 유용하게, 우리는 함수를 다시 컴파일하도록 강제하여 코드 생성 과정을 단계별로 살펴볼 수 있습니다. 이를 위해 `jl_lamdbda_info_t*`에서 캐시된 `functionObject`를 지웁니다:

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

그런 다음 유용한 곳(예: `emit_function`, `emit_expr`, `emit_call` 등)에 중단점을 설정하고 코드 생성을 실행합니다:

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

모듈 사전 컴파일은 각 모듈을 사전 컴파일하기 위해 별도의 Julia 프로세스를 생성합니다. 사전 컴파일 작업자에서 중단점을 설정하거나 실패를 포착하려면 디버거를 작업자에 연결해야 합니다. 가장 쉬운 방법은 디버거가 주어진 이름과 일치하는 새로운 프로세스 시작을 감시하도록 설정하는 것입니다. 예를 들어:

```
(gdb) attach -w -n julia-debug
```

또는:

```
(lldb) process attach -w -n julia-debug
```

그런 다음 사전 컴파일을 시작하는 스크립트/명령을 실행합니다. 앞서 설명한 대로, 부모 프로세스에서 조건부 중단점을 사용하여 특정 파일 로딩 이벤트를 포착하고 디버깅 창을 좁힙니다. (일부 운영 체제에서는 부모 프로세스에서 각 `fork`를 따라가는 것과 같은 대체 접근 방식이 필요할 수 있습니다)

## Mozilla's Record and Replay Framework (rr)

줄리아는 이제 [rr](https://rr-project.org/)와 함께 작동합니다. 이는 모질라의 경량 기록 및 결정론적 디버깅 프레임워크입니다. 이를 통해 실행의 추적을 결정론적으로 재생할 수 있습니다. 재생된 실행의 주소 공간, 레지스터 내용, 시스템 호출 데이터 등은 모든 실행에서 정확히 동일합니다.

rr(3.1.0 이상)의 최신 버전이 필요합니다.

### Reproducing concurrency bugs with rr

rr은 기본적으로 단일 스레드 머신을 시뮬레이션합니다. 동시 코드를 디버깅하기 위해 `rr record --chaos`를 사용할 수 있으며, 이는 rr이 1개에서 8개 코어 사이에서 무작위로 선택하여 시뮬레이션하도록 합니다. 따라서 `JULIA_NUM_THREADS=8`을 설정하고 rr 아래에서 코드를 다시 실행하여 버그를 잡는 것이 좋습니다.

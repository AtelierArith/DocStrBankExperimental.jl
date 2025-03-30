# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h`는 `stdio.h` 스트림에 대한 [libuv](https://docs.libuv.org) 래퍼를 정의합니다:

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... 및 해당 출력 함수:

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

이 `printf` 함수는 `src/` 및 `cli/` 디렉토리의 `.c` 파일에서 표준 입출력이 필요한 곳에서 사용되어 출력 버퍼링이 통일된 방식으로 처리되도록 합니다.

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref), [`Base.stdout`](@ref) 및 [`Base.stderr`](@ref)는 런타임에 정의된 `JL_STD*` libuv 스트림에 바인딩되어 있습니다.

줄리아의 `__init__()` 함수(에서 `base/sysimg.jl`)는 `reinit_stdio()` (에서 `base/stream.jl`)를 호출하여 [`Base.stdin`](@ref), [`Base.stdout`](@ref) 및 [`Base.stderr`](@ref)에 대한 줄리아 객체를 생성합니다.

`reinit_stdio()`는 [`ccall`](@ref)를 사용하여 `JL_STD*`에 대한 포인터를 검색하고, 각 스트림의 유형을 검사하기 위해 `jl_uv_handle_type()`를 호출합니다. 그런 다음 각 스트림을 나타내기 위해 Julia `Base.IOStream`, `Base.TTY` 또는 `Base.PipeEndpoint` 객체를 생성합니다. 예:

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

[`Base.read`](@ref) 및 [`Base.write`](@ref) 메서드는 이러한 스트림에 대해 [`ccall`](@ref)를 사용하여 `src/jl_uv.c`에서 libuv 래퍼를 호출합니다. 예:

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

`jl_printf()` 등에서 의존하는 libuv 스트림은 런타임 초기화 중간까지 사용할 수 없습니다 (자세한 내용은 `init.c`, `init_stdio()` 참조). 이 이전에 출력해야 하는 오류 메시지나 경고는 다음 메커니즘을 통해 표준 C 라이브러리 `fwrite()` 함수로 라우팅됩니다:

`sys.c`에서 `JL_STD*` 스트림 포인터는 정수 상수 `STD*_FILENO (0, 1 및 2)`로 정적으로 초기화됩니다. `jl_uv.c`에서 `jl_uv_puts()` 함수는 `uv_stream_t* stream` 인수를 확인하고 스트림이 `STDOUT_FILENO` 또는 `STDERR_FILENO`로 설정되어 있으면 `fwrite()`를 호출합니다.

이것은 초기화가 완료되기 전에 특정 코드 조각에 접근할 수 있는지 여부와 관계없이 런타임 전반에 걸쳐 `jl_printf()`의 일관된 사용을 허용합니다.

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

`src/support/ios.c` 라이브러리는 [femtolisp](https://github.com/JeffBezanson/femtolisp)에서 상속됩니다. 이 라이브러리는 크로스 플랫폼 버퍼링된 파일 IO와 메모리 내 임시 버퍼를 제공합니다.

`ios.c`는 여전히 다음에서 사용됩니다:

  * `src/flisp/*.c`
  * `src/dump.c` – 직렬화 파일 IO 및 메모리 버퍼용.
  * `src/staticdata.c` – 직렬화 파일 IO 및 메모리 버퍼용.
  * `base/iostream.jl` – 파일 IO를 위한 것 (libuv에 해당하는 `base/fs.jl` 참조).

`ios.c`의 사용은 이러한 모듈에서 대부분 독립적이며 libuv I/O 시스템과 분리되어 있습니다. 그러나 [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654)에서 femtolisp는 레거시 `ios_t` 스트림을 사용하여 `jl_printf()`를 호출합니다.

`ios.h`에는 `ios_t.bm` 필드가 `uv_stream_t.type`과 정렬되도록 하는 해킹이 있으며, 이는 `ios_t.bm`에 사용되는 값이 유효한 `UV_HANDLE_TYPE` 값과 겹치지 않도록 보장합니다. 이를 통해 `uv_stream_t` 포인터가 `ios_t` 스트림을 가리킬 수 있습니다.

이것은 `jl_printf()` 호출자 `jl_static_show()`가 femtolisp의 `fl_print()` 함수에 의해 `ios_t` 스트림을 전달받기 때문에 필요합니다. Julia의 `jl_uv_puts()` 함수는 이를 특별히 처리합니다:

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```

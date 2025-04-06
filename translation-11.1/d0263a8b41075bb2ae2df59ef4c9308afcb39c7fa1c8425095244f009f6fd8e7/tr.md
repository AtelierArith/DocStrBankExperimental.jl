# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h` `stdio.h` akışları için [libuv](https://docs.libuv.org) sarmalayıcıları tanımlar:

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... ve karşılık gelen çıktı fonksiyonları:

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

Bu `printf` fonksiyonları, çıktı tamponlamasının birleştirilmiş bir şekilde yönetilmesini sağlamak için `src/` ve `cli/` dizinlerindeki `.c` dosyaları tarafından gerektiği yerlerde kullanılır.

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref), [`Base.stdout`](@ref) ve [`Base.stderr`](@ref) çalışma zamanında tanımlanan `JL_STD*` libuv akışlarına bağlıdır.

Julia'nın `__init__()` fonksiyonu (`base/sysimg.jl` içinde) `reinit_stdio()` ( `base/stream.jl` içinde) çağırarak [`Base.stdin`](@ref), [`Base.stdout`](@ref) ve [`Base.stderr`](@ref) için Julia nesneleri oluşturur.

`reinit_stdio()` [`ccall`](@ref) kullanarak `JL_STD*` için işaretçileri alır ve her akışın türünü denetlemek için `jl_uv_handle_type()` çağrısını yapar. Ardından, her akışı temsil etmek için bir Julia `Base.IOStream`, `Base.TTY` veya `Base.PipeEndpoint` nesnesi oluşturur, örn.:

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

[`Base.read`](@ref) ve [`Base.write`](@ref) yöntemleri bu akışlar için [`ccall`](@ref) kullanarak `src/jl_uv.c` içindeki libuv sarmalayıcılarını çağırır, örneğin:

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

`jl_printf()` vb. gibi `libuv` akışları, çalışma zamanının başlatılmasının ortalarına kadar mevcut değildir (bkz. `init.c`, `init_stdio()`). Bu noktadan önce yazdırılması gereken hata mesajları veya uyarılar, aşağıdaki mekanizma ile standart C kütüphanesi `fwrite()` fonksiyonuna yönlendirilir:

`sys.c` dosyasında, `JL_STD*` akış işaretçileri tam sayı sabitlerine statik olarak başlatılmıştır: `STD*_FILENO (0, 1 ve 2)`. `jl_uv.c` dosyasında `jl_uv_puts()` fonksiyonu `uv_stream_t* stream` argümanını kontrol eder ve akış `STDOUT_FILENO` veya `STDERR_FILENO` olarak ayarlandığında `fwrite()` çağrısını yapar.

Bu, belirli bir kod parçasının başlatma tamamlanmadan önce erişilebilir olup olmamasına bakılmaksızın, çalışma zamanı boyunca `jl_printf()`'ın tutarlı bir şekilde kullanılmasına olanak tanır.

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

`src/support/ios.c` kütüphanesi [femtolisp](https://github.com/JeffBezanson/femtolisp)'den miras alınmıştır. Bu, çapraz platform tamponlu dosya G/Ç ve bellek içi geçici tamponlar sağlar.

`ios.c` hala şu tarafından kullanılmaktadır:

  * `src/flisp/*.c`
  * `src/dump.c` – serileştirme dosyası IO ve bellek tamponları için.
  * `src/staticdata.c` – serileştirme dosyası IO ve bellek tamponları için.
  * `base/iostream.jl` – dosya IO için (libuv eşdeğeri için `base/fs.jl`'ye bakın).

`ios.c` bu modüllerde çoğunlukla kendine özgü ve libuv I/O sisteminden ayrıdır. Ancak, femtolisp'in bir eski `ios_t` akışı ile `jl_printf()`'e çağrıda bulunduğu [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654) bulunmaktadır.

`ios.h` dosyasında, `ios_t.bm` alanının `uv_stream_t.type` ile hizalanmasını sağlayan bir hack bulunmaktadır ve bu, `ios_t.bm` için kullanılan değerlerin geçerli `UV_HANDLE_TYPE` değerleriyle çakışmamasını garanti eder. Bu, `uv_stream_t` işaretçilerinin `ios_t` akışlarına işaret etmesine olanak tanır.

Bu, `jl_printf()` çağrısı `jl_static_show()`'a femtolisp'in `fl_print()` fonksiyonu tarafından bir `ios_t` akışı geçirildiği için gereklidir. Julia'nın `jl_uv_puts()` fonksiyonu bunun için özel bir işleme sahiptir:

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```

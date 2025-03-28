# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers) se puede utilizar en compilaciones personalizadas de Julia para facilitar la detección de ciertos tipos de errores en el código interno en C/C++ de Julia.

## Address Sanitizer: easy build

Desde una verificación de origen de Julia, deberías poder construir una versión que soporte la sanitización de direcciones en Julia y LLVM de la siguiente manera:

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

Aquí hemos elegido `/tmp/julia` como un directorio de construcción, pero puedes elegir lo que desees. Una vez construido, ejecuta la carga de trabajo que deseas probar con `/tmp/julia/julia`. Los errores de memoria resultarán en errores.

Si necesitas personalización o más detalles, consulta la documentación a continuación.

## General considerations

Usar los sanitizadores de Clang obviamente requiere que uses Clang (`USECLANG=1`), pero hay otra trampa: la mayoría de los sanitizadores requieren una biblioteca de tiempo de ejecución, proporcionada por el compilador anfitrión, mientras que el código instrumentado generado por el JIT de Julia depende de la funcionalidad de esa biblioteca. Esto implica que la versión de LLVM de tu compilador anfitrión debe coincidir con la de la biblioteca LLVM utilizada dentro de Julia.

Una solución fácil es tener una carpeta de construcción dedicada para proporcionar una herramienta de coincidencia, construyendo con `BUILD_LLVM_CLANG=1`. Luego puedes referirte a esta herramienta desde otra carpeta de construcción especificando `USECLANG=1` mientras sobrescribes las variables `CC` y `CXX`.

Los sanitizadores generan errores cuando detectan que se está abriendo una biblioteca compartida utilizando `RTLD_DEEPBIND` (ref: [google/sanitizers#611](https://github.com/google/sanitizers/issues/611)). Dado que [libblastrampoline](https://github.com/staticfloat/libblastrampoline) utiliza por defecto `RTLD_DEEPBIND`, necesitamos establecer la variable de entorno `LBT_USE_RTLD_DEEPBIND=0` al usar un sanitizador.

Para usar uno de los sanitizadores, establece `SANITIZE=1` y luego la bandera apropiada para el sanitizador que deseas usar.

En macOS, esto podría necesitar algunas banderas adicionales para funcionar. En conjunto, podría verse así, más una o más de las banderas `SANITIZE_*` enumeradas a continuación:

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

(o pon esto en tu `Make.user`, para que no necesites recordarlo cada vez).

## Address Sanitizer (ASAN)

Para detectar o depurar errores de memoria, puedes usar [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html) de Clang. Al compilar con `SANITIZE_ADDRESS=1` habilitas ASAN para el compilador de Julia y su código generado. Además, puedes especificar `LLVM_SANITIZE=1` para sanitizar la biblioteca LLVM también. Ten en cuenta que estas opciones incurren en un alto costo de rendimiento y memoria. Por ejemplo, usar ASAN para Julia y LLVM hace que `testall1` tarde de 8 a 10 veces más mientras utiliza 20 veces más memoria (esto se puede reducir a un factor de 3 y 4 respectivamente utilizando las opciones descritas a continuación).

Por defecto, Julia establece la bandera `allow_user_segv_handler=1` de ASAN, que es necesaria para que la entrega de señales funcione correctamente. Puedes definir otras opciones utilizando la bandera de entorno `ASAN_OPTIONS`, en cuyo caso necesitarás repetir la opción predeterminada mencionada anteriormente. Por ejemplo, el uso de memoria se puede reducir especificando `fast_unwind_on_malloc=0` y `malloc_context_size=2`, a costa de la precisión del backtrace. Por ahora, Julia también establece `detect_leaks=0`, pero esto debería eliminarse en el futuro.

### Example setup

#### Step 1: Install toolchain

Verifica un worktree de Git (o crea un directorio de construcción fuera del árbol) en `$TOOLCHAIN_WORKTREE` y crea un archivo de configuración `$TOOLCHAIN_WORKTREE/Make.user` con

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

Ejecutar:

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

para instalar los binarios de la cadena de herramientas en `$TOOLCHAIN_WORKTREE/usr/tools`

#### Step 2: Build Julia with ASAN

Verifica un worktree de Git (o crea un directorio de construcción fuera del árbol) en `$BUILD_WORKTREE` y crea un archivo de configuración `$BUILD_WORKTREE/Make.user` con

```
TOOLCHAIN=$(TOOLCHAIN_WORKTREE)/usr/tools

# use our new toolchain
USECLANG=1
override CC=$(TOOLCHAIN)/clang
override CXX=$(TOOLCHAIN)/clang++
export ASAN_SYMBOLIZER_PATH=$(TOOLCHAIN)/llvm-symbolizer

USE_BINARYBUILDER_LLVM=1

override SANITIZE=1
override SANITIZE_ADDRESS=1

# make the GC use regular malloc/frees, which are hooked by ASAN
override WITH_GC_DEBUG_ENV=1

# default to a debug build for better line number reporting
override JULIA_BUILD_MODE=debug

# make ASAN consume less memory
export ASAN_OPTIONS=detect_leaks=0:fast_unwind_on_malloc=0:allow_user_segv_handler=1:malloc_context_size=2

JULIA_PRECOMPILE=1

# tell libblastrampoline to not use RTLD_DEEPBIND
export LBT_USE_RTLD_DEEPBIND=0
```

Ejecutar:

```sh
cd $BUILD_WORKTREE
make debug
```

para construir `julia-debug` con ASAN.

## Memory Sanitizer (MSAN)

Para detectar el uso de memoria no inicializada, puedes usar [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html) de Clang compilando con `SANITIZE_MEMORY=1`.

## Thread Sanitizer (TSAN)

Para depurar condiciones de carrera y otros problemas relacionados con hilos, puedes usar Clang's [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html) compilando con `SANITIZE_THREAD=1`.

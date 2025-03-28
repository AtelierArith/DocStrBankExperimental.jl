# Building Julia (Detailed)

## Downloading the Julia source code

Si estás detrás de un firewall, es posible que necesites usar el protocolo `https` en lugar del protocolo `git`:

```sh
git config --global url."https://".insteadOf git://
```

Asegúrate de configurar también tu sistema para usar la configuración de proxy adecuada, por ejemplo, estableciendo las variables `https_proxy` y `http_proxy`.

## Building Julia

Cuando se compila por primera vez, la construcción descargará automáticamente el precompilado [external dependencies](#Required-Build-Tools-and-External-Libraries). Si prefieres compilar todas las dependencias por tu cuenta, o estás construyendo en un sistema que no puede acceder a la red durante el proceso de construcción, agrega lo siguiente en `Make.user`:

```
USE_BINARYBUILDER=0
```

Construir Julia requiere 5GiB si se construyen todas las dependencias y aproximadamente 4GiB de memoria virtual.

Para realizar una construcción paralela, utiliza `make -j N` y proporciona el número máximo de procesos concurrentes. Si los valores predeterminados en la construcción no funcionan para ti, y necesitas establecer parámetros específicos de make, puedes guardarlos en `Make.user` y colocar el archivo en la raíz de tu fuente de Julia. La construcción verificará automáticamente la existencia de `Make.user` y lo utilizará si existe.

Puedes crear compilaciones fuera del árbol de Julia especificando `make O=<directorio-de-compilación> configure` en la línea de comandos. Esto creará un espejo de directorio, con todos los Makefiles necesarios para compilar Julia, en el directorio especificado. Estas compilaciones compartirán los archivos fuente en Julia y `deps/srccache`. Cada directorio de compilación fuera del árbol puede tener su propio archivo `Make.user` para anular el archivo global `Make.user` en la carpeta de nivel superior.

Si todo funciona correctamente, verás un banner de Julia y un aviso interactivo en el que puedes ingresar expresiones para su evaluación. (Los errores relacionados con las bibliotecas pueden ser causados por bibliotecas antiguas e incompatibles que están en tu PATH. En este caso, intenta mover el directorio `julia` más arriba en el PATH). Ten en cuenta que la mayoría de las instrucciones anteriores se aplican a sistemas unix.

Para ejecutar julia desde cualquier lugar, puedes:

  * agrega un alias (en `bash`: `echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`), o
  * agrega un enlace simbólico al ejecutable `julia` en el directorio `julia` a `/usr/local/bin` (o cualquier directorio adecuado que ya esté en tu ruta), o
  * agrega el directorio `julia` a tu ruta ejecutable para esta sesión de shell (en `bash`: `export PATH="$(pwd):$PATH"` ; en `csh` o `tcsh`:

`set path= ( $path $cwd )` ), o

  * agrega el directorio `julia` a tu ruta ejecutable de forma permanente (por ejemplo, en `.bash_profile`), o
  * escribe `prefix=/path/to/install/folder` en `Make.user` y luego ejecuta `make install`. Si ya hay una versión de Julia instalada en esta carpeta, debes eliminarla antes de ejecutar `make install`.

Algunas de las opciones que puedes configurar para controlar la construcción de Julia están listadas y documentadas al principio del archivo `Make.inc`, pero nunca debes editarlo para este propósito, usa `Make.user` en su lugar.

Los Makefiles de Julia definen reglas automáticas convenientes llamadas `print-<NOMBRE_VARIABLE>` para imprimir el valor de las variables, reemplazando `<NOMBRE_VARIABLE>` con el nombre de la variable cuyo valor se desea imprimir. Por ejemplo

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

Estas reglas son útiles para propósitos de depuración.

Ahora deberías poder ejecutar Julia así:

```
julia
```

Si estás construyendo un paquete de Julia para distribución en Linux, macOS o Windows, echa un vistazo a las notas detalladas en [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md).

## Updating an existing source tree

Si has descargado previamente `julia` usando `git clone`, puedes actualizar el árbol de fuentes existente usando `git pull` en lugar de comenzar de nuevo:

```sh
cd julia
git pull && make
```

Suponiendo que no has realizado cambios en el árbol fuente que entren en conflicto con las actualizaciones de upstream, estos comandos activarán una compilación para actualizar a la última versión.

## General troubleshooting

1. Con el tiempo, la biblioteca base puede acumular suficientes cambios de modo que el proceso de arranque para construir la imagen del sistema falle. Si esto sucede, la construcción puede fallar con un error como

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    Como se describe, ejecutar `make clean && make` suele ser suficiente. Ocasionalmente, se necesita la limpieza más fuerte realizada por `make cleanall`.
2. Nuevas versiones de dependencias externas pueden ser introducidas, lo que puede ocasionalmente causar conflictos con las compilaciones existentes de versiones anteriores.

    a. Existen objetivos especiales de `make` para ayudar a limpiar la construcción existente de una dependencia. Por ejemplo, `make -C deps clean-llvm` limpiará la construcción existente de `llvm` para que `llvm` se reconstruya a partir de la distribución de origen descargada la próxima vez que se llame a `make`. `make -C deps distclean-llvm` es una limpieza más fuerte que también eliminará la distribución de origen descargada, asegurando que se descargue una copia nueva de la distribución de origen y que se apliquen cualquier nuevo parche la próxima vez que se llame a `make`.

    b. Para eliminar los binarios existentes de `julia` y todas sus dependencias, elimina el directorio `./usr` *en el árbol de origen*.
3. Si has actualizado macOS recientemente, asegúrate de ejecutar `xcode-select --install` para actualizar las herramientas de línea de comandos. De lo contrario, podrías encontrarte con errores por encabezados y bibliotecas faltantes, como `ld: library not found for -lcrt1.10.6.o`.
4. Si has movido el directorio fuente, podrías obtener errores como `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.`, en cuyo caso puedes eliminar la dependencia problemática bajo `deps`.
5. En casos extremos, es posible que desees restablecer el árbol de origen a un estado prístino. Los siguientes comandos de git pueden ser útiles:

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *Para evitar perder trabajo, asegúrate de saber qué hacen estos comandos antes de ejecutarlos. `git` no podrá deshacer estos cambios!*

## Platform-Specific Notes

Notas para varios sistemas operativos:

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

Notas para varias arquitecturas:

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

Construir Julia requiere que el siguiente software esté instalado:

  * **[GNU make]**                — construyendo dependencias.
  * **[gcc & g++][gcc]** (>= 7.1) o **[Clang][clang]** (>= 5.0, >= 9.3 para Apple Clang) — compilando y vinculando C, C++.
  * **[libatomic][gcc]**          — proporcionado por **[gcc]** y necesario para soportar operaciones atómicas.
  * **[python]** (>=2.7)          — necesario para construir LLVM.
  * **[gfortran]**                — compilando y vinculando bibliotecas de Fortran.
  * **[perl]**                    — preprocesamiento de archivos de encabezado de bibliotecas.
  * **[wget]**, **[curl]**, o **[fetch]** (FreeBSD) — para descargar automáticamente bibliotecas externas.
  * **[m4]**                      — necesario para construir GMP.
  * **[awk]**                     — herramienta auxiliar para Makefiles.
  * **[patch]**                   — para modificar el código fuente.
  * **[cmake]** (>= 3.4.3)        — necesario para construir `libgit2`.
  * **[pkg-config]**              — necesario para construir `libgit2` correctamente, especialmente para el soporte de proxy.
  * **[powershell]** (>= 3.0)     — necesario solo en Windows.
  * **[cuál]**                   — necesario para verificar las dependencias de construcción.

En distribuciones basadas en Debian (por ejemplo, Ubuntu), puedes instalarlos fácilmente con `apt-get`:

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

Julia utiliza las siguientes bibliotecas externas, que se descargan automáticamente (o en algunos casos, se incluyen en el repositorio de código fuente de Julia) y luego se compilan desde el código fuente la primera vez que ejecutas `make`. Los números de versión específicos de estas bibliotecas que utiliza Julia se enumeran en [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/).

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — infraestructura del compilador (ver [note below](#llvm)).
  * **[FemtoLisp]**            — empaquetado con el código fuente de Julia, y utilizado para implementar la interfaz del compilador.
  * **[libuv]**  (bifurcación personalizada) — biblioteca de E/S basada en eventos, portátil y de alto rendimiento.
  * **[OpenLibm]**             — biblioteca libm portátil que contiene funciones matemáticas elementales.
  * **[DSFMT]**                — biblioteca de generador de números pseudorandom de Mersenne Twister rápida.
  * **[OpenBLAS]**             — rápido, abierto y mantenido [subprogramas básicos de álgebra lineal (BLAS)]
  * **[LAPACK]**               — biblioteca de rutinas de álgebra lineal para resolver sistemas de ecuaciones lineales simultáneas, soluciones de mínimos cuadrados de sistemas de ecuaciones lineales, problemas de valores propios y problemas de valores singulares.
  * **[MKL]** (opcional)       – OpenBLAS y LAPACK pueden ser reemplazados por la biblioteca MKL de Intel.
  * **[SuiteSparse]**          — biblioteca de rutinas de álgebra lineal para matrices dispersas.
  * **[PCRE]**                 — Biblioteca de expresiones regulares compatible con Perl.
  * **[GMP]**                  — Biblioteca de aritmética de múltiples precisiones de GNU, necesaria para el soporte de `BigInt`.
  * **[MPFR]**                 — Biblioteca de punto flotante de precisión múltiple de GNU, necesaria para el soporte de punto flotante de precisión arbitraria (`BigFloat`).
  * **[libgit2]**              — Biblioteca enlazable de Git, utilizada por el gestor de paquetes de Julia.
  * **[curl]**                 — libcurl proporciona soporte de descarga y proxy.
  * **[libssh2]**              — biblioteca para transporte SSH, utilizada por libgit2 para paquetes con remotos SSH.
  * **[mbedtls]**              — biblioteca utilizada para criptografía y seguridad de capa de transporte, utilizada por libssh2
  * **[utf8proc]**             — una biblioteca para procesar cadenas Unicode codificadas en UTF-8.
  * **[LLVM libunwind]** — La bifurcación de LLVM de [libunwind], una biblioteca que determina la cadena de llamadas de un programa.
  * **[ITTAPI]**               — Tecnología de Instrumentación y Trazado de Intel y API Just-In-Time.

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

Si ya tienes uno o más de estos paquetes instalados en tu sistema, puedes evitar que Julia compile duplicados de estas bibliotecas pasando `USE_SYSTEM_...=1` a `make` o añadiendo la línea a `Make.user`. La lista completa de posibles flags se puede encontrar en `Make.inc`.

Tenga en cuenta que este procedimiento no está oficialmente soportado, ya que introduce variabilidad adicional en la instalación y versionado de las dependencias, y se recomienda solo para los mantenedores de paquetes del sistema. Pueden resultar errores de compilación inesperados, ya que el sistema de construcción no realizará más comprobaciones para asegurar que los paquetes adecuados estén instalados.

### LLVM

La dependencia más complicada es LLVM, para la cual requerimos parches adicionales de upstream (LLVM no es compatible hacia atrás).

Para empaquetar Julia con LLVM, recomendamos cualquiera de las siguientes opciones:

  * empaquetando una biblioteca LLVM solo de Julia dentro del paquete de Julia, o
  * agregando los parches al paquete LLVM de la distribución.

      * Una lista completa de parches está disponible en [Github](https://github.com/JuliaLang/llvm-project), consulta la rama `julia-release/15.x`.
      * El único parche específico de Julia es el cambio de nombre de la biblioteca (`llvm7-symver-jlprefix.patch`), que *no* debe aplicarse a un LLVM del sistema.
      * Los parches restantes son todas correcciones de errores en upstream, y han sido contribuidos al LLVM upstream.

Usar una versión de LLVM no parcheada o diferente resultará en errores y/o un rendimiento deficiente. Puedes construir una versión diferente de LLVM desde un repositorio Git remoto con las siguientes opciones en el archivo `Make.user`:

```make
# Force source build of LLVM
USE_BINARYBUILDER_LLVM = 0
# Use Git for fetching LLVM source code
# this is either `1` to get all of them
DEPS_GIT = 1
# or a space-separated list of specific dependencies to download with git
DEPS_GIT = llvm

# Other useful options:
#URL of the Git repository you want to obtain LLVM from:
#  LLVM_GIT_URL = ...
#Name of the alternate branch to clone from git
#  LLVM_BRANCH = julia-16.0.6-0
#SHA hash of the alterate commit to check out automatically
#  LLVM_SHA1 = $(LLVM_BRANCH)
#List of LLVM targets to build.  It is strongly recommended to keep at least all the
#default targets listed in `deps/llvm.mk`, even if you don't necessarily need all of them.
#  LLVM_TARGETS = ...
#Use ccache for faster recompilation in case you need to restart a build.
#  USECCACHE = 1
#  CMAKE_GENERATOR=Ninja
#  LLVM_ASSERTIONS=1
#  LLVM_DEBUG=Symbols
```

Las diversas fases de construcción están controladas por archivos específicos:

  * `deps/llvm.version` : toca o cambia para revisar una nueva versión, `make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : resultado de `make extract-llvm`
  * `deps/llvm/build_Release*/build-configured` : resultado de `make configure-llvm`
  * `deps/llvm/build_Release*/build-configured` : resultado de `make compile-llvm`
  * `usr-staging/llvm/build_Release*.tgz` : resultado de `make stage-llvm` (regenerar con `make reinstall-llvm`)
  * `usr/manifest/llvm` : resultado de `make install-llvm` (regenerar con `make uninstall-llvm`)
  * `make version-check-llvm` : se ejecuta cada vez para advertir al usuario si hay modificaciones locales

Aunque Julia se puede construir con versiones más nuevas de LLVM, el soporte para esto debe considerarse experimental y no adecuado para empaquetar.

### libuv

Julia utiliza un fork personalizado de libuv. Es una dependencia pequeña y se puede incluir de manera segura en el mismo paquete que Julia, y no entrará en conflicto con la biblioteca del sistema. Las compilaciones de Julia *no* deben intentar usar la biblioteca libuv del sistema.

### BLAS and LAPACK

Como un lenguaje numérico de alto rendimiento, Julia debe estar vinculado a un BLAS y LAPACK multihilo, como OpenBLAS o ATLAS, que proporcionarán un rendimiento mucho mejor que las implementaciones de referencia `libblas` que pueden ser predeterminadas en algunos sistemas.

## Source distributions of releases

Cada pre-lanzamiento y lanzamiento de Julia tiene una distribución de fuente "completa" y una distribución de fuente "ligera".

La distribución completa de origen contiene el código fuente de Julia y todas las dependencias para que se pueda compilar desde el origen sin una conexión a Internet. La distribución de origen ligera no incluye el código fuente de las dependencias.

Por ejemplo, `julia-1.0.0.tar.gz` es la distribución de código fuente ligera para la versión `v1.0.0` de Julia, mientras que `julia-1.0.0-full.tar.gz` es la distribución de código fuente completa.

## Building Julia from source with a Git checkout of a stdlib

Si necesitas construir Julia desde el código fuente con una verificación de Git de una stdlib, entonces usa `make DEPS_GIT=NOMBRE_DE_LA_STDLIB` al construir Julia.

Por ejemplo, si necesitas construir Julia desde el código fuente con un checkout de Git de Pkg, entonces usa `make DEPS_GIT=Pkg` al construir Julia. El repositorio `Pkg` está en `stdlib/Pkg`, y se creó inicialmente con un `HEAD` separado. Si estás haciendo esto desde un repositorio de Julia preexistente, es posible que necesites `make clean` antes.

Si necesitas construir Julia desde el código fuente con checkouts de Git de más de una stdlib, entonces `DEPS_GIT` debe ser una lista separada por espacios de los nombres de las stdlib. Por ejemplo, si necesitas construir Julia desde el código fuente con un checkout de Git de Pkg, Tar y Downloads, entonces usa `make DEPS_GIT='Pkg Tar Downloads'` al construir Julia.

## Building an "assert build" of Julia

Un "build de aserción" de Julia es un build que se construyó con `FORCE_ASSERTIONS=1` y `LLVM_ASSERTIONS=1`. Para construir un build de aserción, define ambas de las siguientes variables en tu archivo `Make.user`:

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

Tenga en cuenta que las compilaciones de Julia con aserciones serán más lentas que las compilaciones regulares (sin aserciones).

## Building 32-bit Julia on a 64-bit machine

Ocasionalmente, pueden surgir errores específicos de arquitecturas de 32 bits, y cuando esto sucede, es útil poder depurar el problema en tu máquina local. Dado que la mayoría de los sistemas modernos de 64 bits admiten la ejecución de programas construidos para sistemas de 32 bits, si no necesitas recompilar Julia desde el código fuente (por ejemplo, si solo necesitas inspeccionar el comportamiento de una Julia de 32 bits sin tener que tocar el código C), probablemente puedas usar una versión de 32 bits de Julia para tu sistema que puedes obtener de [official downloads page](https://julialang.org/downloads/). Sin embargo, si necesitas recompilar Julia desde el código fuente, una opción es usar un contenedor Docker de un sistema de 32 bits. Al menos por ahora, construir una versión de 32 bits de Julia es relativamente sencillo usando [ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu). En resumen, después de configurar `docker`, aquí están los pasos requeridos:

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

En este punto, deberías estar en una consola de máquina de 32 bits (ten en cuenta que `uname` informa la arquitectura del host, por lo que seguirá diciendo 64 bits, pero esto no afectará la compilación de Julia). Puedes agregar paquetes y compilar código; cuando `salgas`, todos los cambios se perderán, así que asegúrate de terminar tu análisis en una sola sesión o configura un script que puedas copiar/pegar para usar para configurar tu entorno.

Desde este punto, deberías

```sh
# apt update
```

(Tenga en cuenta que `sudo` no está instalado, pero tampoco es necesario ya que está ejecutándose como `root`, por lo que puede omitir `sudo` de todos los comandos.)

Luego agrega todos los [build dependencies](#required-build-tools-and-external-libraries), un editor basado en consola de tu elección, `git`, y cualquier otra cosa que necesites (por ejemplo, `gdb`, `rr`, etc). Elige un directorio para trabajar y `git clone` Julia, selecciona la rama que deseas depurar y compila Julia como de costumbre.

## Update the version number of a dependency

Hay dos tipos de construcciones.

1. Construir todo (`deps/` y `src/`) desde el código fuente.  (Agrega `USE_BINARYBUILDER=0` a `Make.user`, consulta [Building Julia](#building-julia))
2. Compilar desde la fuente (`src/`) con dependencias precompiladas (predeterminado)

Cuando desees actualizar el número de versión de una dependencia en `deps/`, es posible que desees utilizar la siguiente lista de verificación:

```md
### Check list

Version numbers:
- [ ] `deps/$(libname).version`: `LIBNAME_VER`, `LIBNAME_BRANCH`, `LIBNAME_SHA1` and `LIBNAME_JLL_VER`
- [ ] `stdlib/$(LIBNAME_JLL_NAME)_jll/Project.toml`: `version`

Checksum:
- [ ] `deps/checksums/$(libname)`
- [ ] `deps/checksums/$(LIBNAME_JLL_NAME)-*/`: `md5` and `sha512`

Patches:
- [ ] `deps/$(libname).mk`
- [ ] `deps/patches/$(libname)-*.patch`
```

Nota:

  * Para dependencias específicas, algunos elementos en la lista de verificación pueden no existir.
  * Para el archivo de suma de verificación, puede ser **un solo archivo** sin sufijo, o **una carpeta** que contenga dos archivos.

### Example: `OpenLibm`

1. Actualizar los números de versión en `deps/openlibm.version`

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = nuevo-hash-sha1`
2. Actualizar el número de versión en `stdlib/OpenLibm_jll/Project.toml`

      * `versión = "0.X.Y+0"`
3. Actualiza los checksums en `deps/checksums/openlibm`

      * `make -f contrib/refresh_checksums.mk openlibm`
4. Verifica si los archivos de parche `deps/patches/openlibm-*.patch` existen.

      * si los parches no existen, omitir.
      * si existen parches, verifica si han sido fusionados en la nueva versión y necesitan ser eliminados. Al eliminar un parche, recuerda modificar el archivo Makefile correspondiente (`deps/openlibm.mk`).

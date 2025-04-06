# Windows

Este archivo describe cómo instalar, construir y usar Julia en Windows.

Para obtener más información general sobre Julia, consulte el [main README](https://github.com/JuliaLang/julia/blob/master/README.md) o el [documentation](https://docs.julialang.org).

## General Information for Windows

Recomendamos encarecidamente ejecutar Julia utilizando una aplicación de terminal moderna, en particular Windows Terminal, que se puede instalar desde el [Microsoft Store](https://aka.ms/terminal).

### Line endings

Julia utiliza archivos en modo binario exclusivamente. A diferencia de muchos otros programas de Windows, si escribes `\n` en un archivo, obtienes un `\n` en el archivo, no algún otro patrón de bits. Esto coincide con el comportamiento exhibido por otros sistemas operativos. Si has instalado Git para Windows, se sugiere, pero no es obligatorio, que configures tu Git del sistema para usar la misma convención:

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

o edita `%USERPROFILE%\.gitconfig` y agrega/edita las líneas:

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

Para las notas de instalación de la distribución binaria en Windows, consulte las instrucciones en [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows).

## Source distribution

### Cygwin-to-MinGW cross-compiling

La forma recomendada de compilar Julia desde el código fuente en Windows es mediante la compilación cruzada desde [Cygwin](https://www.cygwin.com), utilizando versiones de los compiladores MinGW-w64 disponibles a través del gestor de paquetes de Cygwin.

1. Descarga y ejecuta la configuración de Cygwin para [32 bit](https://cygwin.com/setup-x86.exe) o [64 bit](https://cygwin.com/setup-x86_64.exe). Ten en cuenta que puedes compilar Julia de 32 o 64 bits desde Cygwin de 32 o 64 bits. Cygwin de 64 bits tiene una selección de paquetes ligeramente más pequeña pero a menudo más actualizada.

    *Avanzado*: puedes omitir los pasos 2-4 ejecutando:

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    replacing `<url>` with a site from [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) or run setup manually first and select a mirror.
2. Seleccione la ubicación de instalación y un espejo para descargar.
3. En el paso *Seleccionar Paquetes*, selecciona lo siguiente:

    1. Desde la categoría *Devel*: `cmake`, `gcc-g++`, `git`, `make`, `patch`
    2. Desde la categoría *Net*: `curl`
    3. De la categoría *Intérpretes* (o *Python*): `m4`, `python3`
    4. De la categoría *Archivo*: `p7zip`
    5. Para Julia de 32 bits, y también de la categoría *Devel*: `mingw64-i686-gcc-g++` y `mingw64-i686-gcc-fortran`
    6. Para Julia de 64 bits, y también de la categoría *Devel*: `mingw64-x86_64-gcc-g++` y `mingw64-x86_64-gcc-fortran`
4. Permita que la instalación de Cygwin finalice, luego inicie desde el acceso directo instalado *'Cygwin Terminal'*, o *'Cygwin64 Terminal'*, respectivamente.
5. Construir Julia y sus dependencias desde el código fuente:

    1. Obtén las fuentes de Julia

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        Consejo: Si recibes un `error: cannot fork() for fetch-pack: Resource temporarily unavailable` de git, añade `alias git="env PATH=/usr/bin git"` a `~/.bashrc` y reinicia Cygwin.
    2. Establece la variable `XC_HOST` en `Make.user` para indicar la compilación cruzada de MinGW-w64.

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. Iniciar la construcción

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. Ejecuta Julia utilizando los ejecutables de Julia directamente

    ```sh
    usr/bin/julia.exe
    usr/bin/julia-debug.exe
    ```

!!! note "Pro tip: build both!"
    ```sh
    make O=julia-win32 configure
    make O=julia-win64 configure
    echo 'XC_HOST = i686-w64-mingw32' > julia-win32/Make.user
    echo 'XC_HOST = x86_64-w64-mingw32' > julia-win64/Make.user
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-win32  # build for Windows x86 in julia-win32 folder
    make -C julia-win64  # build for Windows x86-64 in julia-win64 folder
    ```


### Compiling with MinGW/MSYS2

[MSYS2](https://www.msys2.org/) es un entorno de distribución y construcción de software para Windows.

Nota: MSYS2 requiere **Windows 7 de 64 bits** o más reciente.

1. Instalar y configurar MSYS2.

    1. Descarga y ejecuta el instalador más reciente para la [64-bit](https://github.com/msys2/msys2-installer/releases/latest) distribución. El instalador tendrá un nombre como `msys2-x86_64-yyyymmdd.exe`.
    2. Abre la terminal de MSYS2. Actualiza la base de datos de paquetes y los paquetes base:

        `pacman -Syu`
    3. Salga y reinicie MSYS2. Actualice el resto de los paquetes base:

        `pacman -Syu`
    4. Luego instala las herramientas necesarias para construir julia:

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        Para Julia de 64 bits, instala la versión x86_64:

        `pacman -S mingw-w64-x86_64-gcc`

        Para Julia de 32 bits, instala la versión i686:

        `pacman -S mingw-w64-i686-gcc`
    5. La configuración de MSYS2 está completa. Ahora `salir` de la shell de MSYS2.
2. Construir Julia y sus dependencias con dependencias preconstruidas.

    1. Abre un nuevo [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview). Actualmente no podemos usar tanto mingw32 como mingw64, así que si deseas construir las versiones x86_64 e i686, necesitarás construirlas en cada entorno por separado.
    2. Clona las fuentes de Julia:

        `git clone https://github.com/JuliaLang/julia.git  cd julia`
    3. Iniciar la construcción

        `make -j$(nproc)`

!!! note "Pro tip: build in dir"
    ```sh
    make O=julia-mingw-w64 configure
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-mingw-w64
    ```


### Cross-compiling from Unix (Linux/Mac/WSL)

También puedes usar compiladores cruzados MinGW-w64 para construir una versión de Windows de Julia desde Linux, Mac o el Subsistema de Windows para Linux (WSL).

Primero, necesitarás asegurarte de que tu sistema tenga las dependencias requeridas. Necesitamos wine (>=1.7.5), un compilador del sistema y algunos descargadores. Nota: una instalación de Cygwin podría interferir con este método si se utiliza WSL.

**En Ubuntu** (en otros sistemas Linux, los nombres de las dependencias probablemente sean similares):

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**En Mac**: Instala XCode, las herramientas de línea de comandos de XCode, X11 (ahora [XQuartz](https://www.xquartz.org/)), y [MacPorts](https://www.macports.org/install.php) o [Homebrew](https://brew.sh/). Luego ejecuta `port install wine wget mingw-w64`, o `brew install wine wget mingw-w64`, según corresponda.

**Entonces ejecuta la construcción:**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo anular XC_HOST = i686-w64-mingw32 >> Make.user`
4. `hacer`
5. `make win-extras` (Necesario antes de ejecutar `make binary-dist`)
6. `make binary-dist` luego `make exe` para crear el instalador de Windows.
7. mueve el instalador `julia-*.exe` a la máquina de destino

Si estás construyendo para Windows de 64 bits, los pasos son esencialmente los mismos. Simplemente reemplaza `i686` en `XC_HOST` con `x86_64`. (Nota: en Mac, wine solo se ejecuta en modo de 32 bits).

## Debugging a cross-compiled build under wine

La forma más efectiva de depurar una versión cruzada de Julia en el host de compilación cruzada es instalar una versión de GDB para Windows y ejecutarla bajo wine como de costumbre. Los paquetes precompilados disponibles [as part of the MSYS2 project](https://packages.msys2.org/) son conocidos por funcionar. Aparte del paquete GDB, también puede necesitar los paquetes de python y termcap. Finalmente, el aviso de GDB puede no funcionar cuando se lanza desde la línea de comandos. Esto se puede solucionar anteponiendo `wineconsole` a la invocación regular de GDB.

## After compiling

Compilar usando una de las opciones anteriores crea una compilación básica de Julia, pero no algunos componentes adicionales que se incluyen si ejecutas el instalador binario completo de Julia. Si necesitas estos componentes, la forma más fácil de obtenerlos es construir el instalador tú mismo usando `make win-extras` seguido de `make binary-dist` y `make exe`. Luego ejecuta el instalador resultante.

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * Ejecuta GDB en la consola de Windows (cmd) en su lugar. GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html) bajo mintty con aplicaciones que no son de Cygwin. Puedes usar `cmd /c start` para iniciar la consola de Windows desde mintty si es necesario.

### GDB not attaching to the right process

  * Utiliza el PID del administrador de tareas de Windows o `WINPID` del comando `ps` en lugar del PID de herramientas de línea de comandos de estilo unix (por ejemplo, `pgrep`). Es posible que necesites agregar la columna PID si no se muestra por defecto en el administrador de tareas de Windows.

### GDB not showing the right backtrace

  * Al adjuntarse al proceso de julia, GDB puede no estar adjuntándose al hilo correcto. Utilice el comando `info threads` para mostrar todos los hilos y `thread <threadno>` para cambiar de hilo.
  * Asegúrate de usar una versión de 32 bits de GDB para depurar una compilación de 32 bits de Julia, o una versión de 64 bits de GDB para depurar una compilación de 64 bits de Julia.

### Build process is slow/eats memory/hangs my computer

  * Disable the Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) and [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx) services, as they are known to have [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html) with MinGW/Cygwin.

    Como se menciona en el enlace anterior: el uso excesivo de memoria por `svchost` específicamente puede ser investigado en el Administrador de tareas haciendo clic en el proceso `svchost.exe` de alta memoria y seleccionando `Ir a servicios`. Desactive los servicios secundarios uno por uno hasta encontrar al culpable.
  * Cuidado con [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda). La herramienta [vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) es indispensable para identificar tales conflictos de software. Usa vmmap para inspeccionar la lista de DLLs cargadas para bash, mintty, o otro proceso persistente utilizado para impulsar la construcción. Esencialmente, *cualquier* DLL fuera del directorio del sistema de Windows es un potencial BLODA.

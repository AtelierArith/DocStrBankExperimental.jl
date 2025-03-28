# Binary distributions

Estas notas son para aquellos que deseen compilar una distribución binaria de Julia para su distribución en varias plataformas. Nos encanta que los usuarios difundan Julia tanto como puedan, probándola en la mayor variedad posible de sistemas operativos y configuraciones de hardware. Dado que cada plataforma tiene peculiaridades y procesos específicos que deben seguirse para crear una distribución de Julia portátil y funcional, hemos separado la mayoría de las notas por sistema operativo.

Tenga en cuenta que, aunque el código para Julia es [MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md), la distribución creada por las técnicas descritas aquí estará licenciada bajo GPL, ya que varias bibliotecas dependientes como `SuiteSparse` están licenciadas bajo GPL. Esperamos tener una distribución de Julia que no sea GPL en el futuro.

## Versioning and Git

El Makefile utiliza tanto el archivo `VERSION` como los hashes de commit y etiquetas del repositorio git para generar el `base/version_git.jl` con información que usamos para llenar la pantalla de inicio y la salida de `versioninfo()`. Si por alguna razón no deseas tener el repositorio git disponible al construir, deberías pregenerar el archivo `base/version_git.jl` con:

```
make -C base version_git.jl.phony
```

Julia tiene muchas dependencias de construcción donde usamos versiones parcheadas que aún no han sido incluidas por los gestores de paquetes populares. Estas dependencias generalmente se descargarán automáticamente cuando construyas, pero si deseas poder construir Julia en una computadora sin acceso a internet, deberías crear un archivo de distribución de código fuente completo con el objetivo de make especial.

```
make full-source-dist
```

que crea un archivo julia-version-commit.tar.gz con todas las dependencias requeridas.

Al compilar una versión etiquetada en el repositorio de git, no mostramos la información de la rama/hash de commit en la pantalla de inicio. Puedes usar esta línea para mostrar una descripción de la versión de hasta 45 caracteres. Para establecer esta línea, debes crear un archivo Make.user que contenga:

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

Por defecto, Julia optimiza su imagen del sistema para la arquitectura nativa de la máquina de construcción. Esto generalmente no es lo que deseas al construir paquetes, ya que hará que Julia falle al iniciar en cualquier máquina con CPUs incompatibles (en particular, las más antiguas con conjuntos de instrucciones más restringidos).

Por lo tanto, recomendamos que pases la variable `MARCH` al llamar a `make`, configurándola al objetivo base que pretendes soportar. Esto determinará la CPU objetivo tanto para el ejecutable de Julia como para las bibliotecas, y la imagen del sistema (esta última también se puede establecer utilizando [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)). Los valores típicamente útiles para CPUs x86 son `x86-64` y `core2` (para compilaciones de 64 bits) y `pentium4` (para compilaciones de 32 bits). Desafortunadamente, las CPUs anteriores a Pentium 4 no son compatibles actualmente (ver [this issue](https://github.com/JuliaLang/julia/issues/7185)).

La lista completa de objetivos de CPU compatibles con LLVM se puede obtener ejecutando `llc -mattr=help`.

## Linux

En Linux, `make binary-dist` crea un tarball que contiene una instalación de Julia completamente funcional. Si deseas crear un paquete de distribución como un `.deb` o `.rpm`, se necesita un esfuerzo adicional. Consulta el repositorio [julia-debian](https://github.com/staticfloat/julia-debian) para un ejemplo de qué metadatos se necesitan para crear paquetes `.deb` para sistemas basados en Debian y Ubuntu. Consulta el [Fedora package](https://src.fedoraproject.org/rpms/julia) para distribuciones basadas en RPM. Aunque aún no hemos experimentado con ello, [Alien](https://wiki.debian.org/Alien) podría usarse para generar paquetes de Julia para varias distribuciones de Linux.

Julia admite la sobrescritura de los directorios de instalación estándar a través de `prefix` y otras variables de entorno que puedes pasar al llamar a `make` y `make install`. Consulta Make.inc para su lista. `DESTDIR` también se puede usar para forzar la instalación en un directorio temporal.

Por defecto, Julia carga `$prefix/etc/julia/startup.jl` como un archivo de inicialización a nivel de instalación. Este archivo puede ser utilizado por los administradores de distribución para configurar rutas personalizadas o código de inicialización. Para los paquetes de distribución de Linux, si `$prefix` está configurado como `/usr`, no hay un `/usr/etc` en el que buscar. Esto requiere que la ruta al directorio privado `etc` de Julia sea cambiada. Esto se puede hacer a través de la variable de make `sysconfdir` al compilar. Simplemente pasa `sysconfdir=/etc` a `make` al compilar y Julia primero verificará `/etc/julia/startup.jl` antes de intentar `$prefix/etc/julia/startup.jl`.

## OS X

Para crear una distribución binaria en OSX, primero compila Julia, luego navega a `contrib/mac/app`, y ejecuta `make` con las mismas variables de make que se utilizaron con `make` al compilar Julia propiamente. Esto creará un archivo `.dmg` en el directorio `contrib/mac/app` que contiene una Julia.app completamente autónoma.

Alternativamente, Julia puede ser construida como un marco invocando `make` con el objetivo `darwinframework` y estableciendo `DARWIN_FRAMEWORK=1`. Por ejemplo, `make DARWIN_FRAMEWORK=1 darwinframework`.

## Windows

Instrucciones para crear una distribución de Julia en Windows se describen en el [build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md).

## Notes on BLAS and LAPACK

Julia construye OpenBLAS por defecto, que incluye las bibliotecas BLAS y LAPACK. En arquitecturas de 32 bits, Julia construye OpenBLAS para usar enteros de 32 bits, mientras que en arquitecturas de 64 bits, Julia construye OpenBLAS para usar enteros de 64 bits (ILP64). Es esencial que todas las funciones de Julia que llaman a las rutinas de la API de BLAS y LAPACK utilicen enteros del ancho correcto.

La mayoría de las distribuciones de BLAS y LAPACK proporcionadas en distribuciones de linux, e incluso implementaciones comerciales, envían bibliotecas que utilizan APIs de 32 bits. En muchos casos, se proporciona una API de 64 bits como una biblioteca separada.

Al utilizar bibliotecas proporcionadas por el proveedor o por el sistema operativo, hay una opción de `make` llamada `USE_BLAS64` que está disponible como parte de la construcción de Julia. Al ejecutar `make USE_BLAS64=0`, Julia llamará a BLAS y LAPACK asumiendo una API de 32 bits, donde todos los enteros son de 32 bits de ancho, incluso en una arquitectura de 64 bits.

Otras bibliotecas que utiliza Julia, como SuiteSparse, también utilizan BLAS y LAPACK internamente. Las API deben ser consistentes en todas las bibliotecas que dependen de BLAS y LAPACK. El proceso de construcción de Julia construirá todas estas bibliotecas correctamente, pero al anular los valores predeterminados y utilizar bibliotecas proporcionadas por el sistema, se debe garantizar esta consistencia.

También tenga en cuenta que las distribuciones de Linux a veces incluyen varias versiones de OpenBLAS, algunas de las cuales habilitan el multihilo, y otras solo funcionan de manera serial. Por ejemplo, en Fedora, `libopenblasp.so` es multihilo, pero `libopenblas.so` no lo es. Recomendamos usar la primera para un rendimiento óptimo. Para elegir una biblioteca OpenBLAS cuyo nombre sea diferente del predeterminado `libopenblas.so`, pase `LIBBLAS=-l$(YOURBLAS)` y `LIBBLASNAME=lib$(YOURBLAS)` a `make`, reemplazando `$(YOURBLAS)` con el nombre de su biblioteca. También puede agregar `.so.0` al nombre de la biblioteca si desea que su paquete funcione sin requerir el enlace simbólico `.so` sin versión.

Finalmente, OpenBLAS incluye su propia versión optimizada de LAPACK. Si estableces `USE_SYSTEM_BLAS=1` y `USE_SYSTEM_LAPACK=1`, también deberías establecer `LIBLAPACK=-l$(YOURBLAS)` y `LIBLAPACKNAME=lib$(YOURBLAS)`. De lo contrario, se utilizará la LAPACK de referencia y el rendimiento será típicamente mucho más bajo.

A partir de Julia 1.7, Julia utiliza [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline) para elegir un BLAS diferente en tiempo de ejecución.

# Point releasing 101

Crear una versión de punto/parche consiste en varios pasos distintos.

## Backporting commits

Algunas solicitudes de extracción están etiquetadas como "backport pending x.y", por ejemplo, "backport pending 0.6". Esto designa que la próxima versión subsiguiente etiquetada desde la rama release-x.y debería incluir el(los) commit(s) en esa solicitud de extracción. Una vez que la solicitud de extracción se fusiona en master, cada uno de los commits debería ser [cherry picked](https://git-scm.com/docs/git-cherry-pick) a una rama dedicada que, en última instancia, se fusionará en release-x.y.

### Creating a backports branch

Primero, crea una nueva rama basada en release-x.y. La convención típica para las ramas de Julia es prefijar el nombre de la rama con tus iniciales si se trata de una rama personal. A modo de ejemplo, diremos que la autora de la rama es Jane Smith.

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

Esto asegura que tu copia local de release-x.y esté actualizada con origin antes de que crees una nueva rama a partir de ella.

### Cherry picking commits

Ahora hacemos el retroceso real. Encuentra todas las solicitudes de extracción fusionadas etiquetadas como "retroceso pendiente x.y" en la interfaz web de GitHub. Para cada una de estas, desplázate hasta la parte inferior donde dice "someperson fusionó el commit `123abc` en `master` hace XX minutos". Ten en cuenta que el nombre del commit es un enlace; si haces clic en él, se te mostrarán los contenidos del commit. Si esta página muestra que `123abc` es un commit de fusión, regresa a la página de la PR; no queremos commits de fusión, queremos los commits reales. Sin embargo, si esto no muestra un commit de fusión, significa que la PR fue fusionada por squash. En ese caso, utiliza el SHA de git del commit, que se encuentra al lado del commit en esta página.

Una vez que tengas el SHA del commit, haz un cherry-pick en la rama de retroceso:

```
git cherry-pick -x -e <sha>
```

Puede haber conflictos que necesiten ser resueltos manualmente. Una vez que los conflictos se resuelvan (si corresponde), agrega una referencia a la solicitud de extracción de GitHub que introdujo el commit en el cuerpo del mensaje del commit.

Después de que todos los commits relevantes estén en la rama de backports, empuja la rama a GitHub.

## Checking for performance regressions

Las versiones puntuales nunca deben introducir regresiones de rendimiento. Afortunadamente, el bot de benchmarking de Julia, Nanosoldier, puede ejecutar benchmarks contra cualquier rama, no solo contra master. En este caso, queremos verificar los resultados de los benchmarks de js/backport-x.y contra release-x.y. Para hacer esto, despierta al Nanosoldier de su letargo robótico utilizando un comentario en tu solicitud de extracción de retroceso:

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

Esto ejecutará todos los puntos de referencia registrados en release-x.y y js/backport-x.y y producirá un resumen de los resultados, marcando todas las mejoras y regresiones.

Si Nanosoldier encuentra alguna regresión, intenta verificar localmente y vuelve a ejecutar Nanosoldier si es necesario. Si las regresiones se consideran reales en lugar de ser solo ruido, tendrás que encontrar un commit en master para retroceder que lo solucione si existe uno; de lo contrario, deberías determinar qué causó la regresión y enviar un parche (o conseguir que alguien que conozca el código envíe un parche) a master, luego retroceder el commit una vez que se haya fusionado. (O enviar un parche directamente a la rama de retroceso si es apropiado.)

## Building test binaries

Después de que la PR de retroceso se haya fusionado en la rama `release-x.y`, actualiza tu clon local de Julia, luego obtén el SHA de la rama usando

```
git rev-parse origin/release-x.y
```

Mantén eso a la mano, ya que es lo que ingresarás en el campo "Revisión" en la interfaz de usuario de buildbot.

Por ahora, todo lo que necesitas son binarios para Linux x86-64, ya que esto es lo que se utiliza para ejecutar PackageEvaluator. Ve a https://buildog.julialang.org, envía un trabajo para `nuke_linux64`, luego programa un trabajo para `package_linux64`, proporcionando el SHA como la revisión. Cuando el trabajo de empaquetado se complete, subirá el binario al bucket `julialang2` en AWS. Recupera la URL, ya que se utilizará para PackageEvaluator.

## Checking for package breakages

Las versiones puntuales nunca deberían romper paquetes, con la posible excepción de paquetes que estén haciendo algunos trucos seriamente cuestionables utilizando internals de Base que no están destinados a ser visibles para el usuario. (En esos casos, tal vez deberías hablar con el autor del paquete.)

Comprobar si los cambios realizados en la próxima nueva versión romperán paquetes se puede lograr utilizando [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl), a menudo llamado "PkgEval" para abreviar. PkgEval es lo que llena los distintivos de estado en los repositorios de GitHub y en pkg.julialang.org. Normalmente se ejecuta en uno de los nodos no de referencia de Nanosoldier y utiliza Vagrant para realizar sus tareas en máquinas virtuales VirtualBox separadas y en paralelo.

### Setting up PackageEvaluator

Clona PackageEvaluator y crea una rama llamada `backport-x.y.z`, y haz checkout de ella. Ten en cuenta que los cambios requeridos son un poco complicados y confusos, y con suerte eso se abordará en una futura versión de PackageEvaluator. Los cambios a realizar se modelarán a partir de [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016).

El script de configuración toma su primer argumento como la versión de Julia a ejecutar y el segundo como el rango de nombres de paquetes (AK para paquetes nombrados de A a K, LZ para L-Z). La idea básica es que vamos a ajustar eso un poco para ejecutar solo dos versiones de Julia, la versión actual x.y y nuestra versión de retroceso, cada una con tres rangos de paquetes.

En el diff vinculado, estamos diciendo que si el segundo argumento es LZ, use los binarios construidos a partir de nuestra rama de retroceso, de lo contrario (AK) use los binarios de lanzamiento. Luego estamos usando el primer argumento para ejecutar una sección de la lista de paquetes: A-F para la entrada 0.4, G-N para 0.5 y O-Z para 0.6.

### Running PackageEvaluator

Para ejecutar PkgEval, encuentra una máquina lo suficientemente potente (como el nodo 1 de Nanosoldier), luego ejecuta

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

Esto produce algunas carpetas en el directorio scripts/. Los nombres de las carpetas y su contenido se decodifican a continuación:

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

Una vez que eso esté hecho, puedes usar `./summary.sh` desde ese mismo directorio para producir un informe resumen de los hallazgos. Lo haremos para cada una de las carpetas para agregar los resultados generales por versión.

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

Ahora tenemos dos archivos, `summary_release.txt` y `summary_backport.txt`, que contienen los resultados de las pruebas de PackageEvaluator (aprobado/fallido) para cada paquete de las dos versiones.

Para facilitar la ingestión de estos archivos en Julia, los convertiremos en archivos CSV y luego utilizaremos el paquete DataFrames para procesar los resultados. Para convertir a CSV, copia cada archivo .txt a un archivo .csv correspondiente, luego entra en Vim y ejecuta `ggVGI"<esc>` y luego `:%s/\.json /",/g`. (No tienes que usar Vim; esta es solo una forma de hacerlo). Ahora procesa los resultados con un código de Julia similar al siguiente.

```julia
using DataFrames

release = readtable("summary_release.csv", header=false, names=[:package, :release])
backport = readtable("summary_backport.csv", header=false, names=[:package, :backport])

results = join(release, backport, on=:package, kind=:outer)

for result in eachrow(results)
    a = result[:release]
    b = result[:backport]
    if (isna(a) && !isna(b)) || (isna(b) && !isna(a))
        color = :yellow
    elseif a != b && occursin("pass", b)
        color = :green
    elseif a != b
        color = :red
    else
        continue
    end
    printstyled(result[:package], ": Release ", a, " -> Backport ", b, "\n", color=color)
end
```

Esto escribirá líneas codificadas por color en `stdout`. Todas las líneas en rojo deben ser investigadas ya que significan posibles fallos causados por la versión de retroceso. Las líneas en amarillo deben ser revisadas ya que significa que un paquete se ejecutó en una versión pero no en la otra por alguna razón. Si encuentras que tu rama de retroceso está causando fallos, utiliza `git bisect` para identificar los commits problemáticos, `git revert` esos commits y repite el proceso.

## Merging backports into the release branch

Después de que hayas asegurado que

  * los commits retroportados pasan todas las pruebas unitarias de Julia,
  * no hay regresiones de rendimiento introducidas por los commits retroportados en comparación con la rama de lanzamiento, y
  * los commits retroportados no rompen ningún paquete registrado,

entonces la rama de backport está lista para ser fusionada en release-x.y. Una vez que se haya fusionado, revisa y elimina la etiqueta "backport pending x.y" de todas las solicitudes de extracción que contengan los commits que han sido retroportados. No elimines la etiqueta de las PR que no han sido retroportadas.

La rama release-x.y ahora debería contener todos los nuevos commits. Lo último que queremos hacer en la rama es ajustar el número de versión. Para hacer esto, envía un PR contra release-x.y que edite el archivo VERSION para eliminar `-pre` del número de versión. Una vez que eso se haya fusionado, estaremos listos para etiquetar.

## Tagging the release

¡Es hora! Revisa la rama release-x.y y asegúrate de que tu copia local de la rama esté actualizada con la rama remota. En la línea de comandos, ejecuta

```
git tag v$(cat VERSION)
git push --tags
```

Esto crea la etiqueta localmente y la envía a GitHub.

Después de etiquetar la versión, envía otra PR a release-x.y para aumentar el número de parche y agregar `-pre` de nuevo al final. Esto indica que el estado de la rama refleja una versión de prerelease de la próxima versión menor en la serie x.y.

Sigue las instrucciones restantes en el Makefile.

## Signing binaries

Algunos de estos pasos requerirán contraseñas seguras. Para obtener las contraseñas apropiadas, contacta a Elliot Saba (staticfloat) o Alex Arslan (ararslan). Ten en cuenta que la firma de código para cada plataforma debe realizarse en esa plataforma (por ejemplo, la firma en Windows debe hacerse en Windows, etc.).

### Linux

La firma de código debe hacerse manualmente en Linux, pero es bastante simple. Primero, obtén el archivo `julia.key` de la carpeta CodeSigning en el bucket de AWS `juliasecure`. Agrega esto a tu llavero de GnuPG usando

```
gpg --import julia.key
```

Esto requerirá ingresar una contraseña que debes obtener de Elliot o Alex. A continuación, establece el nivel de confianza para la clave al máximo. Comienza ingresando una sesión de `gpg`:

```
gpg --edit-key julia
```

En el aviso, escribe `trust`, luego cuando se te pida un nivel de confianza, proporciona el máximo disponible (probablemente 5). Sal de GnuPG.

Ahora, para cada uno de los tarballs de Linux que fueron construidos en los buildbots, ingresa

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

Esto producirá un archivo .asc correspondiente para cada tarball. ¡Y eso es todo!

### macOS

La firma del código debería ocurrir automáticamente en los buildbots de macOS. Sin embargo, es importante verificar que fue exitosa. En un sistema o máquina virtual que ejecute macOS, descarga el archivo .dmg que fue construido en los buildbots. A modo de ejemplo, digamos que el archivo .dmg se llama `julia-x.y.z-osx.dmg`. Ejecuta

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

¡Asegúrate de anotar el nombre del disco montado que se muestra al montar! A modo de ejemplo, asumiremos que este es `disk3`. Si la verificación de firma de código se completó con éxito, no habrá salida del paso `codesign`. Si fue realmente exitoso, puedes desmontar el .dmg ahora:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

Si recibes un mensaje como

> Julia-x.y.app: el objeto de código no está firmado en absoluto


entonces necesitarás firmar manualmente.

Para firmar manualmente, primero recupera los certificados de OS X de la carpeta CodeSigning en el bucket `juliasecure` en AWS. Agrega el archivo .p12 a tu llavero usando Keychain.app. Pregunta a Elliot Saba (staticfloat) o Alex Arslan (ararslan) por la contraseña de la clave. Ahora ejecuta

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

Esto puede fallar con un mensaje como

> Julia-x.y.app: no se permite el recurso fork, información del Finder o desechos similares


Si ese es el caso, necesitarás eliminar atributos extraneous:

```
xattr -cr jlmnt/Julia-x.y.app
```

Luego vuelve a intentar la firma del código. Si eso no produce errores, vuelve a intentar la verificación. Si todo está bien ahora, desmonta el .dmg escribible y conviértelo de nuevo a solo lectura:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

Verifica que el .dmg resultante esté efectivamente corregido haciendo doble clic en él. Si todo se ve bien, expúlsalo y luego elimina el sufijo `_fixed` del nombre. ¡Y eso es todo!

### Windows

La firma debe realizarse manualmente en Windows. Primero, obtén el SDK de Windows 10, que contiene las utilidades de firma necesarias, desde el sitio web de Microsoft. Necesitamos la utilidad `SignTool`, que debería haberse instalado en algún lugar como `C:\Program Files (x86)\Windows Kits\10\App Certification Kit`. Obtén los archivos de certificado de Windows de CodeSigning en `juliasecure` y colócalos en el mismo directorio que los ejecutables. Abre una ventana de CMD de Windows, `cd` a donde están todos los archivos y ejecuta

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

Tenga en cuenta que `^` es un carácter de continuación de línea en Windows CMD y `PASSWORD` es un marcador de posición para la contraseña de este certificado. Como de costumbre, contacte a Elliot o Alex para obtener contraseñas. Si no hay errores, ¡todo está bien!

## Uploading binaries

Ahora que todo está firmado, necesitamos subir los binarios a AWS. Puedes usar un programa como Cyberduck o la utilidad de línea de comandos `aws`. Los binarios deben ir en el bucket `julialang2` en las carpetas apropiadas. Por ejemplo, Linux x86-64 va en `julialang2/bin/linux/x.y`. Asegúrate de eliminar el archivo actual `julia-x.y-latest-linux-<arch>.tar.gz` y reemplazarlo con un duplicado de `julia-x.y.z-linux-<arch>.tar.gz`.

También necesitamos subir los checksums de todo lo que hemos construido, incluidos los tarballs de origen y todos los binarios de lanzamiento. Esto es simple:

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

Tenga en cuenta que si está ejecutando esos comandos en macOS, obtendrá una salida ligeramente diferente, que se puede reformatear al mirar un archivo existente. Los usuarios de Mac también necesitarán usar `md5 -r` en lugar de `md5sum`. Cargue los archivos .md5 y .sha256 en `julialang2/bin/checksums` en AWS.

Asegúrate de que los permisos en AWS para todos los archivos subidos estén configurados como "Todos: LEER."

Para cada archivo que hemos subido, necesitamos purgar la caché de Fastly para que los enlaces en el sitio web apunten a los archivos actualizados. Como ejemplo:

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

A veces esto no es necesario, pero es bueno hacerlo de todos modos.

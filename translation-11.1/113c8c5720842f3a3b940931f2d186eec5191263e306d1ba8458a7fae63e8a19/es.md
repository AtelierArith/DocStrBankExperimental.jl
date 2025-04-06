# [Package Images](@id pkgimages)

El paquete de Julia `images` proporciona cachés de objetos (código nativo) para paquetes de Julia. Son similares a [system image](@ref dev-sysimg) de Julia y admiten muchas de las mismas características. De hecho, el formato de serialización subyacente es el mismo, y la imagen del sistema es la imagen base contra la cual se construyen las imágenes de los paquetes.

## High-level overview

Las imágenes de paquetes son bibliotecas compartidas que contienen tanto código como datos. Al igual que los archivos de caché `.ji`, se generan por paquete. La sección de datos contiene tanto datos globales (variables globales en el paquete) como los metadatos necesarios sobre qué métodos y tipos están definidos por el paquete. La sección de código contiene objetos nativos que almacenan la salida final del compilador basado en LLVM de Julia.

La opción de línea de comandos `--pkgimages=no` se puede usar para desactivar la caché de objetos para esta sesión. Tenga en cuenta que esto significa que los archivos de caché probablemente tendrán que regenerarse. Consulte [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES) para el límite superior de variantes que Julia almacena en caché por defecto.

!!! note
    Mientras que las imágenes del paquete se presentan como bibliotecas compartidas nativas, en realidad son solo una aproximación de ello. No podrás enlazarlas desde un programa nativo y deben ser cargadas desde Julia.


## Linking

Dado que las imágenes del paquete contienen código nativo, debemos ejecutar un enlazador sobre ellas antes de poder usarlas. Puedes establecer la variable de entorno [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING) en `true` para hacer que el proceso de enlace de imágenes del paquete sea detallado.

Además, no podemos asumir que el usuario tiene un enlazador de sistema funcional instalado. Por lo tanto, Julia se envía con LLD, el enlazador de LLVM, para proporcionar una experiencia lista para usar. En `base/linking.jl`, implementamos una interfaz limitada para poder enlazar imágenes de paquetes en todas las plataformas compatibles.

### Quirks

A pesar de que LLD es un enlazador multiplataforma, no proporciona una interfaz consistente entre plataformas. Además, está destinado a ser utilizado desde `clang` u otro controlador de compilador, por lo que reimplementamos parte de la lógica de `llvm-project/clang/lib/Driver/ToolChains`. Afortunadamente, se puede usar `lld -flavor` para configurar lld en la plataforma correcta.

#### Windows

Para evitar tener que lidiar con `link.exe`, usamos `-flavor gnu`, convirtiendo efectivamente `lld` en un enlazador cruzado desde un entorno mingw32. Las DLL de Windows deben contener una función `_DllMainCRTStartup` y para minimizar nuestra dependencia de las bibliotecas mingw32, inyectamos una definición de stub nosotros mismos.

#### MacOS

Las bibliotecas dinámicas en macOS necesitan enlazarse con `-lSystem`. En las versiones recientes de macOS, `-lSystem` solo está disponible para enlazarse cuando Xcode está disponible. Con ese fin, enlazamos con `-undefined dynamic_lookup`.

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

Similar a [multi-versioning](@ref sysimg-multi-versioning) para imágenes del sistema, las imágenes de paquetes admiten múltiples versiones. Si te encuentras en un entorno heterogéneo, con una caché unificada, puedes establecer la variable de entorno `JULIA_CPU_TARGET=generic` para tener múltiples versiones de las cachés de objetos.

## Flags that impact package image creation and selection

Estos son los flags de línea de comandos de Julia que impactan en la selección de caché. Las imágenes de paquetes que se crearon con diferentes flags serán rechazadas.

  * `-g`, `--debug-info`: Se requiere una coincidencia exacta ya que cambia la generación de código.
  * `--check-bounds`: Se requiere una coincidencia exacta ya que cambia la generación de código.
  * `--inline`: Coincidencia exacta requerida ya que cambia la generación de código.
  * `--pkgimages`: Para permitir la ejecución sin la caché de objetos habilitada.
  * `-O`, `--optimize`: Rechazar imágenes de paquetes generadas para un nivel de optimización inferior, pero permitir que se carguen niveles de optimización superiores.

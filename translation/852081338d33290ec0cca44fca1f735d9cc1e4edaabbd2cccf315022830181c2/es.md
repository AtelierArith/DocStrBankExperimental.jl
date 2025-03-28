# [Installation](@id man-installation)

Hay muchas maneras de instalar Julia. Las siguientes secciones destacan el método recomendado para cada una de las principales plataformas soportadas y luego presentan formas alternativas que podrían ser útiles en situaciones especializadas.

La recomendación actual de instalación es una solución basada en Juliaup. Si instalaste Julia anteriormente con un método que *no* se basa en Juliaup y deseas cambiar tu sistema a una instalación que se base en Juliaup, te recomendamos que desinstales todas las versiones anteriores de Julia, asegúrate de eliminar cualquier cosa relacionada con Julia de tu variable `PATH` y luego instala Julia con uno de los métodos descritos a continuación.

## Windows

En Windows, Julia se puede instalar directamente desde la tienda de Windows [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN). También se puede instalar exactamente la misma versión ejecutando

```
winget install julia -s msstore
```

en cualquier shell.

## Mac and Linux

Julia se puede instalar en Linux o Mac ejecutando

```
curl -fsSL https://install.julialang.org | sh
```

en un shell.

### Command line arguments

Se pueden pasar varios argumentos de línea de comandos al instalador de Julia. La sintaxis para los argumentos del instalador es

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

Aquí `<ARGS>` debe ser reemplazado por uno o más de los siguientes argumentos:

  * `--yes` (o `-y`): Ejecuta el instalador en modo no interactivo. Todos los valores de configuración utilizan su valor predeterminado o un valor proporcionado como argumento de línea de comandos.
  * `--default-channel=<NOMBRE>`: Configura el canal predeterminado de Juliaup. Por ejemplo, `--default-channel lts` instalaría el canal `lts` y lo configuraría como el predeterminado.
  * `--add-to-path=<sí|no>`: Configura si Julia debe ser añadida a la variable de entorno `PATH`. Los valores válidos son `sí` (predeterminado) y `no`.
  * `--background-selfupdate=<SECONDS>`: Configura un trabajo CRON opcional que actualiza automáticamente Juliaup si `<SECONDS>` tiene un valor mayor que 0. El valor real controla con qué frecuencia se ejecutará el trabajo CRON para verificar si hay una nueva versión de Juliaup en segundos. El valor predeterminado es 0, es decir, no se creará ningún trabajo CRON.
  * `--startup-selfupdate=<MINUTOS>`: Configura con qué frecuencia Julia buscará nuevas versiones de Juliaup cuando se inicie Julia. El valor predeterminado es cada 1440 minutos.
  * `-p=<RUTA>` (o `--path`): Configura dónde se instalan los binarios de Julia y Juliaup. El valor predeterminado es `~/.juliaup`.

## Alternative installation methods

Tenga en cuenta que recomendamos los siguientes métodos *solo* si ninguno de los métodos de instalación descritos anteriormente funciona para su sistema.

Algunos de los métodos de instalación descritos a continuación recomiendan instalar un paquete llamado `juliaup`. Tenga en cuenta que, sin embargo, esto instala un sistema Julia completamente funcional, no solo Juliaup.

### App Installer (Windows)

Si la Tienda de Windows está bloqueada en un sistema, tenemos una alternativa [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) basada en la configuración. Para usar la versión del Instalador de Aplicaciones, descarga el archivo [this](https://install.julialang.org/Julia.appinstaller) y ábrelo haciendo doble clic en él.

### MSI Installer (Windows)

Si ni la tienda de Windows ni la versión del instalador de aplicaciones funcionan en tu sistema Windows, también puedes usar un instalador basado en MSI. Ten en cuenta que este método de instalación tiene serias limitaciones y generalmente no se recomienda a menos que no funcione ningún otro método. Por ejemplo, no hay un mecanismo de actualización automática para Juliaup con este método de instalación. La versión de 64 bits del instalador MSI se puede descargar desde [here](https://install.julialang.org/Julia-x64.msi) y la versión de 32 bits desde [here](https://install.julialang.org/Julia-x86.msi).

Por defecto, la instalación será una instalación por usuario que no requiere elevación. También puedes hacer una instalación del sistema ejecutando el siguiente comando desde una terminal:

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

En sistemas con brew, puedes instalar Julia ejecutando

```
brew install juliaup
```

en un shell. Ten en cuenta que tendrás que actualizar Juliaup con los comandos estándar de brew.

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

En Arch Linux, Juliaup está disponible [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/).

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

En openSUSE Tumbleweed, puedes instalar Julia ejecutando

```sh
zypper install juliaup
```

en un shell con privilegios de root.

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

Para instalar Julia a través de cargo de Rust, ejecuta:

```sh
cargo install juliaup
```

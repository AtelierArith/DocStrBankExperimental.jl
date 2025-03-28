Nivel de prioridad de un archivo de configuración.

Estos niveles de prioridad corresponden a la lógica de escalación natural (de mayor a menor) al buscar entradas de configuración en git.

  * `CONFIG_LEVEL_DEFAULT` - Abre los archivos de configuración global, XDG y del sistema si están disponibles.
  * `CONFIG_LEVEL_PROGRAMDATA` - A nivel del sistema en Windows, para compatibilidad con git portátil.
  * `CONFIG_LEVEL_SYSTEM` - Archivo de configuración a nivel del sistema; `/etc/gitconfig` en sistemas Linux.
  * `CONFIG_LEVEL_XDG` - Archivo de configuración compatible con XDG; típicamente `~/.config/git/config`.
  * `CONFIG_LEVEL_GLOBAL` - Archivo de configuración específico del usuario (también llamado archivo de configuración global); típicamente `~/.gitconfig`.
  * `CONFIG_LEVEL_LOCAL` - Archivo de configuración específico del repositorio; `$WORK_DIR/.git/config` en repositorios no bare.
  * `CONFIG_LEVEL_APP` - Archivo de configuración específico de la aplicación; definido libremente por las aplicaciones.
  * `CONFIG_HIGHEST_LEVEL` - Representa el archivo de configuración de nivel más alto disponible (es decir, el archivo de configuración más específico disponible que realmente se carga).

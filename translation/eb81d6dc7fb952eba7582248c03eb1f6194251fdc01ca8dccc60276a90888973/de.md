Prioritätsstufe einer Konfigurationsdatei.

Diese Prioritätsstufen entsprechen der natürlichen Eskalationslogik (von höher nach niedriger), wenn nach Konfigurationseinträgen in git gesucht wird.

  * `CONFIG_LEVEL_DEFAULT` - Öffnen Sie die globalen, XDG- und Systemkonfigurationsdateien, falls verfügbar.
  * `CONFIG_LEVEL_PROGRAMDATA` - Systemweit unter Windows, zur Kompatibilität mit portablem git
  * `CONFIG_LEVEL_SYSTEM` - Systemweite Konfigurationsdatei; `/etc/gitconfig` auf Linux-Systemen
  * `CONFIG_LEVEL_XDG` - XDG-kompatible Konfigurationsdatei; typischerweise `~/.config/git/config`
  * `CONFIG_LEVEL_GLOBAL` - Benutzerspezifische Konfigurationsdatei (auch als globale Konfigurationsdatei bezeichnet); typischerweise `~/.gitconfig`
  * `CONFIG_LEVEL_LOCAL` - Repository-spezifische Konfigurationsdatei; `$WORK_DIR/.git/config` in nicht-bare Repos
  * `CONFIG_LEVEL_APP` - Anwendungs-spezifische Konfigurationsdatei; frei von Anwendungen definiert
  * `CONFIG_HIGHEST_LEVEL` - Stellt die höchste verfügbare Konfigurationsdatei dar (d.h. die spezifischste Konfigurationsdatei, die tatsächlich geladen wird)

Niveau de priorité d'un fichier de configuration.

Ces niveaux de priorité correspondent à la logique d'escalade naturelle (de plus élevé à plus bas) lors de la recherche d'entrées de configuration dans git.

  * `CONFIG_LEVEL_DEFAULT` - Ouvrir les fichiers de configuration globaux, XDG et système s'ils sont disponibles.
  * `CONFIG_LEVEL_PROGRAMDATA` - Système entier sur Windows, pour la compatibilité avec git portable
  * `CONFIG_LEVEL_SYSTEM` - Fichier de configuration système ; `/etc/gitconfig` sur les systèmes Linux
  * `CONFIG_LEVEL_XDG` - Fichier de configuration compatible XDG ; typiquement `~/.config/git/config`
  * `CONFIG_LEVEL_GLOBAL` - Fichier de configuration spécifique à l'utilisateur (également appelé fichier de configuration global) ; typiquement `~/.gitconfig`
  * `CONFIG_LEVEL_LOCAL` - Fichier de configuration spécifique au dépôt ; `$WORK_DIR/.git/config` sur les dépôts non nus
  * `CONFIG_LEVEL_APP` - Fichier de configuration spécifique à l'application ; librement défini par les applications
  * `CONFIG_HIGHEST_LEVEL` - Représente le fichier de configuration disponible au niveau le plus élevé (c'est-à-dire le fichier de configuration le plus spécifique disponible qui est effectivement chargé)

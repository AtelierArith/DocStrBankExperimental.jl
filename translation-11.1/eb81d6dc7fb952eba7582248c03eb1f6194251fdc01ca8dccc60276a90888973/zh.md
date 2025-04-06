配置文件的优先级级别。

这些优先级级别对应于在 git 中搜索配置条目时的自然升级逻辑（从高到低）。

  * `CONFIG_LEVEL_DEFAULT` - 打开全局、XDG 和系统配置文件（如果有可用的话）。
  * `CONFIG_LEVEL_PROGRAMDATA` - 在 Windows 上的系统范围内，为了与便携式 git 兼容
  * `CONFIG_LEVEL_SYSTEM` - 系统范围的配置文件；在 Linux 系统上为 `/etc/gitconfig`
  * `CONFIG_LEVEL_XDG` - XDG 兼容的配置文件；通常为 `~/.config/git/config`
  * `CONFIG_LEVEL_GLOBAL` - 用户特定的配置文件（也称为全局配置文件）；通常为 `~/.gitconfig`
  * `CONFIG_LEVEL_LOCAL` - 仓库特定的配置文件；在非裸仓库中为 `$WORK_DIR/.git/config`
  * `CONFIG_LEVEL_APP` - 应用程序特定的配置文件；由应用程序自由定义
  * `CONFIG_HIGHEST_LEVEL` - 代表可用的最高级别配置文件（即实际加载的最具体的配置文件）

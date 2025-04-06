구성 파일의 우선 순위 수준.

이러한 우선 순위 수준은 git에서 구성 항목을 검색할 때 자연스러운 상승 논리(높은 것에서 낮은 것)와 일치합니다.

  * `CONFIG_LEVEL_DEFAULT` - 사용 가능한 경우 전역, XDG 및 시스템 구성 파일을 엽니다.
  * `CONFIG_LEVEL_PROGRAMDATA` - 휴대용 git과의 호환성을 위해 Windows에서 시스템 전체
  * `CONFIG_LEVEL_SYSTEM` - 시스템 전체 구성 파일; Linux 시스템의 경우 `/etc/gitconfig`
  * `CONFIG_LEVEL_XDG` - XDG 호환 구성 파일; 일반적으로 `~/.config/git/config`
  * `CONFIG_LEVEL_GLOBAL` - 사용자별 구성 파일(전역 구성 파일이라고도 함); 일반적으로 `~/.gitconfig`
  * `CONFIG_LEVEL_LOCAL` - 리포지토리 특정 구성 파일; 비베어 리포지토리의 경우 `$WORK_DIR/.git/config`
  * `CONFIG_LEVEL_APP` - 애플리케이션 특정 구성 파일; 애플리케이션에 의해 자유롭게 정의됨
  * `CONFIG_HIGHEST_LEVEL` - 사용 가능한 가장 높은 수준의 구성 파일을 나타냅니다(즉, 실제로 로드된 가장 구체적인 구성 파일)

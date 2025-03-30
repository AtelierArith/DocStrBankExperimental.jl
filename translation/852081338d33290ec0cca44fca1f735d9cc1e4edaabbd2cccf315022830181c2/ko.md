# [Installation](@id man-installation)

Julia를 설치하는 방법은 여러 가지가 있습니다. 다음 섹션에서는 각 주요 지원 플랫폼에 대한 권장 방법을 강조하고, 그 후에는 특수한 상황에서 유용할 수 있는 대체 방법을 제시합니다.

현재 설치 권장 사항은 Juliaup을 기반으로 한 솔루션입니다. 이전에 Juliaup을 기반으로 하지 않는 방법으로 Julia를 설치한 경우, 시스템을 Juliaup 기반 설치로 전환하려면 모든 이전 Julia 버전을 제거하고 `PATH` 변수에서 Julia와 관련된 모든 항목을 제거한 다음 아래에 설명된 방법 중 하나로 Julia를 설치하는 것이 좋습니다.

## Windows

Windows에서 Julia는 Windows 스토어에서 직접 설치할 수 있습니다 [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN). 동일한 버전을 실행하여 설치할 수도 있습니다.

```
winget install julia -s msstore
```

어떤 셸에서도.

## Mac and Linux

Julia는 Linux 또는 Mac에서 다음 명령어를 실행하여 설치할 수 있습니다.

```
curl -fsSL https://install.julialang.org | sh
```

쉘에서.

### Command line arguments

Julia 설치 프로그램에 다양한 명령줄 인수를 전달할 수 있습니다. 설치 프로그램 인수의 구문은

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

여기 `<ARGS>`는 다음 인수 중 하나 이상으로 대체되어야 합니다:

  * `--yes` (또는 `-y`): 설치 프로그램을 비대화식 모드로 실행합니다. 모든 구성 값은 기본값이나 명령줄 인수로 제공된 값을 사용합니다.
  * `--default-channel=<NAME>`: 기본 Juliaup 채널을 구성합니다. 예를 들어 `--default-channel lts`는 `lts` 채널을 설치하고 이를 기본으로 구성합니다.
  * `--add-to-path=<yes|no>`: Julia를 `PATH` 환경 변수에 추가할지 여부를 설정합니다. 유효한 값은 `yes`(기본값)와 `no`입니다.
  * `--background-selfupdate=<SECONDS>`: `<SECONDS>`가 0보다 큰 경우 Juliaup을 자동 업데이트하는 선택적 CRON 작업을 구성합니다. 실제 값은 CRON 작업이 새 Juliaup 버전을 확인하기 위해 얼마나 자주 실행될지를 초 단위로 제어합니다. 기본값은 0이며, 즉 CRON 작업이 생성되지 않습니다.
  * `--startup-selfupdate=<MINUTES>`: Julia가 시작될 때 Juliaup의 새 버전을 얼마나 자주 확인할지를 구성합니다. 기본값은 1440분마다입니다.
  * `-p=<PATH>` (또는 `--path`): Julia 및 Juliaup 바이너리가 설치되는 경로를 구성합니다. 기본값은 `~/.juliaup`입니다.

## Alternative installation methods

다음 방법은 위에 설명된 설치 방법이 귀하의 시스템에서 작동하지 않을 경우에만 *권장*합니다.

아래 설명된 일부 설치 방법은 `juliaup`이라는 패키지를 설치할 것을 권장합니다. 그러나 이는 단순히 Juliaup만 설치하는 것이 아니라 완전한 기능을 갖춘 Julia 시스템을 설치한다는 점에 유의하세요.

### App Installer (Windows)

시스템에서 Windows Store가 차단된 경우, 대안으로 [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) 기반의 설치 방법이 있습니다. App Installer 버전을 사용하려면 [this](https://install.julialang.org/Julia.appinstaller) 파일을 다운로드하고 더블 클릭하여 엽니다.

### MSI Installer (Windows)

Windows 스토어나 앱 설치 프로그램 버전이 Windows 시스템에서 작동하지 않는 경우, MSI 기반 설치 프로그램을 사용할 수도 있습니다. 이 설치 방법은 심각한 제한 사항이 있으며, 다른 방법이 작동하지 않을 경우에만 일반적으로 권장되지 않습니다. 예를 들어, 이 설치 방법으로는 Juliaup에 대한 자동 업데이트 메커니즘이 없습니다. 64비트 MSI 설치 프로그램은 [here](https://install.julialang.org/Julia-x64.msi)에서 다운로드할 수 있으며, 32비트 버전은 [here](https://install.julialang.org/Julia-x86.msi)에서 다운로드할 수 있습니다.

기본적으로 설치는 권한 상승이 필요 없는 사용자별 설치입니다. 다음 명령을 셸에서 실행하여 시스템 설치를 수행할 수도 있습니다:

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

brew install julia

```
brew install juliaup
```

쉘에서. 표준 brew 명령어로 Juliaup을 업데이트해야 한다는 점에 유의하세요.

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

Arch Linux에서 Juliaup은 [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/)에서 사용할 수 있습니다.

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

openSUSE Tumbleweed에서 Julia를 설치하려면 다음 명령어를 실행하세요.

```sh
zypper install juliaup
```

루트 권한이 있는 셸에서.

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

Rust의 cargo를 통해 Julia를 설치하려면 다음 명령어를 실행하세요:

```sh
cargo install juliaup
```

# [Installation](@id man-installation)

有很多方法可以安装 Julia。以下部分强调了每个主要支持平台的推荐方法，然后介绍了在特殊情况下可能有用的替代方法。

当前的安装推荐是基于 Juliaup 的解决方案。如果您之前使用非基于 Juliaup 的方法安装了 Julia，并希望将系统切换到基于 Juliaup 的安装，我们建议您卸载所有先前的 Julia 版本，确保从您的 `PATH` 变量中删除与 Julia 相关的任何内容，然后使用下面描述的其中一种方法安装 Julia。

## Windows

在Windows上，Julia可以直接从Windows商店安装 [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN)。也可以通过执行相同的命令安装完全相同的版本。

```
winget install julia -s msstore
```

在任何 shell 中。

## Mac and Linux

Julia 可以通过执行以下命令在 Linux 或 Mac 上安装

```
curl -fsSL https://install.julialang.org | sh
```

在一个外壳中。

### Command line arguments

可以向Julia安装程序传递各种命令行参数。安装程序参数的语法是

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

在这里，`<ARGS>` 应该替换为以下一个或多个参数：

  * `--yes`（或 `-y`）：以非交互模式运行安装程序。所有配置值使用默认值或作为命令行参数提供的值。
  * `--default-channel=<NAME>`：配置默认的 Juliaup 通道。例如 `--default-channel lts` 将安装 `lts` 通道并将其配置为默认通道。
  * `--add-to-path=<yes|no>`：配置是否将 Julia 添加到 `PATH` 环境变量。有效值为 `yes`（默认）和 `no`。
  * `--background-selfupdate=<SECONDS>`：配置一个可选的 CRON 任务，如果 `<SECONDS>` 的值大于 0，则自动更新 Juliaup。实际值控制 CRON 任务检查新 Juliaup 版本的频率，单位为秒。默认值为 0，即不会创建 CRON 任务。
  * `--startup-selfupdate=<MINUTES>`：配置 Julia 启动时检查 Juliaup 新版本的频率。默认值为每 1440 分钟。
  * `-p=<PATH>`（或 `--path`）：配置 Julia 和 Juliaup 二进制文件的安装位置。默认值为 `~/.juliaup`。

## Alternative installation methods

请注意，我们仅在上述安装方法对您的系统都无效的情况下推荐以下方法。

以下描述的一些安装方法建议安装一个名为 `juliaup` 的软件包。请注意，这仍然会安装一个功能齐全的 Julia 系统，而不仅仅是 Juliaup。

### App Installer (Windows)

如果系统上阻止了 Windows Store，我们有一个替代的 [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) 基于的设置。要使用 App Installer 版本，请下载 [this](https://install.julialang.org/Julia.appinstaller) 文件，并通过双击打开它。

### MSI Installer (Windows)

如果Windows Store和App Installer版本在您的Windows系统上都无法工作，您还可以使用基于MSI的安装程序。请注意，这种安装方法有严重的限制，通常不建议使用，除非没有其他方法可行。例如，使用这种安装方法，Juliaup没有自动更新机制。64位版本的MSI安装程序可以从[here](https://install.julialang.org/Julia-x64.msi)下载，32位版本可以从[here](https://install.julialang.org/Julia-x86.msi)下载。

默认情况下，安装将是一个不需要提升权限的用户安装。您也可以通过从 shell 运行以下命令来进行系统安装：

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

在使用 brew 的系统上，您可以通过运行以下命令安装 Julia：

```
brew install juliaup
```

在终端中。请注意，您需要使用标准的 brew 命令来更新 Juliaup。

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

在 Arch Linux 上，Juliaup 可用 [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/)。

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

在 openSUSE Tumbleweed 上，您可以通过运行以下命令来安装 Julia

```sh
zypper install juliaup
```

在具有根权限的 shell 中。

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

通过 Rust 的 cargo 安装 Julia，请运行：

```sh
cargo install juliaup
```

# Windows

此文件描述了如何在Windows上安装、构建和使用Julia。

有关Julia的更多一般信息，请参见 [main README](https://github.com/JuliaLang/julia/blob/master/README.md) 或 [documentation](https://docs.julialang.org)。

## General Information for Windows

我们强烈建议使用现代终端应用程序运行 Julia，特别是 Windows Terminal，可以从 [Microsoft Store](https://aka.ms/terminal) 安装。

### Line endings

Julia 仅使用二进制模式文件。与许多其他 Windows 程序不同，如果你向文件写入 `\n`，文件中将得到一个 `\n`，而不是其他位模式。这与其他操作系统的行为一致。如果你已安装 Git for Windows，建议但不强制你配置系统 Git 以使用相同的约定：

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

或编辑 `%USERPROFILE%\.gitconfig` 并添加/编辑以下行：

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

有关 Windows 上二进制分发安装说明，请参阅 [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows) 的说明。

## Source distribution

### Cygwin-to-MinGW cross-compiling

在Windows上从源代码编译Julia的推荐方法是通过从 [Cygwin](https://www.cygwin.com) 进行交叉编译，使用通过Cygwin的包管理器提供的MinGW-w64编译器版本。

1. 下载并运行 Cygwin 安装程序，链接为 [32 bit](https://cygwin.com/setup-x86.exe) 或 [64 bit](https://cygwin.com/setup-x86_64.exe)。请注意，您可以从 32 位或 64 位 Cygwin 编译 32 位或 64 位的 Julia。64 位 Cygwin 的软件包选择略小，但通常更新更及时。

    *高级*: 您可以通过运行跳过步骤 2-4：

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    将 `<url>` 替换为来自 [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) 的站点，或者先手动运行设置并选择一个镜像。
2. 选择安装位置和下载镜像。
3. 在 *选择软件包* 步骤中，选择以下内容：

    1. 来自 *Devel* 类别： `cmake`， `gcc-g++`， `git`， `make`， `patch`
    2. 来自 *Net* 类别： `curl`
    3. 来自 *解释器*（或 *Python*）类别： `m4`， `python3`
    4. 来自 *Archive* 类别： `p7zip`
    5. 对于32位Julia，以及来自*Devel*类别的：`mingw64-i686-gcc-g++`和`mingw64-i686-gcc-fortran`
    6. 对于64位Julia，以及来自*Devel*类别的：`mingw64-x86_64-gcc-g++`和`mingw64-x86_64-gcc-fortran`
4. 允许 Cygwin 安装完成，然后从已安装的快捷方式 *'Cygwin Terminal'* 或 *'Cygwin64 Terminal'* 启动。
5. 从源代码构建 Julia 及其依赖项：

    1. 获取Julia源代码

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        提示：如果您在 git 中遇到 `error: cannot fork() for fetch-pack: Resource temporarily unavailable`，请将 `alias git="env PATH=/usr/bin git"` 添加到 `~/.bashrc` 并重启 Cygwin。
    2. 在 `Make.user` 中设置 `XC_HOST` 变量以指示 MinGW-w64 交叉编译

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. 开始构建

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. 直接使用 Julia 可执行文件运行 Julia

    ```sh
    usr/bin/julia.exe
    usr/bin/julia-debug.exe
    ```

!!! note "Pro tip: build both!"
    ```sh
    make O=julia-win32 configure
    make O=julia-win64 configure
    echo 'XC_HOST = i686-w64-mingw32' > julia-win32/Make.user
    echo 'XC_HOST = x86_64-w64-mingw32' > julia-win64/Make.user
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-win32  # build for Windows x86 in julia-win32 folder
    make -C julia-win64  # build for Windows x86-64 in julia-win64 folder
    ```


### Compiling with MinGW/MSYS2

[MSYS2](https://www.msys2.org/) 是一个用于 Windows 的软件分发和构建环境。

注意：MSYS2 需要 **64 位** Windows 7 或更高版本。

1. 安装和配置 MSYS2。

    1. 下载并运行最新的安装程序，名称为 [64-bit](https://github.com/msys2/msys2-installer/releases/latest) 发行版。安装程序的名称将类似于 `msys2-x86_64-yyyymmdd.exe`。
    2. 打开 MSYS2 shell。更新软件包数据库和基础软件包：

        `pacman -Syu`
    3. 退出并重新启动 MSYS2。更新其余的基础包：

        `pacman -Syu`
    4. 然后安装构建 Julia 所需的工具：

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        对于64位Julia，请安装x86_64版本：

        `pacman -S mingw-w64-x86_64-gcc`

        对于32位Julia，请安装i686版本：

        `pacman -S mingw-w64-i686-gcc`
    5. MSYS2 的配置已完成。现在 `exit` MSYS2 shell。
2. 构建 Julia 及其依赖项，使用预构建依赖项。

    1. 打开一个新的 [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview)。目前我们无法同时使用 mingw32 和 mingw64，因此如果您想构建 x86_64 和 i686 版本，您需要在每个环境中单独构建它们。
    2. 克隆Julia源代码：

        `git clone https://github.com/JuliaLang/julia.git  cd julia`
    3. 开始构建

        `make -j$(nproc)`

!!! note "Pro tip: build in dir"
    ```sh
    make O=julia-mingw-w64 configure
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-mingw-w64
    ```


### Cross-compiling from Unix (Linux/Mac/WSL)

您还可以使用 MinGW-w64 交叉编译器从 Linux、Mac 或 Windows 子系统 for Linux (WSL) 构建 Windows 版本的 Julia。

首先，您需要确保您的系统具有所需的依赖项。我们需要 wine (>=1.7.5)、一个系统编译器和一些下载工具。注意：如果使用 WSL，Cygwin 安装可能会干扰此方法。

**在 Ubuntu 上**（在其他 Linux 系统上，依赖项名称可能类似）：

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**在 Mac 上**：安装 XCode、XCode 命令行工具、X11（现在是 [XQuartz](https://www.xquartz.org/)）和 [MacPorts](https://www.macports.org/install.php) 或 [Homebrew](https://brew.sh/)。然后运行 `port install wine wget mingw-w64`，或根据需要运行 `brew install wine wget mingw-w64`。

**然后运行构建：**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo override XC_HOST = i686-w64-mingw32 >> Make.user`
4. `制作`
5. `make win-extras`（在运行 `make binary-dist` 之前是必要的）
6. `make binary-dist` 然后 `make exe` 来创建 Windows 安装程序。
7. 将 `julia-*.exe` 安装程序移动到目标机器上

如果您正在为64位Windows构建，步骤基本相同。只需将`XC_HOST`中的`i686`替换为`x86_64`。（注意：在Mac上，wine仅在32位模式下运行）。

## Debugging a cross-compiled build under wine

在交叉编译主机上调试交叉编译版本的 Julia 最有效的方法是安装 Windows 版本的 GDB，并像往常一样在 wine 下运行。可用的预构建包 [as part of the MSYS2 project](https://packages.msys2.org/) 已知可以正常工作。除了 GDB 包外，您可能还需要 python 和 termcap 包。最后，从命令行启动 GDB 时，提示符可能无法正常工作。可以通过在常规 GDB 调用前添加 `wineconsole` 来解决此问题。

## After compiling

使用上述选项之一进行编译会创建一个基本的 Julia 构建，但不会包含运行完整的 Julia 二进制安装程序时包含的一些额外组件。如果您需要这些组件，获取它们的最简单方法是使用 `make win-extras` 构建安装程序，然后依次运行 `make binary-dist` 和 `make exe`。然后运行生成的安装程序。

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * 在 Windows 控制台 (cmd) 下运行 GDB。GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html) 在 mintty 下与非 Cygwin 应用程序一起使用。如果需要，可以使用 `cmd /c start` 从 mintty 启动 Windows 控制台。

### GDB not attaching to the right process

  * 使用 Windows 任务管理器中的 PID 或 `ps` 命令中的 `WINPID`，而不是来自类 Unix 命令行工具（例如 `pgrep`）的 PID。如果在 Windows 任务管理器中默认未显示 PID 列，您可能需要添加该列。

### GDB not showing the right backtrace

  * 当附加到 Julia 进程时，GDB 可能没有附加到正确的线程。使用 `info threads` 命令显示所有线程，并使用 `thread <threadno>` 切换线程。
  * 确保使用32位版本的GDB来调试32位构建的Julia，或使用64位版本的GDB来调试64位构建的Julia。

### Build process is slow/eats memory/hangs my computer

  * 禁用 Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) 和 [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx) 服务，因为它们已知存在 [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html) 与 MinGW/Cygwin。

    如上面链接所提到的：可以通过在任务管理器中点击高内存使用的 `svchost.exe` 进程并选择 `转到服务` 来调查 `svchost` 的过度内存使用。逐个禁用子服务，直到找到罪魁祸首。
  * 注意 [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda)。[vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) 工具对于识别此类软件冲突是不可或缺的。使用 vmmap 检查 bash、mintty 或其他用于驱动构建的持久进程加载的 DLL 列表。基本上，*任何* 在 Windows 系统目录之外的 DLL 都是潜在的 BLODA。

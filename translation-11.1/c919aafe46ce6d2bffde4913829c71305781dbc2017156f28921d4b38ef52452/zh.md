# Binary distributions

这些笔记是为那些希望编译 Julia 的二进制发行版以便在各种平台上分发的人准备的。我们欢迎用户尽可能广泛地传播 Julia，尽量在各种操作系统和硬件配置上进行尝试。由于每个平台都有特定的注意事项和必须遵循的流程，以便创建一个可移植的、可工作的 Julia 发行版，我们将大部分笔记按操作系统进行了分类。

请注意，虽然Julia的代码是[MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md)，但本文所述技术创建的发行版将是GPL许可的，因为各种依赖库如`SuiteSparse`是GPL许可的。我们确实希望在未来能够拥有一个非GPL的Julia发行版。

## Versioning and Git

Makefile 使用 `VERSION` 文件以及来自 git 仓库的提交哈希和标签来生成 `base/version_git.jl`，其中包含我们用来填充启动画面和 `versioninfo()` 输出的信息。如果由于某种原因您不想在构建时使用 git 仓库，您应该预先生成 `base/version_git.jl` 文件，方法是：

```
make -C base version_git.jl.phony
```

Julia 有很多构建依赖项，我们使用尚未被流行包管理器包含的修补版本。这些依赖项通常会在构建时自动下载，但如果您希望能够在没有互联网访问的计算机上构建 Julia，您应该使用特殊的 make 目标创建一个完整的源代码分发归档。

```
make full-source-dist
```

这将创建一个包含所有所需依赖项的 julia-version-commit.tar.gz 归档。

在 git 仓库中编译标记发布时，我们不会在启动画面中显示分支/提交哈希信息。您可以使用这一行显示最多 45 个字符的发布描述。要设置这一行，您必须创建一个 Make.user 文件，内容为：

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

默认情况下，Julia 会将其系统映像优化为构建机器的本地架构。这通常不是您在构建包时所希望的，因为这会导致 Julia 在任何具有不兼容 CPU 的机器上启动失败（特别是那些具有更受限指令集的旧机器）。

因此，我们建议您在调用 `make` 时传递 `MARCH` 变量，将其设置为您打算支持的基线目标。这将确定 Julia 可执行文件和库的目标 CPU，以及系统映像（后者也可以使用 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 设置）。对于 x86 CPU，通常有用的值是 `x86-64` 和 `core2`（用于 64 位构建）以及 `pentium4`（用于 32 位构建）。不幸的是，当前不支持比 Pentium 4 更旧的 CPU（请参见 [this issue](https://github.com/JuliaLang/julia/issues/7185)）。

可以通过运行 `llc -mattr=help` 获取 LLVM 支持的 CPU 目标的完整列表。

## Linux

在 Linux 上，`make binary-dist` 创建一个包含完整功能 Julia 安装的 tarball。如果您希望创建一个分发包，例如 `.deb` 或 `.rpm`，则需要额外的努力。请参阅 [julia-debian](https://github.com/staticfloat/julia-debian) 仓库，以获取创建适用于 Debian 和基于 Ubuntu 的系统的 `.deb` 包所需的元数据示例。有关基于 RPM 的分发版，请参阅 [Fedora package](https://src.fedoraproject.org/rpms/julia)。尽管我们尚未对此进行实验，但 [Alien](https://wiki.debian.org/Alien) 可用于为各种 Linux 发行版生成 Julia 包。

Julia 支持通过 `prefix` 和其他环境变量来覆盖标准安装目录，这些变量可以在调用 `make` 和 `make install` 时传递。请参见 Make.inc 以获取它们的列表。`DESTDIR` 也可以用于强制安装到临时目录。

默认情况下，Julia 会加载 `$prefix/etc/julia/startup.jl` 作为全局初始化文件。此文件可供发行版管理器使用，以设置自定义路径或初始化代码。对于 Linux 发行版包，如果 `$prefix` 设置为 `/usr`，则没有 `/usr/etc` 可供查找。这需要更改 Julia 私有 `etc` 目录的路径。这可以通过在构建时使用 `sysconfdir` make 变量来完成。只需在构建时将 `sysconfdir=/etc` 传递给 `make`，Julia 将首先检查 `/etc/julia/startup.jl`，然后再尝试 `$prefix/etc/julia/startup.jl`。

## OS X

要在OSX上创建二进制分发，首先构建Julia，然后切换到`contrib/mac/app`，并使用与构建Julia时相同的makevars运行`make`。这将会在`contrib/mac/app`目录中创建一个包含完全自包含的Julia.app的`.dmg`文件。

另外，可以通过使用 `make` 命令并设置 `DARWIN_FRAMEWORK=1` 来将 Julia 构建为一个框架，目标为 `darwinframework`。例如，`make DARWIN_FRAMEWORK=1 darwinframework`。

## Windows

在Windows上创建Julia分发的说明在[build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)中描述。

## Notes on BLAS and LAPACK

Julia 默认构建 OpenBLAS，其中包括 BLAS 和 LAPACK 库。在 32 位架构上，Julia 构建 OpenBLAS 以使用 32 位整数，而在 64 位架构上，Julia 构建 OpenBLAS 以使用 64 位整数（ILP64）。所有调用 BLAS 和 LAPACK API 例程的 Julia 函数使用正确宽度的整数是至关重要的。

大多数在Linux发行版中提供的BLAS和LAPACK分发版，甚至商业实现，都提供使用32位API的库。在许多情况下，64位API作为单独的库提供。

在使用供应商提供或操作系统提供的库时，Julia 构建中提供了一个名为 `USE_BLAS64` 的 `make` 选项。当执行 `make USE_BLAS64=0` 时，Julia 将调用 BLAS 和 LAPACK，假设使用的是 32 位 API，其中所有整数都是 32 位宽，即使在 64 位架构上也是如此。

其他 Julia 使用的库，例如 SuiteSparse，也在内部使用 BLAS 和 LAPACK。所有依赖于 BLAS 和 LAPACK 的库的 API 需要保持一致。Julia 的构建过程将正确构建所有这些库，但在覆盖默认设置并使用系统提供的库时，必须确保这种一致性。

还要注意，Linux 发行版有时会提供多个版本的 OpenBLAS，其中一些启用了多线程，而其他的则仅以串行方式工作。例如，在 Fedora 中，`libopenblasp.so` 是线程安全的，但 `libopenblas.so` 不是。我们建议使用前者以获得最佳性能。要选择一个名称不同于默认 `libopenblas.so` 的 OpenBLAS 库，请将 `LIBBLAS=-l$(YOURBLAS)` 和 `LIBBLASNAME=lib$(YOURBLAS)` 传递给 `make`，将 `$(YOURBLAS)` 替换为您的库的名称。如果您希望您的包在不需要未版本化的 `.so` 符号链接的情况下工作，还可以在库的名称后添加 `.so.0`。

最后，OpenBLAS 包含了其自己的优化版本的 LAPACK。如果您设置 `USE_SYSTEM_BLAS=1` 和 `USE_SYSTEM_LAPACK=1`，您还应该设置 `LIBLAPACK=-l$(YOURBLAS)` 和 `LIBLAPACKNAME=lib$(YOURBLAS)`。否则，将使用参考 LAPACK，性能通常会低得多。

从 Julia 1.7 开始，Julia 使用 [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline) 在运行时选择不同的 BLAS。

# Point releasing 101

创建一个点/补丁版本包含几个不同的步骤。

## Backporting commits

一些拉取请求被标记为“待回溯 x.y”，例如“待回溯 0.6”。这表示从 release-x.y 分支标记的下一个后续版本应包含该拉取请求中的提交。一旦拉取请求合并到主分支，每个提交应为 [cherry picked](https://git-scm.com/docs/git-cherry-pick) 到一个专用分支，最终将合并到 release-x.y。

### Creating a backports branch

首先，基于 release-x.y 创建一个新分支。Julia 分支的典型命名约定是，如果这是一个个人分支，则在分支名称前加上你的首字母。为了举例说明，我们假设该分支的作者是 Jane Smith。

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

这确保了在您从 release-x.y 创建新分支之前，您的本地副本与 origin 是最新的。

### Cherry picking commits

现在我们进行实际的回溯。请在 GitHub 网页 UI 中找到所有标记为“backport pending x.y”的合并拉取请求。对于每一个，滚动到页面底部，查看“someperson merged commit `123abc` into `master` XX minutes ago”。请注意，提交名称是一个链接；如果你点击它，将会显示提交的内容。如果该页面显示 `123abc` 是一个合并提交，请返回 PR 页面——我们不想要合并提交，我们要的是实际的提交。然而，如果这没有显示合并提交，则意味着 PR 是通过压缩合并的。在这种情况下，请使用此页面上列出的提交旁边的 git SHA。

一旦你有了提交的 SHA，将其 cherry-pick 到回溯分支：

```
git cherry-pick -x -e <sha>
```

可能会出现需要手动解决的冲突。一旦冲突解决（如果适用），请在提交消息的正文中添加引入该提交的 GitHub 拉取请求的引用。

在所有相关的提交都在 backports 分支上之后，将该分支推送到 GitHub。

## Checking for performance regressions

点版本发布绝不应引入性能回退。幸运的是，Julia 基准测试机器人 Nanosoldier 可以针对任何分支运行基准测试，而不仅仅是主分支。在这种情况下，我们想要检查 js/backport-x.y 与 release-x.y 的基准测试结果。为此，请在您的回退拉取请求中使用评论唤醒 Nanosoldier 以结束他的机器人沉睡：

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

这将运行所有在 release-x.y 和 js/backport-x.y 上注册的基准测试，并生成结果摘要，标记所有的改进和回归。

如果 Nanosoldier 发现任何回归，尝试在本地验证并在必要时重新运行 Nanosoldier。如果回归被认为是真实的而不仅仅是噪声，您需要在主分支上找到一个提交以回退修复，如果存在的话，否则您应该确定是什么导致了回归并提交一个补丁（或让熟悉代码的人提交补丁）到主分支，然后在合并后回退该提交。（或者如果合适的话，直接向回退分支提交补丁。）

## Building test binaries

在将回溯 PR 合并到 `release-x.y` 分支后，更新你本地的 Julia 克隆，然后使用以下命令获取该分支的 SHA：

```
git rev-parse origin/release-x.y
```

将其保留，因为这是您将在 buildbot UI 的“修订”字段中输入的内容。

目前，您只需要用于 Linux x86-64 的二进制文件，因为这就是运行 PackageEvaluator 所需的。请访问 https://buildog.julialang.org，提交一个 `nuke_linux64` 的作业，然后排队一个 `package_linux64` 的作业，提供 SHA 作为修订版本。当打包作业完成后，它将把二进制文件上传到 AWS 的 `julialang2` 存储桶中。请获取 URL，因为它将用于 PackageEvaluator。

## Checking for package breakages

点版本发布绝不应破坏软件包，可能的例外是那些使用不面向用户的基础内部进行一些严重可疑黑客行为的软件包。（在这些情况下，也许可以和软件包作者谈谈。）

检查即将发布的新版本所做的更改是否会破坏软件包，可以使用 [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl)，通常简称为 "PkgEval"。PkgEval 是用于填充 GitHub 仓库和 pkg.julialang.org 上状态徽章的工具。它通常在 Nanosoldier 的非基准测试节点之一上运行，并使用 Vagrant 在独立的并行 VirtualBox 虚拟机中执行其任务。

### Setting up PackageEvaluator

克隆 PackageEvaluator 并创建一个名为 `backport-x.y.z` 的分支，然后检出该分支。请注意，所需的更改有点黑客和混乱，希望在未来的 PackageEvaluator 版本中能得到解决。要进行的更改将以 [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016) 为模型。

设置脚本的第一个参数是要运行的 Julia 版本，第二个参数是包名称的范围（AK 表示名称以 A-K 开头的包，LZ 表示名称以 L-Z 开头的包）。基本思路是我们将稍微调整一下，只运行两个版本的 Julia，当前的 x.y 版本和我们的回退版本，每个版本都有三个包的范围。

在链接的差异中，我们表示如果第二个参数是 LZ，则使用从我们的回溯分支构建的二进制文件，否则（AK）使用发布的二进制文件。然后我们使用第一个参数来运行软件包列表的一个部分：输入 0.4 的 A-F，0.5 的 G-N，以及 0.6 的 O-Z。

### Running PackageEvaluator

要运行 PkgEval，请找到一台足够强大的机器（例如 Nanosoldier 节点 1），然后运行

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

这将在 scripts/ 目录中生成一些文件夹。文件夹名称及其内容如下解码：

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

完成后，您可以从同一目录使用 `./summary.sh` 来生成发现的摘要报告。我们将对每个文件夹执行此操作，以按版本汇总整体结果。

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

现在我们有两个文件，`summary_release.txt` 和 `summary_backport.txt`，包含两个版本中每个包的 PackageEvaluator 测试结果（通过/失败）。

为了更容易地将这些数据导入到 Julia 中，我们将它们转换为 CSV 文件，然后使用 DataFrames 包来处理结果。要转换为 CSV，请将每个 .txt 文件复制到相应的 .csv 文件中，然后进入 Vim 并执行 `ggVGI"<esc>` 然后 `:%s/\.json /",/g`。（您不必使用 Vim；这只是其中一种方法。）现在使用类似于以下的 Julia 代码处理结果。

```julia
using DataFrames

release = readtable("summary_release.csv", header=false, names=[:package, :release])
backport = readtable("summary_backport.csv", header=false, names=[:package, :backport])

results = join(release, backport, on=:package, kind=:outer)

for result in eachrow(results)
    a = result[:release]
    b = result[:backport]
    if (isna(a) && !isna(b)) || (isna(b) && !isna(a))
        color = :yellow
    elseif a != b && occursin("pass", b)
        color = :green
    elseif a != b
        color = :red
    else
        continue
    end
    printstyled(result[:package], ": Release ", a, " -> Backport ", b, "\n", color=color)
end
```

这将把带颜色编码的行写入 `stdout`。所有红色的行必须进行调查，因为它们表示可能由回退版本引起的故障。黄色的行也应该关注，因为这意味着某个包在一个版本上运行，但由于某种原因在另一个版本上没有运行。如果您发现您的回退分支导致了故障，请使用 `git bisect` 来识别有问题的提交，使用 `git revert` 这些提交，然后重复该过程。

## Merging backports into the release branch

在您确保之后

  * 回溯的提交通过了所有Julia的单元测试，
  * 没有引入与发布分支相比的性能回归问题。
  * 回溯的提交不会破坏任何已注册的包，

然后，回溯分支准备好合并到 release-x.y。一旦合并，检查并从所有包含已回溯提交的拉取请求中移除“backport pending x.y”标签。不要从未回溯的 PR 中移除标签。

release-x.y 分支现在应该包含所有的新提交。我们要对该分支做的最后一件事是调整版本号。为此，请提交一个针对 release-x.y 的 PR，编辑 VERSION 文件以从版本号中删除 `-pre`。一旦合并，我们就准备好打标签了。

## Tagging the release

该是时候了！检查 release-x.y 分支，并确保您的本地分支副本与远程分支保持最新。在命令行中运行

```
git tag v$(cat VERSION)
git push --tags
```

这在本地创建标签并将其推送到 GitHub。

在标记发布后，提交另一个 PR 到 release-x.y，以增加补丁号并将 `-pre` 添加回末尾。这表示该分支状态反映了 x.y 系列下一个点发布的预发布版本。

遵循 Makefile 中的其余指示。

## Signing binaries

某些步骤将需要安全密码。要获取适当的密码，请联系 Elliot Saba (staticfloat) 或 Alex Arslan (ararslan)。请注意，每个平台的代码签名必须在该平台上进行（例如，Windows 签名必须在 Windows 上完成，等等）。

### Linux

代码签名必须在Linux上手动完成，但这非常简单。首先，从`juliasecure` AWS存储桶中的CodeSigning文件夹获取文件`julia.key`。使用以下命令将其添加到您的GnuPG密钥环中：

```
gpg --import julia.key
```

这将需要输入一个您必须从Elliot或Alex那里获得的密码。接下来，将密钥的信任级别设置为最高。首先输入一个 `gpg` 会话：

```
gpg --edit-key julia
```

在提示符下，输入 `trust`，然后在被询问信任级别时，提供可用的最高级别（可能是 5）。退出 GnuPG。

现在，对于在构建机器人上构建的每个 Linux tarball，输入

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

这将为每个 tarball 生成一个相应的 .asc 文件。就这样！

### macOS

代码签名应该在 macOS 构建机器人上自动进行。然而，验证其是否成功是很重要的。在运行 macOS 的系统或虚拟机上，下载在构建机器人上构建的 .dmg 文件。为了举例说明，假设 .dmg 文件名为 `julia-x.y.z-osx.dmg`。运行

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

请务必注意挂载时列出的磁盘名称！为了举例，我们假设这是 `disk3`。如果代码签名验证成功退出，`codesign` 步骤将没有输出。如果确实成功，您现在可以卸载 .dmg：

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

如果你收到类似的消息

> Julia-x.y.app：代码对象根本没有签名


然后您需要手动签名。

要手动签名，首先从 AWS 的 `juliasecure` 存储桶中的 CodeSigning 文件夹中检索 OS X 证书。使用 Keychain.app 将 .p12 文件添加到您的钥匙串中。向 Elliot Saba (staticfloat) 或 Alex Arslan (ararslan) 询问密钥的密码。现在运行

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

这可能会失败并显示类似的消息

> Julia-x.y.app：不允许资源分支、Finder 信息或类似的杂物


如果是这样，你需要删除多余的属性：

```
xattr -cr jlmnt/Julia-x.y.app
```

然后重试代码签名。如果没有产生错误，则重试验证。如果一切正常，卸载可写的 .dmg 并将其转换回只读：

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

验证生成的 .dmg 文件是否确实已修复，方法是双击它。如果一切看起来正常，弹出它，然后去掉名称中的 `_fixed` 后缀。就这样！

### Windows

签名必须在 Windows 上手动执行。首先，从 Microsoft 网站获取 Windows 10 SDK，其中包含必要的签名工具。我们需要 `SignTool` 工具，它应该已安装在类似 `C:\Program Files (x86)\Windows Kits\10\App Certification Kit` 的位置。从 `juliasecure` 的 CodeSigning 中获取 Windows 证书文件，并将它们放在与可执行文件相同的目录中。打开 Windows CMD 窗口，`cd` 到所有文件所在的位置，然后运行

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

请注意，`^` 是 Windows CMD 中的行续字符，`PASSWORD` 是此证书的密码占位符。像往常一样，请联系 Elliot 或 Alex 获取密码。如果没有错误，我们就没问题了！

## Uploading binaries

现在一切都已签署，我们需要将二进制文件上传到 AWS。您可以使用像 Cyberduck 这样的程序或 `aws` 命令行工具。二进制文件应放在 `julialang2` 存储桶中的适当文件夹中。例如，Linux x86-64 应放在 `julialang2/bin/linux/x.y`。请务必删除当前的 `julia-x.y-latest-linux-<arch>.tar.gz` 文件，并用 `julia-x.y.z-linux-<arch>.tar.gz` 的副本替换它。

我们还需要上传我们构建的所有内容的校验和，包括源 tarball 和所有发布的二进制文件。这很简单：

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

请注意，如果您在 macOS 上运行这些命令，您将获得略有不同的输出，可以通过查看现有文件进行重新格式化。Mac 用户还需要使用 `md5 -r` 而不是 `md5sum`。将 .md5 和 .sha256 文件上传到 AWS 的 `julialang2/bin/checksums`。

确保所有上传文件的AWS权限设置为“所有人：读取”。

对于我们上传的每个文件，我们需要清除 Fastly 缓存，以便网站上的链接指向更新后的文件。作为一个例子：

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

有时候这并不是必要的，但这样做还是好的。

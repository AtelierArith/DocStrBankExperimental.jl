# FreeBSD

Clang 是 FreeBSD 11.0-RELEASE 及以上版本的默认编译器。其余构建工具可以从 Ports Collection 中获取，并可以使用 `pkg install git gcc gmake cmake pkgconf` 安装。要构建 Julia，只需运行 `gmake`。 （请注意，必须使用 `gmake` 而不是 `make`，因为 FreeBSD 上的 `make` 对应于不兼容的 BSD Make，而不是 GNU Make。）

如上所述，重要的是要注意在 FreeBSD 上使用 `USE_SYSTEM_*` 标志时应谨慎。这是因为许多系统库，甚至来自 Ports Collection 的库，都链接到系统的 `libgcc_s.so.1`，或链接到另一个链接到系统 `libgcc_s` 的库。该库声明其 GCC 版本为 4.6，这对于构建 Julia 来说太旧，并且在链接时与其他库发生冲突。因此，强烈建议允许 Julia 构建其所有依赖项。如果您选择使用 `USE_SYSTEM_*` 标志，请注意 `/usr/local` 默认不在编译器路径中，因此您可能需要将 `LDFLAGS=-L/usr/local/lib` 和 `CPPFLAGS=-I/usr/local/include` 添加到您的 `Make.user` 中，尽管这样做可能会干扰其他依赖项。

请注意，x86架构由于缺乏编译器运行时库支持，不支持线程，因此如果您使用的是32位系统，可能需要在您的`Make.user`中设置`JULIA_THREADS=0`。

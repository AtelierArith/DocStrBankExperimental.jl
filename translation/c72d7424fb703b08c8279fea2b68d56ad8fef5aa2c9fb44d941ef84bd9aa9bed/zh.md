# macOS

您需要安装当前的 Xcode 命令行工具：在终端中运行 `xcode-select --install`。在每次 macOS 更新后，您需要重新运行此终端命令，否则可能会遇到缺少库或头文件的错误。

依赖库现在使用 [BinaryBuilder](https://binarybuilder.org) 构建，并将自动下载。这是构建 Julia 源代码的首选方式。如果您想自己构建所有库，您需要一个 64 位的 gfortran 来编译 Julia 依赖项。

```bash
brew install gcc
```

如果您在 `.bashrc` 或等效文件中设置了 `LD_LIBRARY_PATH` 或 `DYLD_LIBRARY_PATH`，Julia 可能无法找到与其捆绑在一起的各种库。需要取消设置这些环境变量以使 Julia 正常工作。

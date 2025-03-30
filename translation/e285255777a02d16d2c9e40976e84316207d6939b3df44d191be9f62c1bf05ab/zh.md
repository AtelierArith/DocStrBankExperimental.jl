# ARM (Linux)

Julia 完全支持 ARMv8 (AArch64) 处理器，并且在某些条件下支持 ARMv7 和 ARMv6 (AArch32)。此文件提供了编译的一般指南，以及针对特定设备的说明。

一个 [known issues](https://github.com/JuliaLang/julia/labels/arm) 的 ARM 列表可用。如果您遇到困难，请创建一个问题，包括 `cat /proc/cpuinfo` 的输出。

## 32-bit (ARMv6, ARMv7)

Julia 已成功在以下 ARMv6 和 ARMv7 设备的多个变体上编译：

  * ARMv7 / Cortex A15 三星 Chromebook 在 Crouton 下运行 Ubuntu Linux；
  * [Raspberry Pi](https://www.raspberrypi.org)
  * [Odroid](https://www.hardkernel.com)

Julia 至少需要 `armv6` 和 `vfpv2` 指令集。推荐使用 `armv7-a`。不支持 `armv5` 或软浮点。

### Raspberry Pi 1 / Raspberry Pi Zero

如果在 Raspberry Pi 中使用的 ARM CPU 类型未被 LLVM 检测到，则通过将以下内容添加到 `Make.user` 中显式设置 CPU 目标：

```
JULIA_CPU_TARGET=arm1176jzf-s
```

要完成构建，您可能需要增加交换文件的大小。为此，请编辑 `/etc/dphys-swapfile`，更改以下行：

```
CONF_SWAPSIZE=100
```

请提供您想要翻译的Markdown内容或文本。

```
CONF_SWAPSIZE=512
```

在重新启动交换文件服务之前：

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

Raspberry Pi 2中使用的ARM CPU类型未被LLVM检测到。通过将以下内容添加到`Make.user`中显式设置CPU目标：

`JULIA_CPU_TARGET=cortex-a7`

根据具体的编译器和发行版，可能会由于不支持的内联汇编而导致构建失败。在这种情况下，请将 `MCPU=armv7-a` 添加到 `Make.user`。

## AArch64 (ARMv8)

朱莉亚预计将在ARMv8 CPU上工作和构建。应该遵循一般的 [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md)。朱莉亚预计需要大约8GB的RAM或启用交换空间来构建自身。

### Known issues

从 Julia v1.10 开始，[JITLink](https://llvm.org/docs/JITLink.html) 在此架构上对于所有操作系统在链接到 LLVM 15 或更高版本时会自动启用。由于 [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236)，非平凡的工作负载可能会生成过多的内存映射，在 Linux 上可能会超过文件 `/proc/sys/vm/max_map_count` 中设置的内存映射限制（`mmap`），导致出现类似的错误。

```
JIT session error: Cannot allocate memory
```

如果发生这种情况，请向您的系统管理员请求增加内存映射的限制，例如使用命令

```
sysctl -w vm.max_map_count=262144
```

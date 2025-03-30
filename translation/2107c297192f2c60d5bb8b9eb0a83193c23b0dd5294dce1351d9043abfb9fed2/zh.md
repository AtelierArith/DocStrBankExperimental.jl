# Parallel Computing

Julia 支持这四类并发和并行编程：

1. **异步“任务”，或协程**:

    Julia 任务允许暂停和恢复 I/O、事件处理、生产者-消费者进程以及类似模式的计算。任务可以通过诸如 [`wait`](@ref) 和 [`fetch`](@ref) 的操作进行同步，并通过 [`Channel`](@ref) 进行通信。虽然严格来说它们本身并不是并行计算，但 Julia 允许你在多个线程上调度 [`Task`](@ref)。
2. **多线程**:

    Julia的 [multi-threading](@ref man-multithreading) 提供了在多个线程或CPU核心上同时调度任务的能力，共享内存。这通常是实现个人电脑或单个大型多核服务器上并行处理的最简单方法。Julia的多线程是可组合的。当一个多线程函数调用另一个多线程函数时，Julia会在可用资源上全局调度所有线程，而不会过度订阅。
3. **分布式计算**:

    分布式计算运行多个具有独立内存空间的 Julia 进程。这些进程可以在同一台计算机上或多台计算机上。[`Distributed`](@ref man-distributed) 标准库提供了远程执行 Julia 函数的能力。借助这个基本构建块，可以构建许多不同类型的分布式计算抽象。像 [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) 这样的包就是这种抽象的一个例子。另一方面，像 [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) 和 [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl) 的包提供了对现有 MPI 生态系统库的访问。
4. **GPU计算**:

    Julia GPU 编译器提供了在 GPU 上原生运行 Julia 代码的能力。针对 GPU 的 Julia 包有着丰富的生态系统。[JuliaGPU.org](https://juliagpu.org) 网站提供了功能列表、支持的 GPU、相关包和文档。

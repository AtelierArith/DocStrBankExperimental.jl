# Calling Conventions

Julia 使用三种调用约定来实现四个不同的目的：

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

本机调用约定旨在快速非通用调用。它通常使用专门的签名。

  * LLVM 幽灵（零长度类型）被省略。
  * LLVM 标量和向量是按值传递的。
  * LLVM 聚合类型（数组和结构体）是通过引用传递的。

小的返回值作为LLVM返回值返回。大的返回值通过“结构返回”（`sret`）约定返回，调用者提供一个指向返回槽的指针。

一个同质元组的参数或返回值有时被表示为LLVM向量，而不是LLVM数组。

## JL Call Convention

JL调用约定用于内置函数和通用调度。使用此约定的手写函数通过宏`JL_CALLABLE`声明。该约定使用正好3个参数：

  * `F`  - Julia 表示正在应用的函数
  * `args` - 指向指向盒子的指针数组的指针
  * `nargs` - 数组的长度

返回值是指向一个盒子的指针。

## C ABI

C ABI 包装器使得从 C 调用 Julia 成为可能。该包装器使用本机调用约定调用函数。

元组总是表示为 C 数组。

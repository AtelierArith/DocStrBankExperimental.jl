```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/InteractiveUtils/docs/src/index.md"
```

# [Interactive Utilities](@id man-interactive-utils)

`InteractiveUtils` 模块提供了用于 Julia 交互式使用的工具，例如代码 introspection 和剪贴板访问。它旨在用于交互式工作，并在 [interactive mode](@ref command-line-interface) 中自动加载。

```@docs
InteractiveUtils.apropos
InteractiveUtils.varinfo
InteractiveUtils.versioninfo
InteractiveUtils.methodswith
InteractiveUtils.subtypes
InteractiveUtils.supertypes
InteractiveUtils.edit(::AbstractString, ::Integer)
InteractiveUtils.edit(::Any)
InteractiveUtils.@edit
InteractiveUtils.define_editor
InteractiveUtils.less(::AbstractString)
InteractiveUtils.less(::Any)
InteractiveUtils.@less
InteractiveUtils.@which
InteractiveUtils.@functionloc
InteractiveUtils.@code_lowered
InteractiveUtils.@code_typed
InteractiveUtils.code_warntype
InteractiveUtils.@code_warntype
InteractiveUtils.code_llvm
InteractiveUtils.@code_llvm
InteractiveUtils.code_native
InteractiveUtils.@code_native
InteractiveUtils.@time_imports
InteractiveUtils.clipboard
```

```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/InteractiveUtils/docs/src/index.md"
```

# [Interactive Utilities](@id man-interactive-utils)

El módulo `InteractiveUtils` proporciona utilidades para el uso interactivo de Julia, como la introspección de código y el acceso al portapapeles. Está destinado al trabajo interactivo y se carga automáticamente en [interactive mode](@ref command-line-interface).

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

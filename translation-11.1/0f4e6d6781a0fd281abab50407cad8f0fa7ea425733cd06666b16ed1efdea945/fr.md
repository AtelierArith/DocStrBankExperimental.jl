```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/InteractiveUtils/docs/src/index.md"
```

# [Interactive Utilities](@id man-interactive-utils)

Le module `InteractiveUtils` fournit des utilitaires pour l'utilisation interactive de Julia, tels que l'introspection de code et l'accès au presse-papiers. Il est destiné au travail interactif et est chargé automatiquement dans [interactive mode](@ref command-line-interface).

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

```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/InteractiveUtils/docs/src/index.md"
```

# [Interactive Utilities](@id man-interactive-utils)

Das `InteractiveUtils`-Modul bietet Hilfsprogramme für die interaktive Nutzung von Julia, wie z. B. Code-Introspektion und Zugriff auf die Zwischenablage. Es ist für die interaktive Arbeit gedacht und wird automatisch in [interactive mode](@ref command-line-interface) geladen.

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

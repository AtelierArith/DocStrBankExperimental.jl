```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Establece o cambia el valor de la vinculación `name` en el módulo `module` a `x`. No se realiza conversión de tipo, por lo que si ya se ha declarado un tipo para la vinculación, `x` debe ser del tipo apropiado o se lanzará un error.

Además, se puede especificar un orden atómico para esta operación; de lo contrario, por defecto es monotónico.

Los usuarios normalmente accederán a esta funcionalidad a través de la función [`setproperty!`](@ref Base.setproperty!) o la sintaxis correspondiente (es decir, `module.name = x`), por lo que esto está destinado solo a casos de uso muy específicos.

!!! compat "Julia 1.9"
    Esta función requiere Julia 1.9 o posterior.


Véase también [`setproperty!`](@ref Base.setproperty!) y [`getglobal`](@ref)

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # igual que `getglobal(M, :a)`
ERROR: UndefVarError: `a` no definido en `M`
Sugerencia: añade una importación o asignación apropiada. Esta global fue declarada pero no asignada.
Stacktrace:
 [1] getproperty(x::Module, f::Symbol)
   @ Base ./Base.jl:42
 [2] top-level scope
   @ none:1

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```

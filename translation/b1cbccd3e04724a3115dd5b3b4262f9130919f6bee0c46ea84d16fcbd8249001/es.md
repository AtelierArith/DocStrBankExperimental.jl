```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

Recupera el valor de la vinculación `name` del módulo `module`. Opcionalmente, se puede definir un orden atómico para la operación; de lo contrario, se predetermina a monotónico.

Si bien el acceso a las vinculaciones del módulo utilizando [`getfield`](@ref) sigue siendo compatible, se debe preferir siempre el uso de `getglobal`, ya que `getglobal` permite el control sobre el orden atómico (`getfield` es siempre monotónico) y significa mejor la intención del código tanto para el usuario como para el compilador.

La mayoría de los usuarios no deberían tener que llamar a esta función directamente. La función [`getproperty`](@ref Base.getproperty) o la sintaxis correspondiente (es decir, `module.name`) deberían ser preferidas en todos menos en unos pocos casos de uso muy específicos.

!!! compat "Julia 1.9"
    Esta función requiere Julia 1.9 o posterior.


Véase también [`getproperty`](@ref Base.getproperty) y [`setglobal!`](@ref).

# Ejemplos

```jldoctest
julia> a = 1
1

julia> module M
       a = 2
       end;

julia> getglobal(@__MODULE__, :a)
1

julia> getglobal(M, :a)
2
```

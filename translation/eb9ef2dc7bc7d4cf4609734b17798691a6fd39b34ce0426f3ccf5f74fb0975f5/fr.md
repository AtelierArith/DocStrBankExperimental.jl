```
GC.@preserve x1 x2 ... xn expr
```

Marquez les objets `x1, x2, ...` comme étant *en cours d'utilisation* pendant l'évaluation de l'expression `expr`. Cela est uniquement requis dans le code non sécurisé où `expr` *utilise implicitement* de la mémoire ou d'autres ressources appartenant à l'un des `x`.

*Utilisation implicite* de `x` couvre toute utilisation indirecte de ressources logiquement possédées par `x` que le compilateur ne peut pas voir. Quelques exemples :

  * Accéder à la mémoire d'un objet directement via un `Ptr`
  * Passer un pointeur à `x` à `ccall`
  * Utiliser des ressources de `x` qui seraient nettoyées dans le finaliseur.

`@preserve` ne devrait généralement pas avoir d'impact sur les performances dans des cas d'utilisation typiques où il prolonge brièvement la durée de vie de l'objet. Dans l'implémentation, `@preserve` a des effets tels que la protection des objets alloués dynamiquement contre la collecte des ordures.

# Exemples

Lors du chargement à partir d'un pointeur avec `unsafe_load`, l'objet sous-jacent est utilisé implicitement, par exemple `x` est utilisé implicitement par `unsafe_load(p)` dans ce qui suit :

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

Lors du passage de pointeurs à `ccall`, l'objet pointé est utilisé implicitement et doit être préservé. (Notez cependant que vous devriez normalement passer `x` directement à `ccall`, ce qui compte comme une utilisation explicite.)

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # Alternative préférée
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```

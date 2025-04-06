```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Définissez ou changez la valeur de la liaison `name` dans le module `module` à `x`. Aucune conversion de type n'est effectuée, donc si un type a déjà été déclaré pour la liaison, `x` doit être du type approprié ou une erreur est levée.

De plus, un ordre atomique peut être spécifié pour cette opération, sinon il par défaut à monotone.

Les utilisateurs accéderont généralement à cette fonctionnalité via la fonction [`setproperty!`](@ref Base.setproperty!) ou la syntaxe correspondante (c'est-à-dire `module.name = x`) à la place, donc cela est destiné uniquement à des cas d'utilisation très spécifiques.

!!! compat "Julia 1.9"
    Cette fonction nécessite Julia 1.9 ou une version ultérieure.


Voir aussi [`setproperty!`](@ref Base.setproperty!) et [`getglobal`](@ref)

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # même que `getglobal(M, :a)`
ERROR: UndefVarError: `a` non défini dans `M`
Suggestion : ajoutez un import ou une affectation appropriée. Ce global a été déclaré mais non assigné.
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

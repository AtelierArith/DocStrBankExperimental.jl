```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

Récupère la valeur de la liaison `name` du module `module`. En option, un ordre atomique peut être défini pour l'opération, sinon il est par défaut monotone.

Bien que l'accès aux liaisons de module en utilisant [`getfield`](@ref) soit toujours pris en charge pour maintenir la compatibilité, l'utilisation de `getglobal` doit toujours être préférée car `getglobal` permet de contrôler l'ordre atomique (`getfield` est toujours monotone) et signifie mieux l'intention du code tant pour l'utilisateur que pour le compilateur.

La plupart des utilisateurs ne devraient pas avoir à appeler cette fonction directement – La fonction [`getproperty`](@ref Base.getproperty) ou la syntaxe correspondante (c'est-à-dire `module.name`) devrait être préférée dans tous les cas sauf quelques cas d'utilisation très spécifiques.

!!! compat "Julia 1.9"
    Cette fonction nécessite Julia 1.9 ou une version ultérieure.


Voir aussi [`getproperty`](@ref Base.getproperty) et [`setglobal!`](@ref).

# Exemples

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

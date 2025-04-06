```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

Indique au compilateur d'inférer `f` en utilisant les types déclarés des arguments `@nospecialize`. Cela peut être utilisé pour limiter le nombre de spécialisations générées par le compilateur pendant l'inférence.

# Exemples

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

Dans cet exemple, `f` sera inféré pour chaque type spécifique de `A`, mais `g` ne sera inféré qu'une seule fois avec le type d'argument déclaré `A::AbstractArray`, ce qui signifie que le compilateur ne verra probablement pas le temps d'inférence excessif sur celui-ci tout en ne pouvant pas inférer le type de retour concret. Sans le `@nospecializeinfer`, `f([1.0])` inférerait le type de retour de `g` comme `Float64`, indiquant que l'inférence a été effectuée pour `g(::Vector{Float64})` malgré l'interdiction de génération de code spécialisé.

!!! compat "Julia 1.10"
    L'utilisation de `Base.@nospecializeinfer` nécessite la version 1.10 de Julia.


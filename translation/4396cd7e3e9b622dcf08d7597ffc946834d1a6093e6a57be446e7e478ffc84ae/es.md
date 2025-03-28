```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

Indica al compilador que infiera `f` utilizando los tipos declarados de los argumentos `@nospecialize`d. Esto se puede usar para limitar el número de especializaciones generadas por el compilador durante la inferencia.

# Ejemplos

```julia
julia> f(A::AbstractArray) = g(A)
f (función genérica con 1 método)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (función genérica con 1 método)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

En este ejemplo, `f` será inferido para cada tipo específico de `A`, pero `g` solo será inferido una vez con el tipo de argumento declarado `A::AbstractArray`, lo que significa que el compilador probablemente no verá el tiempo excesivo de inferencia en él mientras no puede inferir el tipo de retorno concreto. Sin el `@nospecializeinfer`, `f([1.0])` inferiría el tipo de retorno de `g` como `Float64`, indicando que la inferencia se ejecutó para `g(::Vector{Float64})` a pesar de la prohibición de la generación de código especializado.

!!! compat "Julia 1.10"
    Usar `Base.@nospecializeinfer` requiere la versión 1.10 de Julia.


```

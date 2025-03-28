```
@nospecialize
```

Aplicado a un nombre de argumento de función, indica al compilador que la implementación del método no debe especializarse para diferentes tipos de ese argumento, sino que debe utilizar el tipo declarado para ese argumento. Se puede aplicar a un argumento dentro de una lista de argumentos formal, o en el cuerpo de la función. Cuando se aplica a un argumento, el macro debe envolver toda la expresión del argumento, por ejemplo, `@nospecialize(x::Real)` o `@nospecialize(i::Integer...)` en lugar de envolver solo el nombre del argumento. Cuando se usa en el cuerpo de una función, el macro debe ocurrir en posición de declaración y antes de cualquier código.

Cuando se usa sin argumentos, se aplica a todos los argumentos del ámbito padre. En el ámbito local, esto significa todos los argumentos de la función que contiene. En el ámbito global (de nivel superior), esto significa todos los métodos definidos posteriormente en el módulo actual.

La especialización se puede restablecer a la predeterminada utilizando [`@specialize`](@ref).

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! nota
    `@nospecialize` afecta la generación de código pero no la inferencia: limita la diversidad del código nativo resultante, pero no impone ninguna limitación (más allá de las estándar) sobre la inferencia de tipos. Usa [`Base.@nospecializeinfer`](@ref) junto con `@nospecialize` para suprimir adicionalmente la inferencia.


# Ejemplos

```julia
julia> f(A::AbstractArray) = g(A)
f (función genérica con 1 método)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (función genérica con 1 método)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

Aquí, la anotación `@nospecialize` resulta en el equivalente de

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

asegurando que solo se generará una versión del código nativo para `g`, una que sea genérica para cualquier `AbstractArray`. Sin embargo, el tipo de retorno específico aún se infiere para ambos, `g` y `f`, y esto todavía se utiliza para optimizar los llamadores de `f` y `g`.

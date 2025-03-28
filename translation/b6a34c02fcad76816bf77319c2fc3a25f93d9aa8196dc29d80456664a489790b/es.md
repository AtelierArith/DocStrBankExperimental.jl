```
let
```

Los bloques `let` crean un nuevo ámbito rígido y, opcionalmente, introducen nuevos enlaces locales.

Al igual que los [otros constructos de ámbito](@ref man-scope-table), los bloques `let` definen el bloque de código donde las variables locales recién introducidas son accesibles. Además, la sintaxis tiene un significado especial para las asignaciones separadas por comas y los nombres de variables que pueden aparecer opcionalmente en la misma línea que el `let`:

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

Las variables introducidas en esta línea son locales al bloque `let` y las asignaciones se evalúan en orden, con cada lado derecho evaluado en el ámbito sin considerar el nombre en el lado izquierdo. Por lo tanto, tiene sentido escribir algo como `let x = x`, ya que las dos variables `x` son distintas, con el lado izquierdo ocultando localmente el `x` del ámbito exterior. Esto puede ser incluso un modismo útil, ya que se crean nuevas variables locales cada vez que se ingresan ámbitos locales, pero esto solo es observable en el caso de variables que sobreviven a su ámbito a través de cierres. Una variable `let` sin una asignación, como `var2` en el ejemplo anterior, declara una nueva variable local que aún no está vinculada a un valor.

Por el contrario, los bloques [`begin`](@ref) también agrupan múltiples expresiones, pero no introducen un ámbito ni tienen la sintaxis de asignación especial.

### Ejemplos

En la función a continuación, hay un solo `x` que se actualiza iterativamente tres veces por el `map`. Los cierres devueltos hacen referencia a ese único `x` en su valor final:

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generic function with 1 method)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

Sin embargo, si agregamos un bloque `let` que introduce una *nueva* variable local, terminaremos con tres variables distintas siendo capturadas (una en cada iteración) a pesar de que elegimos usar (ocultar) el mismo nombre.

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generic function with 1 method)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

Todos los constructos de ámbito que introducen nuevas variables locales se comportan de esta manera cuando se ejecutan repetidamente; la característica distintiva de `let` es su capacidad para declarar de manera sucinta nuevos `local`s que pueden ocultar variables externas del mismo nombre. Por ejemplo, usar directamente el argumento de la función `do` captura de manera similar tres variables distintas:

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generic function with 1 method)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```

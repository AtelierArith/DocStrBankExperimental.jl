```
;
```

`;` tiene un papel similar en Julia que en muchos lenguajes similares a C, y se utiliza para delimitar el final de la declaración anterior.

`;` no es necesario al final de una línea, pero se puede usar para separar declaraciones en una sola línea o para unir declaraciones en una sola expresión.

Agregar `;` al final de una línea en el REPL suprimirá la impresión del resultado de esa expresión.

En las declaraciones de funciones, y opcionalmente en las llamadas, `;` separa los argumentos regulares de las palabras clave.

En literales de arreglos, los argumentos separados por punto y coma tienen su contenido concatenado. Un separador hecho de un solo `;` concatena verticalmente (es decir, a lo largo de la primera dimensión), `;;` concatena horizontalmente (segunda dimensión), `;;;` concatena a lo largo de la tercera dimensión, etc. Tal separador también se puede usar en la última posición en los corchetes cuadrados para agregar dimensiones adicionales de longitud 1.

Un `;` en la primera posición dentro de paréntesis se puede usar para construir una tupla nombrada. La misma sintaxis `(; ...)` en el lado izquierdo de una asignación permite la desestructuración de propiedades.

En el REPL estándar, escribir `;` en una línea vacía cambiará al modo shell.

# Ejemplos

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # sin el ; o una coma final esto asignaría a x
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # establecer variables b y x usando desestructuración de propiedades

julia> b, x
(2, 1)

julia> ; # al escribir ;, el aviso cambia (en su lugar) a: shell>
shell> echo hello
hello
```

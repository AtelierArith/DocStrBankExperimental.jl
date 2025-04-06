# Complex and Rational Numbers

Julia incluye tipos predefinidos tanto para números complejos como racionales, y soporta todas las operaciones estándar [Mathematical Operations and Elementary Functions](@ref) sobre ellos. [Conversion and Promotion](@ref conversion-and-promotion) están definidos de tal manera que las operaciones en cualquier combinación de tipos numéricos predefinidos, ya sean primitivos o compuestos, se comporten como se espera.

## Complex Numbers

La constante global [`im`](@ref) está vinculada al número complejo *i*, que representa la raíz cuadrada principal de -1. (Se rechazó el uso de `i` de los matemáticos o `j` de los ingenieros para esta constante global, ya que son nombres de variables de índice muy populares). Dado que Julia permite que los literales numéricos sean [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients), este vínculo es suficiente para proporcionar una sintaxis conveniente para los números complejos, similar a la notación matemática tradicional:

```jldoctest
julia> 1+2im
1 + 2im
```

Puedes realizar todas las operaciones aritméticas estándar con números complejos:

```jldoctest
julia> (1 + 2im)*(2 - 3im)
8 + 1im

julia> (1 + 2im)/(1 - 2im)
-0.6 + 0.8im

julia> (1 + 2im) + (1 - 2im)
2 + 0im

julia> (-3 + 2im) - (5 - 1im)
-8 + 3im

julia> (-1 + 2im)^2
-3 - 4im

julia> (-1 + 2im)^2.5
2.729624464784009 - 6.9606644595719im

julia> (-1 + 2im)^(1 + 1im)
-0.27910381075826657 + 0.08708053414102428im

julia> 3(2 - 5im)
6 - 15im

julia> 3(2 - 5im)^2
-63 - 60im

julia> 3(2 - 5im)^-1.0
0.20689655172413793 + 0.5172413793103449im
```

El mecanismo de promoción asegura que las combinaciones de operandos de diferentes tipos simplemente funcionen:

```jldoctest
julia> 2(1 - 1im)
2 - 2im

julia> (2 + 3im) - 1
1 + 3im

julia> (1 + 2im) + 0.5
1.5 + 2.0im

julia> (2 + 3im) - 0.5im
2.0 + 2.5im

julia> 0.75(1 + 2im)
0.75 + 1.5im

julia> (2 + 3im) / 2
1.0 + 1.5im

julia> (1 - 3im) / (2 + 2im)
-0.5 - 1.0im

julia> 2im^2
-2 + 0im

julia> 1 + 3/4im
1.0 - 0.75im
```

Tenga en cuenta que `3/4im == 3/(4*im) == -(3/4*im)`, ya que un coeficiente literal se asocia más estrechamente que la división.

Se proporcionan funciones estándar para manipular valores complejos:

```jldoctest
julia> z = 1 + 2im
1 + 2im

julia> real(1 + 2im) # real part of z
1

julia> imag(1 + 2im) # imaginary part of z
2

julia> conj(1 + 2im) # complex conjugate of z
1 - 2im

julia> abs(1 + 2im) # absolute value of z
2.23606797749979

julia> abs2(1 + 2im) # squared absolute value
5

julia> angle(1 + 2im) # phase angle in radians
1.1071487177940904
```

Como de costumbre, el valor absoluto ([`abs`](@ref)) de un número complejo es su distancia desde cero. [`abs2`](@ref) da el cuadrado del valor absoluto, y es de particular utilidad para números complejos ya que evita tomar una raíz cuadrada. [`angle`](@ref) devuelve el ángulo de fase en radianes (también conocido como la *argumento* o función *arg*). La gama completa de otros [Elementary Functions](@ref) también está definida para números complejos:

```jldoctest
julia> sqrt(1im)
0.7071067811865476 + 0.7071067811865475im

julia> sqrt(1 + 2im)
1.272019649514069 + 0.7861513777574233im

julia> cos(1 + 2im)
2.0327230070196656 - 3.0518977991517997im

julia> exp(1 + 2im)
-1.1312043837568135 + 2.4717266720048188im

julia> sinh(1 + 2im)
-0.4890562590412937 + 1.4031192506220405im
```

Tenga en cuenta que las funciones matemáticas típicamente devuelven valores reales cuando se aplican a números reales y valores complejos cuando se aplican a números complejos. Por ejemplo, [`sqrt`](@ref) se comporta de manera diferente cuando se aplica a `-1` en comparación con `-1 + 0im`, a pesar de que `-1 == -1 + 0im`:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

El [literal numeric coefficient notation](@ref man-numeric-literal-coefficients) no funciona al construir un número complejo a partir de variables. En su lugar, la multiplicación debe escribirse explícitamente:

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

Sin embargo, esto *no* se recomienda. En su lugar, utiliza la función más eficiente [`complex`](@ref) para construir un valor complejo directamente a partir de sus partes real e imaginaria:

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

Esta construcción evita las operaciones de multiplicación y suma.

[`Inf`](@ref) y [`NaN`](@ref) se propagan a través de números complejos en las partes real e imaginaria de un número complejo como se describe en la sección [Special floating-point values](@ref):

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

Julia tiene un tipo de número racional para representar relaciones exactas de enteros. Los racionales se construyen utilizando el operador [`//`](@ref):

```jldoctest
julia> 2//3
2//3
```

Si el numerador y el denominador de una fracción racional tienen factores comunes, se reducen a su forma más baja de modo que el denominador sea no negativo:

```jldoctest
julia> 6//9
2//3

julia> -4//8
-1//2

julia> 5//-15
-1//3

julia> -4//-12
1//3
```

Esta forma normalizada para una razón de enteros es única, por lo que la igualdad de valores racionales se puede comprobar verificando la igualdad del numerador y el denominador. El numerador y el denominador estandarizados de un valor racional se pueden extraer utilizando las funciones [`numerator`](@ref) y [`denominator`](@ref):

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

La comparación directa del numerador y el denominador generalmente no es necesaria, ya que las operaciones aritméticas y de comparación estándar están definidas para valores racionales:

```jldoctest
julia> 2//3 == 6//9
true

julia> 2//3 == 9//27
false

julia> 3//7 < 1//2
true

julia> 3//4 > 2//3
true

julia> 2//4 + 1//6
2//3

julia> 5//12 - 1//4
1//6

julia> 5//8 * 3//12
5//32

julia> 6//5 / 10//7
21//25
```

Los números racionales se pueden convertir fácilmente en números de punto flotante:

```jldoctest
julia> float(3//4)
0.75
```

La conversión de racional a punto flotante respeta la siguiente identidad para cualquier valor integral de `a` y `b`, excepto cuando `a==0 && b <= 0`:

```jldoctest
julia> a = 1; b = 2;

julia> isequal(float(a//b), a/b)
true

julia> a, b = 0, 0
(0, 0)

julia> float(a//b)
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]

julia> a/b
NaN

julia> a, b = 0, -1
(0, -1)

julia> float(a//b), a/b
(0.0, -0.0)
```

Construir valores racionales infinitos es aceptable:

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

Intentando construir un valor racional [`NaN`](@ref), sin embargo, es inválido:

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

Como de costumbre, el sistema de promoción hace que las interacciones con otros tipos numéricos sean sencillas:

```jldoctest
julia> 3//5 + 1
8//5

julia> 3//5 - 0.5
0.09999999999999998

julia> 2//7 * (1 + 2im)
2//7 + 4//7*im

julia> 2//7 * (1.5 + 2im)
0.42857142857142855 + 0.5714285714285714im

julia> 3//2 / (1 + 2im)
3//10 - 3//5*im

julia> 1//2 + 2im
1//2 + 2//1*im

julia> 1 + 2//3im
1//1 - 2//3*im

julia> 0.5 == 1//2
true

julia> 0.33 == 1//3
false

julia> 0.33 < 1//3
true

julia> 1//3 - 0.33
0.0033333333333332993
```

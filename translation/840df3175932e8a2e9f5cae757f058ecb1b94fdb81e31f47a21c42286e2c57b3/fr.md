# Complex and Rational Numbers

Julia inclut des types prédéfinis pour les nombres complexes et rationnels, et prend en charge toutes les [Mathematical Operations and Elementary Functions](@ref) standard sur eux. [Conversion and Promotion](@ref conversion-and-promotion) sont définis de sorte que les opérations sur n'importe quelle combinaison de types numériques prédéfinis, qu'ils soient primitifs ou composites, se comportent comme prévu.

## Complex Numbers

La constante globale [`im`](@ref) est liée au nombre complexe *i*, représentant la racine carrée principale de -1. (L'utilisation de `i` pour les mathématiciens ou de `j` pour les ingénieurs pour cette constante globale a été rejetée car ce sont des noms de variables d'index très populaires.) Étant donné que Julia permet aux littéraux numériques d'être [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients), cette liaison suffit à fournir une syntaxe pratique pour les nombres complexes, similaire à la notation mathématique traditionnelle :

```jldoctest
julia> 1+2im
1 + 2im
```

Vous pouvez effectuer toutes les opérations arithmétiques standard avec des nombres complexes :

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

Le mécanisme de promotion garantit que les combinaisons d'opérandes de différents types fonctionnent simplement :

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

Notez que `3/4im == 3/(4*im) == -(3/4*im)`, puisque un coefficient littéral a une priorité d'association plus forte que la division.

Des fonctions standard pour manipuler des valeurs complexes sont fournies :

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

Comme d'habitude, la valeur absolue ([`abs`](@ref)) d'un nombre complexe est sa distance à zéro. [`abs2`](@ref) donne le carré de la valeur absolue, et est particulièrement utile pour les nombres complexes car cela évite de prendre une racine carrée. [`angle`](@ref) renvoie l'angle de phase en radians (également connu sous le nom de *argument* ou fonction *arg*). L'ensemble complet des autres [Elementary Functions](@ref) est également défini pour les nombres complexes :

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

Notez que les fonctions mathématiques retournent généralement des valeurs réelles lorsqu'elles sont appliquées à des nombres réels et des valeurs complexes lorsqu'elles sont appliquées à des nombres complexes. Par exemple, [`sqrt`](@ref) se comporte différemment lorsqu'il est appliqué à `-1` par rapport à `-1 + 0im`, même si `-1 == -1 + 0im` :

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

Le [literal numeric coefficient notation](@ref man-numeric-literal-coefficients) ne fonctionne pas lors de la construction d'un nombre complexe à partir de variables. Au lieu de cela, la multiplication doit être écrite explicitement :

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

Cependant, cela n'est *pas* recommandé. Au lieu de cela, utilisez la fonction plus efficace [`complex`](@ref) pour construire une valeur complexe directement à partir de ses parties réelle et imaginaire :

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

Cette construction évite les opérations de multiplication et d'addition.

[`Inf`](@ref) et [`NaN`](@ref) se propagent à travers des nombres complexes dans les parties réelle et imaginaire d'un nombre complexe comme décrit dans la section [Special floating-point values](@ref) :

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

Julia a un type de nombre rationnel pour représenter des rapports exacts d'entiers. Les rationnels sont construits en utilisant l'opérateur [`//`](@ref) :

```jldoctest
julia> 2//3
2//3
```

Si le numérateur et le dénominateur d'un rationnel ont des facteurs communs, ils sont réduits à leurs termes les plus bas de sorte que le dénominateur soit non négatif :

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

Cette forme normalisée pour un rapport d'entiers est unique, donc l'égalité des valeurs rationnelles peut être testée en vérifiant l'égalité du numérateur et du dénominateur. Le numérateur et le dénominateur standardisés d'une valeur rationnelle peuvent être extraits en utilisant les fonctions [`numerator`](@ref) et [`denominator`](@ref) :

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

La comparaison directe du numérateur et du dénominateur n'est généralement pas nécessaire, car les opérations arithmétiques et de comparaison standard sont définies pour les valeurs rationnelles :

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

Les rationnels peuvent facilement être convertis en nombres à virgule flottante :

```jldoctest
julia> float(3//4)
0.75
```

La conversion d'un rationnel en flottant respecte l'identité suivante pour toutes les valeurs entières de `a` et `b`, sauf lorsque `a==0 && b <= 0` :

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

Construire des valeurs rationnelles infinies est acceptable :

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

Essayer de construire une valeur rationnelle [`NaN`](@ref), cependant, elle est invalide :

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

Comme d'habitude, le système de promotion rend les interactions avec d'autres types numériques sans effort :

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

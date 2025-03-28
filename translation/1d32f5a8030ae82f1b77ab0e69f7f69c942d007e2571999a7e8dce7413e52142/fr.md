# Mathematical Operations and Elementary Functions

Julia fournit une collection complète d'opérateurs arithmétiques de base et d'opérateurs bit à bit pour tous ses types primitifs numériques, tout en offrant des implémentations portables et efficaces d'une collection complète de fonctions mathématiques standard.

## Arithmetic Operators

Les éléments suivants [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations) sont pris en charge sur tous les types numériques primitifs :

| Expression | Name           | Description                            |
|:---------- |:-------------- |:-------------------------------------- |
| `+x`       | unary plus     | the identity operation                 |
| `-x`       | unary minus    | maps values to their additive inverses |
| `x + y`    | binary plus    | performs addition                      |
| `x - y`    | binary minus   | performs subtraction                   |
| `x * y`    | times          | performs multiplication                |
| `x / y`    | divide         | performs division                      |
| `x ÷ y`    | integer divide | x / y, truncated to an integer         |
| `x \ y`    | inverse divide | equivalent to `y / x`                  |
| `x ^ y`    | power          | raises `x` to the `y`th power          |
| `x % y`    | remainder      | equivalent to `rem(x, y)`              |

Un littéral numérique placé directement avant un identifiant ou des parenthèses, par exemple `2x` ou `2(x + y)`, est traité comme une multiplication, sauf avec une priorité plus élevée que d'autres opérations binaires. Voir [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients) pour plus de détails.

Julia's promotion system makes arithmetic operations on mixtures of argument types "just work" naturally and automatically. See [Conversion and Promotion](@ref conversion-and-promotion) for details of the promotion system.

Le signe ÷ peut être facilement tapé en écrivant `\div<tab>` dans le REPL ou l'IDE Julia. Voir le [manual section on Unicode input](@ref Unicode-Input) pour plus d'informations.

Voici quelques exemples simples utilisant des opérateurs arithmétiques :

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

(Par convention, nous avons tendance à espacer les opérateurs plus étroitement s'ils sont appliqués avant d'autres opérateurs voisins. Par exemple, nous écririons généralement `-x + 2` pour refléter que d'abord `x` est négatif, puis `2` est ajouté à ce résultat.)

Lorsqu'il est utilisé dans une multiplication, `false` agit comme un *zéro fort* :

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

Ceci est utile pour prévenir la propagation des valeurs `NaN` dans des quantités qui sont connues pour être nulles. Voir [Knuth (1992)](https://arxiv.org/abs/math/9205211) pour la motivation.

## Boolean Operators

Les [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations) sont pris en charge sur les [`Bool`](@ref) types :

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

La négation change `true` en `false` et vice versa. Les opérations de court-circuit sont expliquées sur la page liée.

Notez que `Bool` est un type entier et que toutes les règles de promotion habituelles et les opérateurs numériques sont également définis sur celui-ci.

## Bitwise Operators

Les éléments suivants [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators) sont pris en charge sur tous les types d'entiers primitifs :

| Expression | Name                                                                     |
|:---------- |:------------------------------------------------------------------------ |
| `~x`       | bitwise not                                                              |
| `x & y`    | bitwise and                                                              |
| `x \| y`   | bitwise or                                                               |
| `x ⊻ y`    | bitwise xor (exclusive or)                                               |
| `x ⊼ y`    | bitwise nand (not and)                                                   |
| `x ⊽ y`    | bitwise nor (not or)                                                     |
| `x >>> y`  | [logical shift](https://en.wikipedia.org/wiki/Logical_shift) right       |
| `x >> y`   | [arithmetic shift](https://en.wikipedia.org/wiki/Arithmetic_shift) right |
| `x << y`   | logical/arithmetic shift left                                            |

Voici quelques exemples avec des opérateurs bit à bit :

```jldoctest
julia> ~123
-124

julia> 123 & 234
106

julia> 123 | 234
251

julia> 123 ⊻ 234
145

julia> xor(123, 234)
145

julia> nand(123, 123)
-124

julia> 123 ⊼ 123
-124

julia> nor(123, 124)
-128

julia> 123 ⊽ 124
-128

julia> ~UInt32(123)
0xffffff84

julia> ~UInt8(123)
0x84
```

## Updating operators

Chaque opérateur arithmétique binaire et opérateur bit à bit a également une version de mise à jour qui assigne le résultat de l'opération à son opérande gauche. La version de mise à jour de l'opérateur binaire est formée en plaçant un `=` immédiatement après l'opérateur. Par exemple, écrire `x += 3` est équivalent à écrire `x = x + 3` :

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

Les versions mises à jour de tous les opérateurs arithmétiques binaires et des opérateurs bit à bit sont :

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    Un opérateur de mise à jour rebind la variable sur le côté gauche. En conséquence, le type de la variable peut changer.

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

Pour *chaque* opération binaire comme `^`, il existe une opération "point" correspondante `.^` qui est *automatiquement* définie pour effectuer `^` élément par élément sur des tableaux. Par exemple, `[1, 2, 3] ^ 3` n'est pas défini, car il n'y a pas de signification mathématique standard à "élever au cube" un tableau (non carré), mais `[1, 2, 3] .^ 3` est défini comme le calcul du résultat élément par élément (ou "vectorisé") `[1^3, 2^3, 3^3]`. De même, pour les opérateurs unaires comme `!` ou `√`, il existe un correspondant `.√` qui applique l'opérateur élément par élément.

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

Plus précisément, `a .^ b` est analysé comme le ["dot" call](@ref man-vectorized) `(^).(a,b)`, qui effectue une opération [broadcast](@ref Broadcasting) : il peut combiner des tableaux et des scalaires, des tableaux de la même taille (effectuant l'opération élément par élément), et même des tableaux de formes différentes (par exemple, en combinant des vecteurs de ligne et de colonne pour produire une matrice). De plus, comme tous les "appels par point" vectorisés, ces "opérateurs par point" sont *fusionnés*. Par exemple, si vous calculez `2 .* A.^2 .+ sin.(A)` (ou équivalemment `@. 2A^2 + sin(A)`, en utilisant le [`@.`](@ref @__dot__) macro) pour un tableau `A`, cela effectue une *unique* boucle sur `A`, calculant `2a^2 + sin(a)` pour chaque élément `a` de `A`. En particulier, les appels par point imbriqués comme `f.(g.(x))` sont fusionnés, et les opérateurs binaires "adjacents" comme `x .+ 3 .* x.^2` sont équivalents à des appels par point imbriqués `(+).(x, (*).(3, (^).(x, 2)))`.

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

Notez que la syntaxe par point est également applicable aux opérateurs définis par l'utilisateur. Par exemple, si vous définissez `⊗(A, B) = kron(A, B)` pour donner une syntaxe infixe pratique `A ⊗ B` pour les produits de Kronecker ([`kron`](@ref)), alors `[A, B] .⊗ [C, D]` calculera `[A⊗C, B⊗D]` sans codage supplémentaire.

Combiner des opérateurs de point avec des littéraux numériques peut être ambigu. Par exemple, il n'est pas clair si `1.+x` signifie `1. + x` ou `1 .+ x`. Par conséquent, cette syntaxe est interdite, et des espaces doivent être utilisés autour de l'opérateur dans de tels cas.

## Numeric Comparisons

Les opérations de comparaison standard sont définies pour tous les types numériques primitifs :

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

Voici quelques exemples simples :

```jldoctest
julia> 1 == 1
true

julia> 1 == 2
false

julia> 1 != 2
true

julia> 1 == 1.0
true

julia> 1 < 2
true

julia> 1.0 > 3
false

julia> 1 >= 1.0
true

julia> -1 <= 1
true

julia> -1 <= -1
true

julia> -1 <= -2
false

julia> 3 < -0.5
false
```

Les entiers sont comparés de manière standard – par comparaison de bits. Les nombres à virgule flottante sont comparés selon le [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008) :

  * Les nombres finis sont ordonnés de la manière habituelle.
  * Le zéro positif est égal mais pas supérieur au zéro négatif.
  * `Inf` est égal à lui-même et supérieur à tout le reste sauf `NaN`.
  * `-Inf` est égal à lui-même et inférieur à tout le reste sauf `NaN`.
  * `NaN` n'est égal à rien, n'est pas inférieur à rien et n'est pas supérieur à rien, y compris lui-même.

Le dernier point est potentiellement surprenant et mérite donc d'être noté :

```jldoctest
julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

et peut causer des maux de tête lors du travail avec [arrays](@ref man-multi-dim-arrays) :

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

Julia fournit des fonctions supplémentaires pour tester les nombres pour des valeurs spéciales, ce qui peut être utile dans des situations comme les comparaisons de clés de hachage :

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref) considère les `NaN` comme égaux entre eux :

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal` peut également être utilisé pour distinguer les zéros signés :

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

Les comparaisons de types mixtes entre entiers signés, entiers non signés et flottants peuvent être délicates. Une grande attention a été portée pour s'assurer que Julia les effectue correctement.

Pour d'autres types, `isequal` appelle par défaut [`==`](@ref), donc si vous souhaitez définir l'égalité pour vos propres types, vous n'avez qu'à ajouter une méthode `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566`. Si vous définissez votre propre fonction d'égalité, vous devriez probablement définir une méthode correspondante [`hash`](@ref) pour garantir que `isequal(x,y)` implique `hash(x) == hash(y)`.

### Chaining comparisons

Contrairement à la plupart des langages, avec le [notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators), les comparaisons peuvent être enchaînées de manière arbitraire :

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

La comparaison en chaîne est souvent très pratique dans le code numérique. Les comparaisons en chaîne utilisent l'opérateur `&&` pour les comparaisons scalaires, et l'opérateur [`&`](@ref) pour les comparaisons élément par élément, ce qui leur permet de fonctionner sur des tableaux. Par exemple, `0 .< A .< 1` donne un tableau booléen dont les entrées sont vraies lorsque les éléments correspondants de `A` se situent entre 0 et 1.

Notez le comportement d'évaluation des comparaisons enchaînées :

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> v(1) < v(2) <= v(3)
2
1
3
true

julia> v(1) > v(2) <= v(3)
2
1
false
```

L'expression du milieu n'est évaluée qu'une seule fois, plutôt que deux fois comme ce serait le cas si l'expression était écrite comme `v(1) < v(2) && v(2) <= v(3)`. Cependant, l'ordre des évaluations dans une comparaison en chaîne est indéfini. Il est fortement recommandé de ne pas utiliser d'expressions avec des effets de bord (comme l'impression) dans des comparaisons en chaîne. Si des effets de bord sont nécessaires, l'opérateur de court-circuit `&&` doit être utilisé explicitement (voir [Short-Circuit Evaluation](@ref)).

### Elementary Functions

Julia fournit une collection complète de fonctions et d'opérateurs mathématiques. Ces opérations mathématiques sont définies sur une classe aussi large de valeurs numériques que le permettent des définitions sensées, y compris les entiers, les nombres à virgule flottante, les rationnels et les nombres complexes, partout où de telles définitions ont un sens.

De plus, ces fonctions (comme toute fonction Julia) peuvent être appliquées de manière "vectorisée" aux tableaux et autres collections avec le [dot syntax](@ref man-vectorized) `f.(A)`, par exemple `sin.(A)` calculera le sinus de chaque élément d'un tableau `A`.

## Operator Precedence and Associativity

Julia applique l'ordre et l'associativité des opérations suivants, de la plus haute priorité à la plus basse :

| Category       | Operators                                              | Associativity   |
|:-------------- |:------------------------------------------------------ |:--------------- |
| Syntax         | `.` followed by `::`                                   | Left            |
| Exponentiation | `^`                                                    | Right           |
| Unary          | `+ - ! ~ ¬ √ ∛ ∜ ⋆ ± ∓ <: >:`                          | Right[^1]       |
| Bitshifts      | `<< >> >>>`                                            | Left            |
| Fractions      | `//`                                                   | Left            |
| Multiplication | `* / % & \ ÷`                                          | Left[^2]        |
| Addition       | `+ - \| ⊻`                                             | Left[^2]        |
| Syntax         | `: ..`                                                 | Left            |
| Syntax         | `\|>`                                                  | Left            |
| Syntax         | `<\|`                                                  | Right           |
| Comparisons    | `> < >= <= == === != !== <:`                           | Non-associative |
| Control flow   | `&&` followed by `\|\|` followed by `?`                | Right           |
| Pair           | `=>`                                                   | Right           |
| Assignments    | `= += -= *= /= //= \= ^= ÷= %= \|= &= ⊻= <<= >>= >>>=` | Right           |

[^1]: The unary operators `+` and `-` require explicit parentheses around their argument to disambiguate them from the operator `++`, etc. Other compositions of unary operators are parsed with right-associativity, e. g., `√√-a` as `√(√(-a))`.

[^2]: The operators `+`, `++` and `*` are non-associative. `a + b + c` is parsed as `+(a, b, c)` not `+(+(a, b), c)`. However, the fallback methods for `+(a, b, c, d...)` and `*(a, b, c, d...)` both default to left-associative evaluation.

Pour une liste complète de *tous* les opérateurs Julia et leur priorité, voir le haut de ce fichier : [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm). Notez que certains des opérateurs là-bas ne sont pas définis dans le module `Base`, mais peuvent être définis par des bibliothèques standard, des paquets ou du code utilisateur.

Vous pouvez également trouver la priorité numérique pour tout opérateur donné via la fonction intégrée `Base.operator_precedence`, où des nombres plus élevés ont la priorité :

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

Un symbole représentant l'associativité des opérateurs peut également être trouvé en appelant la fonction intégrée `Base.operator_associativity` :

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

Notez que des symboles tels que `:sin` renvoient une priorité de `0`. Cette valeur représente des opérateurs invalides et non des opérateurs de la plus basse priorité. De même, ces opérateurs se voient attribuer une associativité `:none`.

[Numeric literal coefficients](@ref man-numeric-literal-coefficients), par exemple `2x`, sont traités comme des multiplications avec une priorité plus élevée que toute autre opération binaire, à l'exception de `^` où ils ont une priorité plus élevée uniquement en tant qu'exposant.

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

La juxtaposition se parse comme un opérateur unaire, qui a la même asymétrie naturelle autour des exposants : `-x^y` et `2x^y` se parse comme `-(x^y)` et `2(x^y)` tandis que `x^-y` et `x^2y` se parse comme `x^(-y)` et `x^(2y)`.

## Numerical Conversions

Julia prend en charge trois formes de conversion numérique, qui diffèrent par leur gestion des conversions inexactes.

  * La notation `T(x)` ou `convert(T, x)` convertit `x` en une valeur de type `T`.

      * Si `T` est un type à virgule flottante, le résultat est la valeur représentable la plus proche, qui peut être l'infini positif ou négatif.
      * Si `T` est un type entier, une `InexactError` est levée si `x` n'est pas représentable par `T`.
  * `x % T` convertit un entier `x` en une valeur de type entier `T` congruente à `x` modulo `2^n`, où `n` est le nombre de bits dans `T`. En d'autres termes, la représentation binaire est tronquée pour s'adapter.
  * Le [Rounding functions](@ref) prend un type `T` comme argument optionnel. Par exemple, `round(Int,x)` est un raccourci pour `Int(round(x))`.

Les exemples suivants montrent les différentes formes.

```jldoctest
julia> Int8(127)
127

julia> Int8(128)
ERROR: InexactError: trunc(Int8, 128)
Stacktrace:
[...]

julia> Int8(127.0)
127

julia> Int8(3.14)
ERROR: InexactError: Int8(3.14)
Stacktrace:
[...]

julia> Int8(128.0)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]

julia> 127 % Int8
127

julia> 128 % Int8
-128

julia> round(Int8,127.4)
127

julia> round(Int8,127.6)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]
```

Voir [Conversion and Promotion](@ref conversion-and-promotion) pour savoir comment définir vos propres conversions et promotions.

### Rounding functions

| Function              | Description                      | Return type |
|:--------------------- |:-------------------------------- |:----------- |
| [`round(x)`](@ref)    | round `x` to the nearest integer | `typeof(x)` |
| [`round(T, x)`](@ref) | round `x` to the nearest integer | `T`         |
| [`floor(x)`](@ref)    | round `x` towards `-Inf`         | `typeof(x)` |
| [`floor(T, x)`](@ref) | round `x` towards `-Inf`         | `T`         |
| [`ceil(x)`](@ref)     | round `x` towards `+Inf`         | `typeof(x)` |
| [`ceil(T, x)`](@ref)  | round `x` towards `+Inf`         | `T`         |
| [`trunc(x)`](@ref)    | round `x` towards zero           | `typeof(x)` |
| [`trunc(T, x)`](@ref) | round `x` towards zero           | `T`         |

### Division functions

| Function                   | Description                                                                                               |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------- |
| [`div(x, y)`](@ref), `x÷y` | truncated division; quotient rounded towards zero                                                         |
| [`fld(x, y)`](@ref)        | floored division; quotient rounded towards `-Inf`                                                         |
| [`cld(x, y)`](@ref)        | ceiling division; quotient rounded towards `+Inf`                                                         |
| [`rem(x, y)`](@ref), `x%y` | remainder; satisfies `x == div(x, y)*y + rem(x, y)`; sign matches `x`                                     |
| [`mod(x, y)`](@ref)        | modulus; satisfies `x == fld(x, y)*y + mod(x, y)`; sign matches `y`                                       |
| [`mod1(x, y)`](@ref)       | `mod` with offset 1; returns `r∈(0, y]` for `y>0` or `r∈[y, 0)` for `y<0`, where `mod(r, y) == mod(x, y)` |
| [`mod2pi(x)`](@ref)        | modulus with respect to 2pi;  `0 <= mod2pi(x) < 2pi`                                                      |
| [`divrem(x, y)`](@ref)     | returns `(div(x, y),rem(x, y))`                                                                           |
| [`fldmod(x, y)`](@ref)     | returns `(fld(x, y), mod(x, y))`                                                                          |
| [`gcd(x, y...)`](@ref)     | greatest positive common divisor of `x`, `y`,...                                                          |
| [`lcm(x, y...)`](@ref)     | least positive common multiple of `x`, `y`,...                                                            |

### Sign and absolute value functions

| Function                 | Description                                                |
|:------------------------ |:---------------------------------------------------------- |
| [`abs(x)`](@ref)         | a positive value with the magnitude of `x`                 |
| [`abs2(x)`](@ref)        | the squared magnitude of `x`                               |
| [`sign(x)`](@ref)        | indicates the sign of `x`, returning -1, 0, or +1          |
| [`signbit(x)`](@ref)     | indicates whether the sign bit is on (true) or off (false) |
| [`copysign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `y`      |
| [`flipsign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `x*y`    |

### Powers, logs and roots

| Function                 | Description                                                                |
|:------------------------ |:-------------------------------------------------------------------------- |
| [`sqrt(x)`](@ref), `√x`  | square root of `x`                                                         |
| [`cbrt(x)`](@ref), `∛x`  | cube root of `x`                                                           |
| [`hypot(x, y)`](@ref)    | hypotenuse of right-angled triangle with other sides of length `x` and `y` |
| [`exp(x)`](@ref)         | natural exponential function at `x`                                        |
| [`expm1(x)`](@ref)       | accurate `exp(x) - 1` for `x` near zero                                    |
| [`ldexp(x, n)`](@ref)    | `x * 2^n` computed efficiently for integer values of `n`                   |
| [`log(x)`](@ref)         | natural logarithm of `x`                                                   |
| [`log(b, x)`](@ref)      | base `b` logarithm of `x`                                                  |
| [`log2(x)`](@ref)        | base 2 logarithm of `x`                                                    |
| [`log10(x)`](@ref)       | base 10 logarithm of `x`                                                   |
| [`log1p(x)`](@ref)       | accurate `log(1 + x)` for `x` near zero                                    |
| [`exponent(x)`](@ref)    | binary exponent of `x`                                                     |
| [`significand(x)`](@ref) | binary significand (a.k.a. mantissa) of a floating-point number `x`        |

Pour un aperçu des raisons pour lesquelles des fonctions comme [`hypot`](@ref), [`expm1`](@ref), et [`log1p`](@ref) sont nécessaires et utiles, consultez les excellents articles de blog de John D. Cook sur le sujet : [expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/), et [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/).

### Trigonometric and hyperbolic functions

Toutes les fonctions trigonométriques et hyperboliques standard sont également définies :

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

Ce sont toutes des fonctions à un seul argument, avec [`atan`](@ref) acceptant également deux arguments correspondant à une fonction traditionnelle [`atan2`](https://en.wikipedia.org/wiki/Atan2).

De plus, [`sinpi(x)`](@ref) et [`cospi(x)`](@ref) sont fournis pour des calculs plus précis de [`sin(pi * x)`](@ref) et [`cos(pi * x)`](@ref) respectivement.

Pour calculer des fonctions trigonométriques avec des degrés au lieu de radians, suffixez la fonction avec `d`. Par exemple, [`sind(x)`](@ref) calcule le sinus de `x` où `x` est spécifié en degrés. La liste complète des fonctions trigonométriques avec des variantes en degrés est :

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

De nombreuses autres fonctions mathématiques spéciales sont fournies par le package [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl).

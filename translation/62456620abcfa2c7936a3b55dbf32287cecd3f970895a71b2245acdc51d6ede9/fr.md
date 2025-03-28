# Integers and Floating-Point Numbers

Les entiers et les valeurs à virgule flottante sont les éléments de base de l'arithmétique et du calcul. Les représentations intégrées de ces valeurs sont appelées primitives numériques, tandis que les représentations d'entiers et de nombres à virgule flottante en tant que valeurs immédiates dans le code sont connues sous le nom de littéraux numériques. Par exemple, `1` est un littéral entier, tandis que `1.0` est un littéral à virgule flottante ; leurs représentations binaires en mémoire en tant qu'objets sont des primitives numériques.

Julia fournit une large gamme de types numériques primitifs, et un ensemble complet d'opérateurs arithmétiques et bit à bit ainsi que des fonctions mathématiques standard sont définis sur eux. Ceux-ci se mappent directement sur les types numériques et les opérations qui sont pris en charge nativement sur les ordinateurs modernes, permettant ainsi à Julia de tirer pleinement parti des ressources de calcul. De plus, Julia fournit un support logiciel pour [Arbitrary Precision Arithmetic](@ref), qui peut gérer des opérations sur des valeurs numériques qui ne peuvent pas être représentées efficacement dans les représentations matérielles natives, mais au prix d'une performance relativement plus lente.

Les types numériques primitifs de Julia sont les suivants :

  * **Types entiers :**

| Type              | Signed? | Number of bits | Smallest value | Largest value |
|:----------------- |:------- |:-------------- |:-------------- |:------------- |
| [`Int8`](@ref)    | ✓       | 8              | -2^7           | 2^7 - 1       |
| [`UInt8`](@ref)   |         | 8              | 0              | 2^8 - 1       |
| [`Int16`](@ref)   | ✓       | 16             | -2^15          | 2^15 - 1      |
| [`UInt16`](@ref)  |         | 16             | 0              | 2^16 - 1      |
| [`Int32`](@ref)   | ✓       | 32             | -2^31          | 2^31 - 1      |
| [`UInt32`](@ref)  |         | 32             | 0              | 2^32 - 1      |
| [`Int64`](@ref)   | ✓       | 64             | -2^63          | 2^63 - 1      |
| [`UInt64`](@ref)  |         | 64             | 0              | 2^64 - 1      |
| [`Int128`](@ref)  | ✓       | 128            | -2^127         | 2^127 - 1     |
| [`UInt128`](@ref) |         | 128            | 0              | 2^128 - 1     |
| [`Bool`](@ref)    | N/A     | 8              | `false` (0)    | `true` (1)    |

  * **Types à virgule flottante :**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

De plus, un support complet pour [Complex and Rational Numbers](@ref) est construit sur ces types numériques primitifs. Tous les types numériques interagissent naturellement sans conversion explicite, grâce à un [type promotion system](@ref conversion-and-promotion) flexible et extensible par l'utilisateur.

## Integers

Les entiers littéraux sont représentés de la manière standard :

```jldoctest
julia> 1
1

julia> 1234
1234
```

Le type par défaut pour un littéral entier dépend de l'architecture du système cible, qu'elle soit 32 bits ou 64 bits :

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

La variable interne de Julia [`Sys.WORD_SIZE`](@ref) indique si le système cible est en 32 bits ou en 64 bits :

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia définit également les types `Int` et `UInt`, qui sont des alias pour les types d'entiers natifs signés et non signés du système respectivement :

```julia-repl
# 32-bit system:
julia> Int
Int32
julia> UInt
UInt32

# 64-bit system:
julia> Int
Int64
julia> UInt
UInt64
```

Les littéraux d'entiers plus grands qui ne peuvent pas être représentés en utilisant uniquement 32 bits mais qui peuvent être représentés en 64 bits créent toujours des entiers 64 bits, quel que soit le type de système :

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

Les entiers non signés sont saisis et affichés en utilisant le préfixe `0x` et les chiffres hexadécimaux (base 16) `0-9a-f` (les chiffres en majuscules `A-F` fonctionnent également pour l'entrée). La taille de la valeur non signée est déterminée par le nombre de chiffres hexadécimaux utilisés :

```jldoctest
julia> x = 0x1
0x01

julia> typeof(x)
UInt8

julia> x = 0x123
0x0123

julia> typeof(x)
UInt16

julia> x = 0x1234567
0x01234567

julia> typeof(x)
UInt32

julia> x = 0x123456789abcdef
0x0123456789abcdef

julia> typeof(x)
UInt64

julia> x = 0x11112222333344445555666677778888
0x11112222333344445555666677778888

julia> typeof(x)
UInt128
```

Ce comportement est basé sur l'observation que lorsque l'on utilise des littéraux hexadécimaux non signés pour des valeurs entières, on les utilise généralement pour représenter une séquence d'octets numériques fixe, plutôt que simplement une valeur entière.

Les littéraux binaires et octaux sont également pris en charge :

```jldoctest
julia> x = 0b10
0x02

julia> typeof(x)
UInt8

julia> x = 0o010
0x08

julia> typeof(x)
UInt8

julia> x = 0x00000000000000001111222233334444
0x00000000000000001111222233334444

julia> typeof(x)
UInt128
```

En ce qui concerne les littéraux hexadécimaux, les littéraux binaires et octaux produisent des types d'entiers non signés. La taille de l'élément de données binaire est la taille minimale nécessaire, si le chiffre de tête du littéral n'est pas `0`. Dans le cas de zéros de tête, la taille est déterminée par la taille minimale nécessaire pour un littéral, qui a la même longueur mais un chiffre de tête `1`. Cela signifie que :

  * `0x1` et `0x12` sont des littéraux `UInt8`,
  * `0x123` et `0x1234` sont des littéraux `UInt16`,
  * `0x12345` et `0x12345678` sont des littéraux `UInt32`,
  * `0x123456789` et `0x1234567890adcdef` sont des littéraux `UInt64`, etc.

Même s'il y a des chiffres zéro en tête qui ne contribuent pas à la valeur, ils comptent pour déterminer la taille de stockage d'un littéral. Ainsi, `0x01` est un `UInt8` tandis que `0x0001` est un `UInt16`.

Cela permet à l'utilisateur de contrôler la taille.

Les littéraux non signés (commençant par `0x`) qui codent des entiers trop grands pour être représentés en tant que valeurs `UInt128` construiront des valeurs `BigInt` à la place. Ce n'est pas un type non signé, mais c'est le seul type intégré suffisamment grand pour représenter de telles valeurs entières grandes.

Les littéraux binaires, octaux et hexadécimaux peuvent être signés par un `-` immédiatement précédant le littéral non signé. Ils produisent un entier non signé de la même taille que le littéral non signé le ferait, avec le complément à deux de la valeur :

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

Les valeurs minimales et maximales représentables des types numériques primitifs tels que les entiers sont données par les fonctions [`typemin`](@ref) et [`typemax`](@ref) :

```jldoctest
julia> (typemin(Int32), typemax(Int32))
(-2147483648, 2147483647)

julia> for T in [Int8,Int16,Int32,Int64,Int128,UInt8,UInt16,UInt32,UInt64,UInt128]
           println("$(lpad(T,7)): [$(typemin(T)),$(typemax(T))]")
       end
   Int8: [-128,127]
  Int16: [-32768,32767]
  Int32: [-2147483648,2147483647]
  Int64: [-9223372036854775808,9223372036854775807]
 Int128: [-170141183460469231731687303715884105728,170141183460469231731687303715884105727]
  UInt8: [0,255]
 UInt16: [0,65535]
 UInt32: [0,4294967295]
 UInt64: [0,18446744073709551615]
UInt128: [0,340282366920938463463374607431768211455]
```

Les valeurs retournées par [`typemin`](@ref) et [`typemax`](@ref) sont toujours du type d'argument donné. (L'expression ci-dessus utilise plusieurs fonctionnalités qui n'ont pas encore été introduites, y compris [for loops](@ref man-loops), [Strings](@ref man-strings), et [Interpolation](@ref string-interpolation), mais devrait être suffisamment facile à comprendre pour les utilisateurs ayant une certaine expérience en programmation.)

### Overflow behavior

En Julia, dépasser la valeur maximale représentable d'un type donné entraîne un comportement de débordement :

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

Les opérations arithmétiques avec les types entiers de Julia effectuent intrinsèquement [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic), reflétant les caractéristiques de l'arithmétique entière sur le matériel informatique moderne. Dans les scénarios où un dépassement est une possibilité, il est crucial de vérifier explicitement les effets de débordement qui peuvent résulter de tels dépassements. Le module [`Base.Checked`](@ref) fournit une suite d'opérations arithmétiques équipées de vérifications de débordement, qui déclenchent des erreurs si un dépassement se produit. Pour les cas d'utilisation où le débordement ne peut être toléré en aucune circonstance, il est conseillé d'utiliser le type [`BigInt`](@ref), comme détaillé dans [Arbitrary Precision Arithmetic](@ref).

Un exemple de comportement de débordement et comment le résoudre potentiellement est le suivant :

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

La division entière (la fonction `div`) a deux cas exceptionnels : la division par zéro et la division du plus bas nombre négatif ([`typemin`](@ref)) par -1. Chacun de ces cas déclenche une [`DivideError`](@ref). Les fonctions de reste et de module (`rem` et `mod`) déclenchent une `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566` lorsque leur deuxième argument est zéro.

## Floating-Point Numbers

Les nombres à virgule flottante littéraux sont représentés dans les formats standard, en utilisant [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation) lorsque cela est nécessaire :

```jldoctest
julia> 1.0
1.0

julia> 1.
1.0

julia> 0.5
0.5

julia> .5
0.5

julia> -1.23
-1.23

julia> 1e10
1.0e10

julia> 2.5e-4
0.00025
```

Les résultats ci-dessus sont toutes des valeurs [`Float64`](@ref). Les valeurs littérales [`Float32`](@ref) peuvent être saisies en écrivant un `f` à la place de `e` :

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

Les valeurs peuvent être converties en [`Float32`](@ref) facilement :

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

Les littéraux flottants hexadécimaux sont également valides, mais uniquement en tant que valeurs [`Float64`](@ref), avec `p` précédant l'exposant en base 2 :

```jldoctest
julia> 0x1p0
1.0

julia> 0x1.8p3
12.0

julia> x = 0x.4p-1
0.125

julia> typeof(x)
Float64
```

Les nombres à virgule flottante en demi-précision sont également pris en charge ([`Float16`](@ref)), mais ils sont implémentés en logiciel et utilisent [`Float32`](@ref) pour les calculs.

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

Le soulignement `_` peut être utilisé comme séparateur de chiffres :

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

Les nombres à virgule flottante ont [two zeros](https://en.wikipedia.org/wiki/Signed_zero), zéro positif et zéro négatif. Ils sont égaux l'un à l'autre mais ont des représentations binaires différentes, comme on peut le voir en utilisant la fonction [`bitstring`](@ref) :

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

Il existe trois valeurs flottantes standard spécifiées qui ne correspondent à aucun point sur la droite des nombres réels :

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

Pour une discussion plus approfondie sur la façon dont ces valeurs flottantes non finies sont ordonnées les unes par rapport aux autres et par rapport à d'autres flottants, voir [Numeric Comparisons](@ref). Par le [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008), ces valeurs flottantes sont les résultats de certaines opérations arithmétiques :

```jldoctest
julia> 1/Inf
0.0

julia> 1/0
Inf

julia> -5/0
-Inf

julia> 0.000001/0
Inf

julia> 0/0
NaN

julia> 500 + Inf
Inf

julia> 500 - Inf
-Inf

julia> Inf + Inf
Inf

julia> Inf - Inf
NaN

julia> Inf * Inf
Inf

julia> Inf / Inf
NaN

julia> 0 * Inf
NaN

julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

Les fonctions [`typemin`](@ref) et [`typemax`](@ref) s'appliquent également aux types à virgule flottante :

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

La plupart des nombres réels ne peuvent pas être représentés exactement avec des nombres à virgule flottante, et il est donc important, pour de nombreux usages, de connaître la distance entre deux nombres à virgule flottante adjacents représentables, souvent connue sous le nom de [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon).

Julia fournit [`eps`](@ref), qui donne la distance entre `1.0` et la prochaine valeur flottante représentable plus grande :

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

Ces valeurs sont `2.0^-23` et `2.0^-52` en tant que [`Float32`](@ref) et [`Float64`](@ref), respectivement. La fonction [`eps`](@ref) peut également prendre une valeur à virgule flottante comme argument et donne la différence absolue entre cette valeur et la prochaine valeur à virgule flottante représentable. C'est-à-dire que `eps(x)` produit une valeur du même type que `x` telle que `x + eps(x)` est la prochaine valeur à virgule flottante représentable plus grande que `x` :

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(1000.)
1.1368683772161603e-13

julia> eps(1e-27)
1.793662034335766e-43

julia> eps(0.0)
5.0e-324
```

La distance entre deux nombres à virgule flottante représentables adjacents n'est pas constante, mais est plus petite pour des valeurs plus petites et plus grande pour des valeurs plus grandes. En d'autres termes, les nombres à virgule flottante représentables sont les plus denses sur la droite des nombres réels près de zéro, et deviennent de plus en plus rares de manière exponentielle à mesure que l'on s'éloigne de zéro. Par définition, `eps(1.0)` est le même que `eps(Float64)` puisque `1.0` est une valeur à virgule flottante de 64 bits.

Julia fournit également les fonctions [`nextfloat`](@ref) et [`prevfloat`](@ref) qui renvoient respectivement le plus grand ou le plus petit nombre à virgule flottante représentable par rapport à l'argument :

```jldoctest
julia> x = 1.25f0
1.25f0

julia> nextfloat(x)
1.2500001f0

julia> prevfloat(x)
1.2499999f0

julia> bitstring(prevfloat(x))
"00111111100111111111111111111111"

julia> bitstring(x)
"00111111101000000000000000000000"

julia> bitstring(nextfloat(x))
"00111111101000000000000000000001"
```

Cet exemple met en évidence le principe général selon lequel les nombres à virgule flottante représentables adjacents ont également des représentations entières binaires adjacentes.

### Rounding modes

Si un nombre n'a pas de représentation en virgule flottante exacte, il doit être arrondi à une valeur représentable appropriée. Cependant, la manière dont cet arrondi est effectué peut être modifiée si nécessaire selon les modes d'arrondi présentés dans le [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008).

Le mode par défaut utilisé est toujours [`RoundNearest`](@ref), qui arrondit à la valeur représentable la plus proche, avec des égalités arrondies vers la valeur la plus proche ayant un bit significatif le moins significatif pair.

### Background and References

L'arithmétique à virgule flottante implique de nombreuses subtilités qui peuvent surprendre les utilisateurs qui ne sont pas familiers avec les détails d'implémentation de bas niveau. Cependant, ces subtilités sont décrites en détail dans la plupart des livres sur le calcul scientifique, ainsi que dans les références suivantes :

  * Le guide définitif sur l'arithmétique à virgule flottante est le [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html); cependant, il n'est pas disponible gratuitement en ligne.
  * Pour une présentation brève mais claire de la façon dont les nombres à virgule flottante sont représentés, consultez le [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/) de John D. Cook sur le sujet ainsi que son [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/) concernant certains des problèmes découlant de la façon dont cette représentation diffère du comportement de l'abstraction idéalisée des nombres réels.
  * Aussi recommandé est le [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/).
  * Pour une excellente discussion approfondie sur les nombres à virgule flottante et les problèmes de précision numérique rencontrés lors de leur utilisation, consultez l'article de David Goldberg [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf).
  * Pour une documentation encore plus exhaustive sur l'histoire, la justification et les problèmes liés aux nombres à virgule flottante, ainsi qu'une discussion sur de nombreux autres sujets en informatique numérique, consultez le [collected writings](https://people.eecs.berkeley.edu/~wkahan/) de [William Kahan](https://en.wikipedia.org/wiki/William_Kahan), communément connu sous le nom de "Père de la virgule flottante". D'un intérêt particulier peut être [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html).

## Arbitrary Precision Arithmetic

Pour permettre des calculs avec des entiers et des nombres à virgule flottante de précision arbitraire, Julia encapsule le [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) et le [GNU MPFR Library](https://www.mpfr.org), respectivement. Les types [`BigInt`](@ref) et [`BigFloat`](@ref) sont disponibles dans Julia pour les entiers et les nombres à virgule flottante de précision arbitraire, respectivement.

Les constructeurs existent pour créer ces types à partir de types numériques primitifs, et le [string literal](@ref non-standard-string-literals) [`@big_str`](@ref) ou [`parse`](@ref) peuvent être utilisés pour les construire à partir de `AbstractString`s. Les `BigInt`s peuvent également être entrés en tant que littéraux entiers lorsqu'ils sont trop grands pour d'autres types entiers intégrés. Notez qu'il n'existe pas de type entier à précision arbitraire non signé dans `Base` (`BigInt` est suffisant dans la plupart des cas), des littéraux hexadécimaux, octaux et binaires peuvent être utilisés (en plus des littéraux décimaux).

Une fois créés, ils participent à l'arithmétique avec tous les autres types numériques grâce à [type promotion and conversion mechanism](@ref conversion-and-promotion) :

```jldoctest
julia> BigInt(typemax(Int64)) + 1
9223372036854775808

julia> big"123456789012345678901234567890" + 1
123456789012345678901234567891

julia> parse(BigInt, "123456789012345678901234567890") + 1
123456789012345678901234567891

julia> string(big"2"^200, base=16)
"100000000000000000000000000000000000000000000000000"

julia> 0x100000000000000000000000000000000-1 == typemax(UInt128)
true

julia> 0x000000000000000000000000000000000
0

julia> typeof(ans)
BigInt

julia> big"1.23456789012345678901"
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> parse(BigFloat, "1.23456789012345678901")
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> BigFloat(2.0^66) / 3
2.459565876494606882133333333333333333333333333333333333333333333333333333333344e+19

julia> factorial(BigInt(40))
815915283247897734345611269596115894272000000000
```

Cependant, la promotion de type entre les types primitifs ci-dessus et [`BigInt`](@ref)/[`BigFloat`](@ref) n'est pas automatique et doit être explicitement indiquée.

```jldoctest
julia> x = typemin(Int64)
-9223372036854775808

julia> x = x - 1
9223372036854775807

julia> typeof(x)
Int64

julia> y = BigInt(typemin(Int64))
-9223372036854775808

julia> y = y - 1
-9223372036854775809

julia> typeof(y)
BigInt
```

La précision par défaut (en nombre de bits de la mantisse) et le mode d'arrondi des opérations [`BigFloat`](@ref) peuvent être modifiés globalement en appelant [`setprecision`](@ref) et [`setrounding`](@ref), et tous les calculs ultérieurs tiendront compte de ces changements. Alternativement, la précision ou l'arrondi peuvent être modifiés uniquement dans l'exécution d'un bloc de code particulier en utilisant les mêmes fonctions avec un bloc `do` :

```jldoctest
julia> setrounding(BigFloat, RoundUp) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.100000000000000000000000000000000000000000000000000000000000000000000000000003

julia> setrounding(BigFloat, RoundDown) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> setprecision(40) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.1000000000004
```

!!! warning
    La relation entre [`setprecision`](@ref) ou [`setrounding`](@ref) et [`@big_str`](@ref), la macro utilisée pour les littéraux de chaîne `big` (comme `big"0.3"`), pourrait ne pas être intuitive, en raison du fait que `@big_str` est une macro. Consultez la documentation de `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` pour plus de détails.


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

Pour rendre les formules et expressions numériques courantes plus claires, Julia permet aux variables d'être immédiatement précédées d'un littéral numérique, impliquant une multiplication. Cela rend l'écriture des expressions polynomiales beaucoup plus propre :

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

Cela rend également l'écriture des fonctions exponentielles plus élégante :

```jldoctest numeric-coefficients
julia> 2^2x
64
```

La priorité des coefficients littéraux numériques est légèrement inférieure à celle des opérateurs unaires tels que la négation. Ainsi, `-2x` est analysé comme `(-2) * x` et `√2x` est analysé comme `(√2) * x`. Cependant, les coefficients littéraux numériques s'analysent de manière similaire aux opérateurs unaires lorsqu'ils sont combinés avec l'exponentiation. Par exemple, `2^3x` est analysé comme `2^(3x)`, et `2x^3` est analysé comme `2*(x^3)`.

Les littéraux numériques fonctionnent également comme coefficients pour les expressions entre parenthèses :

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    La priorité des coefficients littéraux numériques utilisés pour la multiplication implicite est plus élevée que celle des autres opérateurs binaires tels que la multiplication (`*`) et la division (`/`, `\`, et `//`). Cela signifie, par exemple, que `1 / 2im` est égal à `-0.5im` et que `6 // 2(2 + 1)` est égal à `1 // 1`.


De plus, les expressions entre parenthèses peuvent être utilisées comme coefficients pour des variables, impliquant la multiplication de l'expression par la variable :

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

Ni la juxtaposition de deux expressions entre parenthèses, ni le placement d'une variable avant une expression entre parenthèses, ne peuvent cependant être utilisés pour impliquer une multiplication :

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

Les deux expressions sont interprétées comme une application de fonction : toute expression qui n'est pas un littéral numérique, lorsqu'elle est immédiatement suivie d'une parenthèse, est interprétée comme une fonction appliquée aux valeurs dans les parenthèses (voir [Functions](@ref) pour en savoir plus sur les fonctions). Ainsi, dans ces deux cas, une erreur se produit puisque la valeur de gauche n'est pas une fonction.

Les améliorations syntaxiques ci-dessus réduisent considérablement le bruit visuel engendré lors de l'écriture de formules mathématiques courantes. Notez qu'aucun espace blanc ne doit se trouver entre un coefficient littéral numérique et l'identifiant ou l'expression entre parenthèses qu'il multiplie.

### Syntax Conflicts

La syntaxe des coefficients littéraux juxtaposés peut entrer en conflit avec certaines syntaxes de littéraux numériques : littéraux entiers hexadécimaux, octaux et binaires, ainsi que la notation d'ingénierie pour les littéraux à virgule flottante. Voici quelques situations où des conflits syntaxiques se produisent :

  * L'expression littérale entière hexadécimale `0xff` pourrait être interprétée comme le littéral numérique `0` multiplié par la variable `xff`. Des ambiguïtés similaires se posent avec des littéraux octaux et binaires comme `0o777` ou `0b01001010`.
  * L'expression littérale à virgule flottante `1e10` pourrait être interprétée comme le littéral numérique `1` multiplié par la variable `e10`, et de même pour la forme équivalente `E`.
  * L'expression littérale en virgule flottante 32 bits `1.5f22` pourrait être interprétée comme le littéral numérique `1.5` multiplié par la variable `f22`.

Dans tous les cas, l'ambiguïté est résolue en faveur de l'interprétation en tant que littéraux numériques :

  * Les expressions commençant par `0x`/`0o`/`0b` sont toujours des littéraux hexadécimaux/octaux/binaires.
  * Les expressions commençant par un littéral numérique suivi de `e` ou `E` sont toujours des littéraux à virgule flottante.
  * Les expressions commençant par un littéral numérique suivi de `f` sont toujours des littéraux de point flottant 32 bits.

Contrairement à `E`, qui est équivalent à `e` dans les littéraux numériques pour des raisons historiques, `F` est juste une autre lettre et ne se comporte pas comme `f` dans les littéraux numériques. Ainsi, les expressions commençant par un littéral numérique suivi de `F` sont interprétées comme le littéral numérique multiplié par une variable, ce qui signifie que, par exemple, `1.5F22` est égal à `1.5 * F22`.

## Literal zero and one

Julia fournit des fonctions qui renvoient 0 et 1 littéraux correspondant à un type spécifié ou au type d'une variable donnée.

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

Ces fonctions sont utiles dans [Numeric Comparisons](@ref) pour éviter les frais généraux dus à des [type conversion](@ref conversion-and-promotion) inutiles.

Exemples :

```jldoctest
julia> zero(Float32)
0.0f0

julia> zero(1.0)
0.0

julia> one(Int32)
1

julia> one(BigFloat)
1.0
```

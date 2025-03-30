# Mathematics

## [Mathematical Operators](@id math-ops)

```@docs
Base.:-(::Any)
Base.:(+)
Base.:-(::Any, ::Any)
Base.:*(::Any, ::Any...)
Base.:(/)
Base.:\(::Any, ::Any)
Base.:^(::Number, ::Number)
Base.fma
Base.muladd
Base.inv(::Number)
Base.div
Base.div(::Any, ::Any, ::RoundingMode)
Base.fld
Base.cld
Base.mod
Base.rem
Base.rem(::Any, ::Any, ::RoundingMode)
Base.rem2pi
Base.Math.mod2pi
Base.divrem
Base.fldmod
Base.fld1
Base.mod1
Base.fldmod1
Base.:(//)
Base.rationalize
Base.numerator
Base.denominator
Base.:(<<)
Base.:(>>)
Base.:(>>>)
Base.bitrotate
Base.:(:)
Base.range
Base.OneTo
Base.StepRangeLen
Base.logrange
Base.LogRange
Base.:(==)
Base.:(!=)
Base.:(!==)
Base.:(<)
Base.:(<=)
Base.:(>)
Base.:(>=)
Base.cmp
Base.:(~)
Base.:(&)
Base.:(|)
Base.xor
Base.nand
Base.nor
Base.:(!)
&&
||
```

## Mathematical Functions

```@docs
Base.isapprox
Base.sin(::Number)
Base.cos(::Number)
Base.sincos(::Float64)
Base.tan(::Number)
Base.Math.sind
Base.Math.cosd
Base.Math.tand
Base.Math.sincosd
Base.Math.sinpi
Base.Math.cospi
Base.Math.tanpi
Base.Math.sincospi
Base.sinh(::Number)
Base.cosh(::Number)
Base.tanh(::Number)
Base.asin(::Number)
Base.acos(::Number)
Base.atan(::Number)
Base.Math.asind
Base.Math.acosd
Base.Math.atand
Base.Math.sec(::Number)
Base.Math.csc(::Number)
Base.Math.cot(::Number)
Base.Math.secd
Base.Math.cscd
Base.Math.cotd
Base.Math.asec(::Number)
Base.Math.acsc(::Number)
Base.Math.acot(::Number)
Base.Math.asecd
Base.Math.acscd
Base.Math.acotd
Base.Math.sech(::Number)
Base.Math.csch(::Number)
Base.Math.coth(::Number)
Base.asinh(::Number)
Base.acosh(::Number)
Base.atanh(::Number)
Base.Math.asech(::Number)
Base.Math.acsch(::Number)
Base.Math.acoth(::Number)
Base.Math.sinc
Base.Math.cosc
Base.Math.deg2rad
Base.Math.rad2deg
Base.Math.hypot
Base.log(::Number)
Base.log(::Number, ::Number)
Base.log2
Base.log10
Base.log1p
Base.Math.frexp
Base.exp(::Float64)
Base.exp2
Base.exp10
Base.Math.ldexp
Base.Math.modf
Base.expm1
Base.round
Base.Rounding.RoundingMode
Base.Rounding.RoundNearest
Base.Rounding.RoundNearestTiesAway
Base.Rounding.RoundNearestTiesUp
Base.Rounding.RoundToZero
Base.Rounding.RoundFromZero
Base.Rounding.RoundUp
Base.Rounding.RoundDown
Base.round(::Complex{<: AbstractFloat}, ::RoundingMode, ::RoundingMode)
Base.ceil
Base.floor
Base.trunc
Base.unsafe_trunc
Base.min
Base.max
Base.minmax
Base.Math.clamp
Base.Math.clamp!
Base.abs
Base.Checked
Base.Checked.checked_abs
Base.Checked.checked_neg
Base.Checked.checked_add
Base.Checked.checked_sub
Base.Checked.checked_mul
Base.Checked.checked_div
Base.Checked.checked_rem
Base.Checked.checked_fld
Base.Checked.checked_mod
Base.Checked.checked_cld
Base.Checked.checked_pow
Base.Checked.add_with_overflow
Base.Checked.sub_with_overflow
Base.Checked.mul_with_overflow
Base.abs2
Base.copysign
Base.sign
Base.signbit
Base.flipsign
Base.sqrt(::Number)
Base.isqrt
Base.Math.cbrt(::AbstractFloat)
Base.real
Base.imag
Base.reim
Base.conj
Base.angle
Base.cis
Base.cispi
Base.binomial
Base.factorial
Base.gcd
Base.lcm
Base.gcdx
Base.ispow2
Base.nextpow
Base.prevpow
Base.nextprod
Base.invmod
Base.powermod
Base.ndigits
Base.add_sum
Base.widemul
Base.Math.evalpoly
Base.Math.@evalpoly
Base.FastMath.@fastmath
```

## Customizable binary operators

일부 유니코드 문자는 중위 표기법을 지원하는 새로운 이진 연산자를 정의하는 데 사용할 수 있습니다. 예를 들어 `⊗(x,y) = kron(x,y)`는 `⊗` (오템스) 함수를 크로네커 곱으로 정의하며, 이를 중위 구문을 사용하여 이진 연산자로 호출할 수 있습니다: `C = A ⊗ B`와 일반적인 접두사 구문 `C = ⊗(A,B)`로도 호출할 수 있습니다.

다른 기호로는 \odot `⊙`와 \oplus `⊕`가 이러한 확장을 지원합니다.

완전한 목록은 파서 코드에 있습니다: [https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm)

`*`와 같은 우선순위로 파싱되는 기호에는 `* / ÷ % & ⋅ ∘ × |\\| ∩ ∧ ⊗ ⊘ ⊙ ⊚ ⊛ ⊠ ⊡ ⊓ ∗ ∙ ∤ ⅋ ≀ ⊼ ⋄ ⋆ ⋇ ⋉ ⋊ ⋋ ⋌ ⋏ ⋒ ⟑ ⦸ ⦼ ⦾ ⦿ ⧶ ⧷ ⨇ ⨰ ⨱ ⨲ ⨳ ⨴ ⨵ ⨶ ⨷ ⨸ ⨻ ⨼ ⨽ ⩀ ⩃ ⩄ ⩋ ⩍ ⩎ ⩑ ⩓ ⩕ ⩘ ⩚ ⩜ ⩞ ⩟ ⩠ ⫛ ⊍ ▷ ⨝ ⟕ ⟖ ⟗`가 포함되며, `+`와 같은 우선순위로 파싱되는 기호에는 `+ - |\|| ⊕ ⊖ ⊞ ⊟ |++| ∪ ∨ ⊔ ± ∓ ∔ ∸ ≏ ⊎ ⊻ ⊽ ⋎ ⋓ ⟇ ⧺ ⧻ ⨈ ⨢ ⨣ ⨤ ⨥ ⨦ ⨧ ⨨ ⨩ ⨪ ⨫ ⨬ ⨭ ⨮ ⨹ ⨺ ⩁ ⩂ ⩅ ⩊ ⩌ ⩏ ⩐ ⩒ ⩔ ⩖ ⩗ ⩛ ⩝ ⩡ ⩢ ⩣`가 포함됩니다. 화살표, 비교 및 거듭제곱과 관련된 많은 다른 기호들도 있습니다.

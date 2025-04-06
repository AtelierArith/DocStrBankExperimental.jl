# [Numbers](@id lib-numbers)

## Standard Numeric Types

`Base`의 `Number`의 모든 하위 유형에 대한 유형 트리는 아래에 표시됩니다. 추상 유형은 표시되었으며, 나머지는 구체적인 유형입니다.

```
Number  (Abstract Type)
├─ Complex
└─ Real  (Abstract Type)
   ├─ AbstractFloat  (Abstract Type)
   │  ├─ Float16
   │  ├─ Float32
   │  ├─ Float64
   │  └─ BigFloat
   ├─ Integer  (Abstract Type)
   │  ├─ Bool
   │  ├─ Signed  (Abstract Type)
   │  │  ├─ Int8
   │  │  ├─ Int16
   │  │  ├─ Int32
   │  │  ├─ Int64
   │  │  ├─ Int128
   │  │  └─ BigInt
   │  └─ Unsigned  (Abstract Type)
   │     ├─ UInt8
   │     ├─ UInt16
   │     ├─ UInt32
   │     ├─ UInt64
   │     └─ UInt128
   ├─ Rational
   └─ AbstractIrrational  (Abstract Type)
      └─ Irrational
```

### Abstract number types

```@docs
Core.Number
Core.Real
Core.AbstractFloat
Core.Integer
Core.Signed
Core.Unsigned
Base.AbstractIrrational
```

### Concrete number types

```@docs
Core.Float16
Core.Float32
Core.Float64
Base.BigFloat
Core.Bool
Core.Int8
Core.UInt8
Core.Int16
Core.UInt16
Core.Int32
Core.UInt32
Core.Int64
Core.UInt64
Core.Int128
Core.UInt128
Base.Int
Base.UInt
Base.BigInt
Base.Complex
Base.Rational
Base.Irrational
```

## Data Formats

```@docs
Base.digits
Base.digits!
Base.bitstring
Base.parse
Base.tryparse
Base.big
Base.signed
Base.unsigned
Base.float(::Any)
Base.Math.significand
Base.Math.exponent
Base.complex(::Complex)
Base.bswap
Base.hex2bytes
Base.hex2bytes!
Base.bytes2hex
```

## General Number Functions and Constants

```@docs
Base.one
Base.oneunit
Base.zero
Base.im
Base.MathConstants.pi
Base.MathConstants.ℯ
Base.MathConstants.catalan
Base.MathConstants.eulergamma
Base.MathConstants.golden
Base.Inf
Base.Inf64
Base.Inf32
Base.Inf16
Base.NaN
Base.NaN64
Base.NaN32
Base.NaN16
Base.issubnormal
Base.isfinite
Base.isinf
Base.isnan
Base.iszero
Base.isone
Base.nextfloat
Base.prevfloat
Base.isinteger
Base.isreal
Core.Float32(::Any)
Core.Float64(::Any)
Base.Rounding.rounding
Base.Rounding.setrounding(::Type, ::Any)
Base.Rounding.setrounding(::Function, ::Type, ::RoundingMode)
Base.Rounding.get_zero_subnormals
Base.Rounding.set_zero_subnormals
```

### Integers

```@docs
Base.count_ones
Base.count_zeros
Base.leading_zeros
Base.leading_ones
Base.trailing_zeros
Base.trailing_ones
Base.isodd
Base.iseven
Base.@int128_str
Base.@uint128_str
```

## [BigFloats and BigInts](@id BigFloats-and-BigInts)

[`BigFloat`](@ref) 및 [`BigInt`](@ref) 유형은 각각 임의 정밀도 부동 소수점 및 정수 산술을 구현합니다. `4d61726b646f776e2e436f64652822222c2022426967466c6f61742229_40726566`의 경우 [GNU MPFR library](https://www.mpfr.org/)가 사용되며, `4d61726b646f776e2e436f64652822222c2022426967496e742229_40726566`의 경우 [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org)가 사용됩니다.

```@docs
Base.MPFR.BigFloat(::Any, rounding::RoundingMode)
Base.precision
Base.MPFR.setprecision
Base.GMP.BigInt(::Any)
Base.@big_str
```

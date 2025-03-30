# SHA

```@meta
DocTestSetup = quote
    using SHA
    using InteractiveUtils
end
```

## SHA functions

使用非常简单：

```jldoctest
julia> using SHA

julia> bytes2hex(sha256("test"))
"9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

每个导出的函数（在撰写本文时，已实现 SHA-1、SHA-2 224、256、384 和 512，以及 SHA-3 224、256、384 和 512 函数）接受一个 `AbstractVector{UInt8}`、一个 `AbstractString` 或一个 `IO` 对象。这使得对文件进行校验和计算变得简单：

```julia
shell> cat /tmp/test.txt
test
julia> using SHA

julia> open("/tmp/test.txt") do f
           sha2_256(f)
       end
32-element Array{UInt8,1}:
 0x9f
 0x86
 0xd0
 0x81
 0x88
 0x4c
 0x7d
 0x65
    ⋮
 0x5d
 0x6c
 0x15
 0xb0
 0xf0
 0x0a
 0x08
```

### All SHA functions

由于口语中将 `sha256` 用作 `sha2_256` 的代称，因此提供了便利函数，将 `shaxxx()` 函数调用映射到 `sha2_xxx()`。对于 SHA-3，没有这样的口语用法，用户必须使用完整的 `sha3_xxx()` 名称。

`shaxxx()` 接受 `AbstractString` 和数组类型对象（`NTuple` 和 `Array`），其元素类型为 `UInt8`。

**SHA-1**

```@docs
sha1
```

**SHA-2**

```@docs
sha224
sha256
sha384
sha512
sha2_224
sha2_256
sha2_384
sha2_512
```

**SHA-3**

```@docs
sha3_224
sha3_256
sha3_384
sha3_512
```

## Working with context

要从多个项目创建哈希，可以使用 `SHAX_XXX_CTX()` 类型来创建一个有状态的哈希对象，该对象可以通过 `update!` 更新，并通过 `digest!` 完成。

```jldoctest
julia> using SHA

julia> ctx = SHA2_256_CTX()
SHA2 256-bit hash state

julia> update!(ctx, b"some data")
0x0000000000000009

julia> update!(ctx, b"some more data")
0x0000000000000017

julia> digest!(ctx)
32-element Vector{UInt8}:
 0xbe
 0xcf
 0x23
 0xda
 0xaf
 0x02
 0xf7
 0xa3
 0x57
 0x92
    ⋮
 0x89
 0x4f
 0x59
 0xd8
 0xb3
 0xb4
 0x81
 0x8b
 0xc5
```

请注意，在撰写本文时，SHA3 代码尚未优化，因此其速度大约比 SHA2 慢一个数量级。

```@docs
update!
digest!
```

### All SHA context types

**SHA-1**

```@docs
SHA1_CTX
```

**SHA-2**

便利类型也提供，其中 `SHAXXX_CTX` 是 `SHA2_XXX_CTX` 的类型别名。

```@docs
SHA224_CTX
SHA256_CTX
SHA384_CTX
SHA512_CTX
SHA2_224_CTX
SHA2_256_CTX
SHA2_384_CTX
SHA2_512_CTX
```

**SHA-3**

```@docs
SHA3_224_CTX
SHA3_256_CTX
SHA3_384_CTX
SHA3_512_CTX
```

## HMAC functions

```jldoctest
julia> using SHA

julia> key = collect(codeunits("key_string"))
10-element Vector{UInt8}:
 0x6b
 0x65
 0x79
 0x5f
 0x73
 0x74
 0x72
 0x69
 0x6e
 0x67

julia> bytes2hex(hmac_sha3_256(key, "test-message"))
"bc49a6f2aa29b27ee5ed1e944edd7f3d153e8a01535d98b5e24dac9a589a6248"
```

要从多个项目创建哈希，可以使用 `HMAC_CTX()` 类型来创建一个有状态的哈希对象，该对象可以通过 `update!` 更新，并通过 `digest!` 完成。

```jldoctest
julia> using SHA

julia> key = collect(codeunits("key_string"))
10-element Vector{UInt8}:
 0x6b
 0x65
 0x79
 0x5f
 0x73
 0x74
 0x72
 0x69
 0x6e
 0x67

julia> ctx = HMAC_CTX(SHA3_256_CTX(), key);

julia> update!(ctx, b"test-")
0x0000000000000000000000000000008d

julia> update!(ctx, b"message")
0x00000000000000000000000000000094

julia> bytes2hex(digest!(ctx))
"bc49a6f2aa29b27ee5ed1e944edd7f3d153e8a01535d98b5e24dac9a589a6248"
```

### All HMAC functions

**HMAC 上下文类型**

```@docs
HMAC_CTX
```

**SHA-1**

```@docs
hmac_sha1
```

**SHA-2**

```@docs
hmac_sha224
hmac_sha256
hmac_sha384
hmac_sha512
hmac_sha2_224
hmac_sha2_256
hmac_sha2_384
hmac_sha2_512
```

**SHA-3**

```@docs
hmac_sha3_224
hmac_sha3_256
hmac_sha3_384
hmac_sha3_512
```

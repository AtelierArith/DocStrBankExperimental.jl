```
版本号
```

版本号类型遵循[语义版本控制 (semver)](https://semver.org/)的规范，由主版本号、次版本号和修订号的数字值组成，后面跟有预发布和构建的字母数字注释。

`VersionNumber` 对象可以与所有标准比较运算符（`==`、`<`、`<=` 等）进行比较，结果遵循 semver 规则。

`VersionNumber` 具有以下公共字段：

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

另请参见 [`@v_str`](@ref)，以高效地从 semver 格式的字面字符串构造 `VersionNumber` 对象，[`VERSION`](@ref) 获取 Julia 本身的 `VersionNumber`，以及手册中的 [版本号字面量](@ref man-version-number-literals)。

# 示例

```jldoctest
julia> a = VersionNumber(1, 2, 3)
v"1.2.3"

julia> a >= v"1.2"
true

julia> b = VersionNumber("2.0.1-rc1")
v"2.0.1-rc1"

julia> b >= v"2.0.1"
false
```

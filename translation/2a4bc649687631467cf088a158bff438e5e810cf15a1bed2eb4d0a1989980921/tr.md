```
VersionNumber
```

Sürüm numarası türü, [anlamlı sürümleme (semver)](https://semver.org/) spesifikasyonlarını takip eder ve ana, alt ve yaman sayısal değerlerden oluşur; ardından ön sürüm ve yapı alfanümerik notasyonlar gelir.

`VersionNumber` nesneleri, tüm standart karşılaştırma operatörleri (`==`, `<`, `<=`, vb.) ile karşılaştırılabilir ve sonuç semver kurallarını takip eder.

`VersionNumber` aşağıdaki kamu alanlarına sahiptir:

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

Ayrıca, semver formatındaki literal dizelerden `VersionNumber` nesnelerini verimli bir şekilde oluşturmak için [`@v_str`](@ref), Julia'nın `VersionNumber`'ı için [`VERSION`](@ref) ve kılavuzda [Sürüm Numarası Literalleri](@ref man-version-number-literals) ile ilgili bilgileri de inceleyebilirsiniz.

# Örnekler

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

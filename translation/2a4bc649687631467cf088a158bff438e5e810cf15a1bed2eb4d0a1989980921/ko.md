```
VersionNumber
```

버전 번호 유형으로, [시맨틱 버전 관리(semver)](https://semver.org/)의 사양을 따르며, 주요, 부, 패치 숫자 값으로 구성되고, 그 뒤에 사전 릴리스 및 빌드 알파벳 주석이 옵니다.

`VersionNumber` 객체는 모든 표준 비교 연산자(`==`, `<`, `<=` 등)와 비교할 수 있으며, 결과는 semver 규칙을 따릅니다.

`VersionNumber`는 다음과 같은 공개 필드를 가지고 있습니다:

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

또한 [`@v_str`](@ref)를 참조하여 semver 형식의 리터럴 문자열로부터 `VersionNumber` 객체를 효율적으로 생성하고, [`VERSION`](@ref)를 통해 Julia 자체의 `VersionNumber`를 확인하며, 매뉴얼의 [버전 번호 리터럴](@ref man-version-number-literals)도 참고하세요.

# 예제

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

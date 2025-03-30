```
reverse(s::AbstractString) -> AbstractString
```

문자열을 뒤집습니다. 기술적으로 이 함수는 문자열의 코드 포인트를 뒤집으며, 주된 용도는 뒤집힌 순서의 문자열 처리, 특히 뒤집힌 정규 표현식 검색을 위한 것입니다. `s`의 인덱스를 `reverse(s)`의 인덱스로 변환하고 그 반대의 경우도 처리하기 위해 [`reverseind`](@ref)를 참조하십시오. 또한 코드 포인트가 아닌 사용자 가시 "문자"(그래프)에 대해 작업하기 위해 `Unicode` 모듈의 `graphemes`를 참조하십시오. 복사 없이 역순 반복을 위해 [`Iterators.reverse`](@ref)도 참조하십시오. 사용자 정의 문자열 유형은 `reverse` 함수를 직접 구현해야 하며, 일반적으로 동일한 유형과 인코딩의 문자열을 반환해야 합니다. 다른 인코딩의 문자열을 반환하는 경우, `s[reverseind(s,i)] == reverse(s)[i]`를 만족시키기 위해 해당 문자열 유형에 대해 `reverseind`도 재정의해야 합니다.

# 예제

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! note
    아래 예제는 서로 다른 시스템에서 다르게 렌더링될 수 있습니다. 주석은 어떻게 렌더링되어야 하는지를 나타냅니다.


결합 문자는 놀라운 결과를 초래할 수 있습니다:

```jldoctest
julia> reverse("ax̂e") # 모자는 입력에서는 x 위에, 출력에서는 e 위에 있습니다.
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # 그래프를 뒤집습니다; 모자는 입력과 출력 모두에서 x 위에 있습니다.
"ex̂a"
```

```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

`data`를 스트림 `io`에 TOML 구문으로 작성합니다. 키워드 인수 `sorted`가 `true`로 설정되면, 키워드 인수 `by`에 의해 주어진 함수에 따라 테이블을 정렬합니다. 키워드 인수 `inline_tables`가 주어지면, "inline"으로 출력해야 하는 테이블의 집합이어야 합니다.

다음 데이터 유형이 지원됩니다: `AbstractDict`, `AbstractVector`, `AbstractString`, `Integer`, `AbstractFloat`, `Bool`, `Dates.DateTime`, `Dates.Time`, `Dates.Date`. 정수와 부동 소수점 수는 각각 `Float64`와 `Int64`로 변환 가능해야 합니다. 다른 데이터 유형의 경우, 데이터 유형을 받아 지원되는 유형의 값을 반환하는 `to_toml` 함수를 전달하십시오.

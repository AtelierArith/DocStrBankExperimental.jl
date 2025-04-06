```
@s_str -> SubstitutionString
```

정규 표현식 치환에 사용되는 치환 문자열을 생성합니다. 문자열 내에서 `\N` 형식의 시퀀스는 정규 표현식의 N번째 캡처 그룹을 참조하고, `\g<groupname>`은 이름이 `groupname`인 명명된 캡처 그룹을 참조합니다.

# 예제

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```

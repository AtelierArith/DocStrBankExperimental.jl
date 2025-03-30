```
@b_str
```

문자열 구문을 사용하여 불변 바이트(`UInt8`) 벡터를 만듭니다.

# 예제

```jldoctest
julia> v = b"12\x01\x02"
4-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x01
 0x02

julia> v[2]
0x32
```

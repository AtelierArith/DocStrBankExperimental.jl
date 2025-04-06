```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

벡터의 모든 값이 ASCII 문자 집합(0x00에서 0x7f)에 속하는지 테스트합니다. 이 함수는 빠른 ASCII 검사가 필요한 다른 문자열 구현에서 사용하기 위해 설계되었습니다.

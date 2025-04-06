```
LAPACKException
```

일반 LAPACK 예외는 [LAPACK 함수](@ref man-linalg-lapack-functions)에 대한 직접 호출 중 또는 LAPACK 함수를 내부적으로 사용하는 다른 함수에 대한 호출 중에 발생하며, 이러한 함수는 전문화된 오류 처리가 부족합니다. `info` 필드는 기본 오류에 대한 추가 정보를 포함하며 호출된 LAPACK 함수에 따라 다릅니다.

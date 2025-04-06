```
contains(needle)
```

인수에 `needle`이 포함되어 있는지 확인하는 함수를 만듭니다. 즉, `haystack -> contains(haystack, needle)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix2{typeof(contains)}` 유형이며, 특수화된 메서드를 구현하는 데 사용할 수 있습니다.

```
readdlm(source, delim::AbstractChar, eol::AbstractChar; options...)
```

모든 데이터가 숫자일 경우 결과는 숫자 배열이 됩니다. 일부 요소가 숫자로 파싱될 수 없는 경우 숫자와 문자열의 이질적인 배열이 반환됩니다.

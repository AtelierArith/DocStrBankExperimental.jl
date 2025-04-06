```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

`AbstractTestSet`의 결과를 형식화된 테이블로 출력합니다.

`depth_pad`는 모든 출력 앞에 추가해야 할 패딩의 양을 나타냅니다.

`Test.finish` 내부에서 호출되며, `finish`된 테스트 세트가 가장 상위 테스트 세트인 경우에 해당합니다.

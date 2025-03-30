```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

모듈의 공용 전역 변수에 대한 정보를 제공하는 마크다운 테이블을 반환하며, 선택적으로 `pattern`과 일치하는 변수로 제한할 수 있습니다.

메모리 소비 추정치는 객체의 내부 구조 크기에 대한 대략적인 하한입니다.

  * `all` : 모듈에 정의된 비공개 객체, 사용 중단된 객체 및 컴파일러 생성 객체도 나열합니다.
  * `imported` : 다른 모듈에서 명시적으로 가져온 객체도 나열합니다.
  * `recursive` : 하위 모듈의 객체를 재귀적으로 포함하며, 각 모듈에서 동일한 설정을 준수합니다.
  * `sortby` : 결과를 정렬할 열입니다. 옵션은 `:name` (기본값), `:size`, 및 `:summary`입니다.
  * `minsize` : 크기가 최소 `minsize` 바이트인 객체만 포함합니다. 기본값은 `0`입니다.

`varinfo`의 출력은 표시 목적으로만 사용됩니다. 모듈에 정의된 기호의 배열을 가져오려면 [`names`](@ref)를 참조하십시오. 이는 보다 일반적인 조작에 적합합니다.

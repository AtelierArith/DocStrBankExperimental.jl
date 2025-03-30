```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

텍스트 콘솔에서 가독성을 최적화한 형식의 로거로, 예를 들어 Julia REPL과의 대화형 작업에 적합합니다.

`min_level`보다 낮은 로그 수준은 필터링됩니다.

메시지 형식은 키워드 인수를 설정하여 제어할 수 있습니다:

  * `meta_formatter`는 로그 이벤트 메타데이터 `(level, _module, group, id, file, line)`를 받아 색상(출력 스타일에 전달될 색상), 접두사 및 접미사를 로그 메시지에 반환하는 함수입니다. 기본값은 로그 수준으로 접두사를 붙이고 모듈, 파일 및 줄 위치를 포함하는 접미사를 붙이는 것입니다.
  * `show_limited`는 형식화 중에 `:limit` `IOContext` 키를 설정하여 큰 데이터 구조의 출력을 화면에 맞게 제한합니다.
  * `right_justify`는 로그 메타데이터가 오른쪽 정렬되는 정수 열입니다. 기본값은 0(메타데이터가 별도의 줄에 표시됨)입니다.

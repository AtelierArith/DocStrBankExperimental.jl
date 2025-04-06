```
TextDisplay(io::IO)
```

`TextDisplay <: AbstractDisplay`를 반환하며, 이는 주어진 I/O 스트림에 텍스트 표현을 작성하여 모든 객체를 text/plain MIME 유형으로 표시합니다(기본값). (이것이 Julia REPL에서 객체가 출력되는 방식입니다.)

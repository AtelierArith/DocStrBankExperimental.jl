```
RadioMenu
```

사용자가 목록에서 단일 옵션을 선택할 수 있는 메뉴입니다.

# 샘플 출력

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
좋아하는 과일을 선택하세요:
^  포도
   딸기
 > 블루베리
v  복숭아
당신의 좋아하는 과일은 블루베리입니다!
```

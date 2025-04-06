```
MultiSelectMenu
```

사용자가 목록에서 여러 옵션을 선택할 수 있는 메뉴입니다.

# 샘플 출력

```julia-repl
julia> request(MultiSelectMenu(options))
좋아하는 과일을 선택하세요:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] 사과
 > [X] 오렌지
   [X] 포도
   [ ] 딸기
   [ ] 블루베리
   [X] 복숭아
   [ ] 레몬
   [ ] 라임
당신이 좋아하는 과일:
  - 오렌지
  - 포도
  - 복숭아
```

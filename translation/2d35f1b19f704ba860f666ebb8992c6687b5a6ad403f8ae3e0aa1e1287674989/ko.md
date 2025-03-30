```
@nextract N esym isym
```

`N` 개의 변수를 생성하여 `esym_1`, `esym_2`, ..., `esym_N`로 `isym`에서 값을 추출합니다. `isym`은 `Symbol` 또는 익명 함수 표현식일 수 있습니다.

`@nextract 2 x y`는 다음을 생성합니다.

```
x_1 = y[1]
x_2 = y[2]
```

반면에 `@nextract 3 x d->y[2d-1]`는 다음을 생성합니다.

```
x_1 = y[1]
x_2 = y[3]
x_3 = y[5]
```

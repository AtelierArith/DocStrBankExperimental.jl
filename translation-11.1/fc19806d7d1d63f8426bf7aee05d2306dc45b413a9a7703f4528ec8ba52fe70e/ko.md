```
@nif N 조건식 expr
@nif N 조건식 expr elseexpr
```

`if ... elseif ... else ... end` 문장의 시퀀스를 생성합니다. 예를 들어:

```
@nif 3 d->(i_d >= size(A,d)) d->(error("차원 ", d, " 너무 큼")) d->println("모두 OK")
```

다음과 같이 생성됩니다:

```
if i_1 > size(A, 1)
    error("차원 ", 1, " 너무 큼")
elseif i_2 > size(A, 2)
    error("차원 ", 2, " 너무 큼")
else
    println("모두 OK")
end
```

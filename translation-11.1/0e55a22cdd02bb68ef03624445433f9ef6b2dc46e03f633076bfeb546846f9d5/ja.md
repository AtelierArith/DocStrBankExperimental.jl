```
default(p::Period) -> Period
```

入力されたPeriodに対して、Year、Month、Dayの場合は`T(1)`を、Hour、Minute、Second、Millisecondの場合は`T(0)`を返すことで、適切な「デフォルト」値を返します。

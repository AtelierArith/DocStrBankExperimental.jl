```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering`는 `data`의 인덱스에 대해 `i`가 `j`보다 작으면 `data[i]`가 `data[j]`보다 작다는 것을 의미합니다. `order`에 따라 `data[i]`와 `data[j]`가 같을 경우, `i`와 `j`는 숫자 값으로 비교됩니다.

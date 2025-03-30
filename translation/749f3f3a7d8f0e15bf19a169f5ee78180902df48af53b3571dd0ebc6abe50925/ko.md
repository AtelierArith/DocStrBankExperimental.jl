```
ReverseOrdering(fwd::Ordering=Forward)
```

주문을 반전시키는 래퍼입니다.

주어진 `Ordering` `o`에 대해, 모든 `a`, `b`에 대해 다음이 성립합니다:

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```

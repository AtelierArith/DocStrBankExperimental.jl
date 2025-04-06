```
copy_adjoint!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

행렬 `A`의 요소를 다음과 같이 어드전션을 사용하여 `B`에 효율적으로 복사합니다:

```
B[ir_dest, jr_dest] = adjoint(A)[jr_src, ir_src]
```

요소 `B[ir_dest, jr_dest]`는 덮어쓰여집니다. 또한, 인덱스 범위 매개변수는 `length(ir_dest) == length(jr_src)` 및 `length(jr_dest) == length(ir_src)`를 만족해야 합니다.

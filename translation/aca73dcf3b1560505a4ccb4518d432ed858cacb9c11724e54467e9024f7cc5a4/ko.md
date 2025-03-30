```
unsafe_pointer_to_objref(p::Ptr)
```

`Ptr`를 객체 참조로 변환합니다. 포인터가 유효한 힙에 할당된 Julia 객체를 참조한다고 가정합니다. 그렇지 않은 경우 정의되지 않은 동작이 발생하므로 이 함수는 "안전하지 않다"고 간주되며 주의해서 사용해야 합니다.

또한 [`pointer_from_objref`](@ref)를 참조하십시오.

```
spzeros!(::Type{Tv}, I::AbstractVector{Ti}, J::AbstractVector{Ti}, m::Integer, n::Integer,
         klasttouch::Vector{Ti}, csrrowptr::Vector{Ti}, csrcolval::Vector{Ti},
         [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}]) where {Tv,Ti<:Integer}
```

`spzeros(I, J)`의 부모이자 전문가 드라이버로, 사용자가 중간 객체에 대한 미리 할당된 저장소를 제공할 수 있도록 합니다. 이 메서드는 `spzeros`에 대해 `SparseArrays.sparse!`가 `sparse`에 해당하는 것과 같습니다. 필요한 버퍼 길이에 대한 자세한 내용은 `SparseArrays.sparse!` 문서를 참조하십시오.

!!! compat "Julia 1.10"
    이 메서드는 Julia 버전 1.10 이상이 필요합니다.


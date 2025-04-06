```
as
```

`as`는 `import` 또는 `using`에 의해 범위로 가져온 식별자의 이름을 바꾸기 위해 키워드로 사용되며, 이름 충돌을 피하고 이름을 줄이는 데 목적이 있습니다. (`import` 또는 `using` 문 외부에서는 `as`는 키워드가 아니며 일반 식별자로 사용할 수 있습니다.)

`import LinearAlgebra as LA`는 가져온 `LinearAlgebra` 표준 라이브러리를 `LA`로 범위에 가져옵니다.

`import LinearAlgebra: eigen as eig, cholesky as chol`는 `LinearAlgebra`에서 `eigen` 및 `cholesky` 메서드를 각각 `eig` 및 `chol`로 범위에 가져옵니다.

`as`는 개별 식별자가 범위로 가져올 때만 `using`과 함께 작동합니다. 예를 들어, `using LinearAlgebra: eigen as eig` 또는 `using LinearAlgebra: eigen as eig, cholesky as chol`는 작동하지만, `using LinearAlgebra as LA`는 유효하지 않은 구문입니다. 이는 `LinearAlgebra`에서 *모든* 내보낸 이름을 `LA`로 바꾸는 것이 말이 되지 않기 때문입니다.

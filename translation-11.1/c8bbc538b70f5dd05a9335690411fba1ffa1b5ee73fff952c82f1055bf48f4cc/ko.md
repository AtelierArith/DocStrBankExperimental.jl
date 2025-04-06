```
peel([T,] obj::GitObject)
```

`obj`를 재귀적으로 벗겨서 `T` 유형의 객체를 얻습니다. `T`가 제공되지 않으면 `obj`는 유형이 변경될 때까지 벗겨집니다.

  * `GitTag`는 참조하는 객체로 벗겨집니다.
  * `GitCommit`은 `GitTree`로 벗겨집니다.

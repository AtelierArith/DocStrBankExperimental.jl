```
peel([T,] obj::GitObject)
```

`obj`'yi, `T` türünde bir nesne elde edilene kadar özyinelemeli olarak soyun. Eğer `T` sağlanmamışsa, `obj` türü değişene kadar soyulacaktır.

  * Bir `GitTag`, referans verdiği nesneye soyulacaktır.
  * Bir `GitCommit`, bir `GitTree`'ye soyulacaktır.

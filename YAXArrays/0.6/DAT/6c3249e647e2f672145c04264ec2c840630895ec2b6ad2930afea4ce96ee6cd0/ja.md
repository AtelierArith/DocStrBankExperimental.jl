```
CubeTable()
```

DataCubeオブジェクトを反復可能なテーブルに変換する関数。引数としてリストを取り、`name=cube`式として指定されます。例えば、`CubeTable(data=cube1,country=cube2)`は、`data`と`country`のエントリを持つテーブルを生成します。ここで、`data`は`cube1`の値を含み、`country`は`cube2`の値を含みます。キューブは`mapCube`のようにその軸に沿って一致し、ブロードキャストされます。

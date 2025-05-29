```
isclean(entries::EntryTable; zero_threshold=0.0)
```

エントリが順序付けられ、ユニークであり、振幅がゼロでない場合はtrueを返します。振幅が`zero_threshold`以下の値はゼロと見なされます。

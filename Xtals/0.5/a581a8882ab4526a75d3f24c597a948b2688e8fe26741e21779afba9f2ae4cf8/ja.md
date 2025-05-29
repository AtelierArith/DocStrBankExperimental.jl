```
strip_numbers_from_atom_labels!(crystal)
```

`crystal.atoms`のラベルから数字を削除します。具体的には、`crystal.atoms`内の`atom`について、`atom`に現れる最初の数字を見つけます。この数字とその後のすべての文字を`atom`から削除します。例: C12 –> C Ba12A_3 –> Ba

# 引数

  * `crystal::Crystal`: 結晶構造情報を含む結晶

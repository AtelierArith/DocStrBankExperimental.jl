```
isbinary(blob::GitBlob) -> Bool
```

Bir dosyanın ikili olup olmadığını tahmin etmek için bir sezgi kullanın: NULL baytları aramak ve ilk 8000 bayt arasında yazdırılabilir ile yazdırılamaz karakterlerin makul bir oranını aramak.

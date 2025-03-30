```
trsen!(job, compq, select, T, Q) -> (T, Q, w, s, sep)
trsen!(select, T, Q) -> (T, Q, w, s, sep)
```

Bir matrisin Schur faktörizasyonunu yeniden sıralar ve isteğe bağlı olarak ters koşul sayısını bulur. Eğer `job = N` ise, koşul sayıları bulunmaz. Eğer `job = E` ise, yalnızca bu özdeğerler kümesi için koşul sayısı bulunur. Eğer `job = V` ise, yalnızca invariant alt uzay için koşul sayısı bulunur. Eğer `job = B` ise, hem küme hem de alt uzay için koşul sayıları bulunur. Eğer `compq = V` ise, Schur vektörleri `Q` güncellenir. Eğer `compq = N` ise, Schur vektörleri değiştirilmez. `select`, hangi özdeğerlerin kümede olduğunu belirler. 3-arg yöntemi, 5-arg yöntemini `job = N` ve `compq = V` ile çağırır.

`T`, `Q`, yeniden sıralanmış özdeğerler `w`, özdeğerler kümesinin koşul sayısı `s` ve invariant alt uzayın koşul sayısı `sep` döner.

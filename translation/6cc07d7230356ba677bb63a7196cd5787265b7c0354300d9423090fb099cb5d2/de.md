```
unsafe_convert(T, x)
```

Konvertiere `x` in ein C-Argument vom Typ `T`, wobei der Eingabewert `x` der Rückgabewert von `cconvert(T, ...)` sein muss.

In Fällen, in denen [`convert`](@ref) ein Julia-Objekt in einen `Ptr` umwandeln müsste, sollte diese Funktion verwendet werden, um diese Umwandlung zu definieren und durchzuführen.

Sei vorsichtig, dass eine Julia-Referenz auf `x` so lange existiert, wie das Ergebnis dieser Funktion verwendet wird. Dementsprechend sollte das Argument `x` für diese Funktion niemals ein Ausdruck sein, sondern nur ein Variablenname oder ein Feldverweis. Zum Beispiel ist `x=a.b.c` akzeptabel, aber `x=[a,b,c]` ist es nicht.

Das Präfix `unsafe` bei dieser Funktion weist darauf hin, dass die Verwendung des Ergebnisses dieser Funktion, nachdem das `x`-Argument für diese Funktion nicht mehr für das Programm zugänglich ist, zu undefiniertem Verhalten führen kann, einschließlich Programmkorruption oder Segfaults, zu einem späteren Zeitpunkt.

Siehe auch [`cconvert`](@ref)

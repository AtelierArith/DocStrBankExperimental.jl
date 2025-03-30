```
==(x, y)
```

Genel eşitlik operatörü. [`===`](@ref) ile geri dönmektedir. Eşitlik kavramına sahip tüm türler için, bir örneğin temsil ettiği soyut değere dayalı olarak uygulanmalıdır. Örneğin, tüm sayısal türler sayısal değerlerine göre karşılaştırılır, tür göz ardı edilir. Dizeler, kodlamayı göz ardı ederek karakter dizileri olarak karşılaştırılır. Aynı türdeki koleksiyonlar genellikle anahtar kümelerini karşılaştırır ve eğer bunlar `==` ise, o anahtarlar için değerleri karşılaştırır ve tüm bu çiftler `==` ise true döner. Diğer özellikler genellikle dikkate alınmaz (örneğin, tam tür).

Bu operatör, kayan noktalı sayılar için IEEE semantiğini takip eder: `0.0 == -0.0` ve `NaN != NaN`.

Sonuç `Bool` türündedir, bir operand [`missing`](@ref) olduğunda, bu durumda `missing` döner ([üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic)). Koleksiyonlar genellikle [`all`](@ref) benzeri üç değerli mantığı uygular, herhangi bir operand `missing` değer içeriyorsa ve diğer tüm çiftler eşitse `missing` döner. Her zaman `Bool` sonucu almak için [`isequal`](@ref) veya [`===`](@ref) kullanın.

# Uygulama

Yeni sayısal türler, yeni türün iki argümanı için bu işlevi uygulamalı ve mümkün olduğunda diğer türlerle karşılaştırmayı terfi kuralları aracılığıyla ele almalıdır.

[`isequal`](@ref) `==` ile geri döner, bu nedenle `==` için yeni yöntemler [`Dict`](@ref) türü tarafından anahtarları karşılaştırmak için kullanılacaktır. Eğer türünüz bir sözlük anahtarı olarak kullanılacaksa, bu nedenle [`hash`](@ref) işlevini de uygulamalıdır.

Eğer bir tür `==`, [`isequal`](@ref) ve [`isless`](@ref) tanımlıyorsa, karşılaştırmaların tutarlılığını sağlamak için [`<`](@ref) işlevini de uygulamalıdır.

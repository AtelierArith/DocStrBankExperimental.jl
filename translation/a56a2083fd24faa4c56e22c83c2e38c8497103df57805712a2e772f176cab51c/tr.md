```
codepoint(c::AbstractChar) -> Integer
```

Karakter `c` ile ilgili Unicode kod noktası (bir işaretsiz tam sayı) döndürülür (veya `c` geçerli bir karakteri temsil etmiyorsa bir istisna fırlatılır). `Char` için bu bir `UInt32` değeri, ancak yalnızca Unicode'un bir alt kümesini temsil eden `AbstractChar` türleri farklı boyutta bir tam sayı döndürebilir (örneğin `UInt8`).

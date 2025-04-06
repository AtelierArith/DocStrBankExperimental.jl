```
graphemes(s::AbstractString) -> GraphemeIterator
```

`S` içinde, Unicode UAX #29 tarafından tanımlandığı gibi, dize içindeki genişletilmiş graphemlere karşılık gelen alt dizelerin üzerinde bir yineleyici döndürür. (Kabaca, bunlar kullanıcıların tek karakterler olarak algılayacağı şeylerdir, her ne kadar birden fazla kod noktası içerebilirler; örneğin, bir harf ile bir aksan işareti bir tek graphem olarak kabul edilir.)

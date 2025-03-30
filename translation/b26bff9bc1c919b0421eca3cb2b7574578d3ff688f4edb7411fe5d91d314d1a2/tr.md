```
x::EscapeInfo
```

Kaçış bilgileri için bir ızgara, aşağıdaki özellikleri tutar:

  * `x.Analyzed::Bool`: ızgaranın resmi bir parçası değildir, yalnızca `x`'in analiz edilip edilmediğini gösterir
  * `x.ReturnEscape::Bool`: `x`'in geri dönüş yoluyla çağırana kaçabileceğini gösterir
  * `x.ThrownEscape::BitSet`: `x`'in istisna olarak atılabileceği SSA ifade numaralarını kaydeder:

      * `isempty(x.ThrownEscape)`: `x` bu çağrı çerçevesinde asla atılmayacaktır (en alt)
      * `pc ∈ x.ThrownEscape`: `x` `pc`'deki SSA ifadesinde atılabilir
      * `-1 ∈ x.ThrownEscape`: `x` bu çağrı çerçevesinin herhangi bir noktasında atılabilir (en üst)

    Bu bilgi, istisna yoluyla potansiyel kaçışları yaymak için `escape_exception!` tarafından kullanılacaktır.
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`: `x`'in alanlarına veya dizi elemanlarına taklit edilebilecek tüm olası değerleri tutar:

      * `x.AliasInfo === false` `x`'in alanlarının/elemanlarının henüz analiz edilmediğini gösterir
      * `x.AliasInfo === true` `x`'in alanlarının/elemanlarının analiz edilemeyeceğini gösterir, örneğin `x`'in tipi bilinmiyor veya somut değil ve dolayısıyla alanlarının/elemanlarının kesin olarak bilinmesi mümkün değil
      * `x.AliasInfo::IndexableFields` kesin indeks bilgisi ile `x` nesnesinin alanlarına taklit edilebilecek tüm olası değerleri kaydeder
      * `x.AliasInfo::IndexableElements` kesin indeks bilgisi ile `x` dizisinin elemanlarına taklit edilebilecek tüm olası değerleri kaydeder
      * `x.AliasInfo::Unindexable` kesin indeks bilgisi olmadan `x`'in alanlarına/elemanlarına taklit edilebilecek tüm olası değerleri kaydeder
  * `x.Liveness::BitSet`: `x`'in canlı olması gereken SSA ifade numaralarını kaydeder, örneğin bir çağrı argümanı olarak kullanılmak, bir çağırana geri döndürülmek veya `:foreigncall` için korunmak üzere:

      * `isempty(x.Liveness)`: `x` bu çağrı çerçevesinde asla kullanılmayacaktır (en alt)
      * `0 ∈ x.Liveness` ayrıca, şu anda analiz edilen çağrı çerçevesinin bir çağrı argümanı olduğu özel anlamına gelir (ve dolayısıyla çağırandan hemen görünür).
      * `pc ∈ x.Liveness`: `x` `pc`'deki SSA ifadesinde kullanılabilir
      * `-1 ∈ x.Liveness`: `x` bu çağrı çerçevesinin herhangi bir noktasında kullanılabilir (en üst)

Ortak `EscapeInfo`'ları oluşturmak için yardımcı yapıcılar vardır, örneğin,

  * `NoEscape()`: bu ızgaranın en alt (-benzeri) elemanı, hiçbir yere kaçmayacağı anlamına gelir
  * `AllEscape()`: bu ızgaranın en üst elemanı, her yere kaçacağı anlamına gelir

`analyze_escapes`, bu elemanları en alt seviyeden en üst seviyeye, Julia'nın yerel tür çıkarım rutinine paralel bir yönde geçirecektir. Soyut bir durum, en alt (-benzeri) elemanlarla başlatılacaktır:

  * çağrı argümanları `ArgEscape()` olarak başlatılır, `Liveness` özelliği `0`'ı içerir, bu da çağrı argümanı olarak geçirildiğini ve çağırandan hemen görünür olduğunu gösterir
  * diğer durumlar `NotAnalyzed()` olarak başlatılır, bu, `NoEscape`'den biraz daha düşük olan özel bir ızgara elemanıdır, ancak aynı zamanda henüz analiz edilmediğinden başka bir anlam ifade etmez (bu nedenle resmi olarak ızgaranın bir parçası değildir)

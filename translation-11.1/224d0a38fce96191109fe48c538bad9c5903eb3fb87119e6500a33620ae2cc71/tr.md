```
merge_analysis(repo::GitRepo, anns::Vector{GitAnnotated}) -> analysis, preference
```

Açıklama: `anns` tarafından işaretlenen dallar üzerinde analiz yapın ve hangi koşullar altında birleştirilebileceklerini belirleyin. Örneğin, eğer `anns[1]` sadece `ann[2]`'nin bir atasıysa, `merge_analysis` hızlı bir birleştirme işleminin mümkün olduğunu bildirecektir.

İki çıktı döndürün: `analysis` ve `preference`. `analysis` birkaç olası değere sahiptir: 

  * `MERGE_ANALYSIS_NONE`: `anns` öğelerinin birleştirilmesi mümkün değildir.
  * `MERGE_ANALYSIS_NORMAL`: HEAD ve kullanıcının birleştirmek istediği commit'lerin hepsinin ortak bir atadan ayrıldığı normal bir birleştirme. Bu durumda değişikliklerin çözülmesi gerekir ve çatışmalar meydana gelebilir.
  * `MERGE_ANALYSIS_UP_TO_DATE`: kullanıcının birleştirmek istediği tüm giriş commit'leri HEAD'den ulaşılabilir, bu nedenle birleştirme yapılmasına gerek yoktur.
  * `MERGE_ANALYSIS_FASTFORWARD`: giriş commit'i HEAD'in bir alt kümesidir ve bu nedenle birleştirme yapılmasına gerek yoktur - bunun yerine kullanıcı sadece giriş commit'lerini kontrol edebilir.
  * `MERGE_ANALYSIS_UNBORN`: depo HEAD'i mevcut olmayan bir commit'e işaret ediyor. Birleştirme yapmak mümkün değildir, ancak giriş commit'lerini kontrol etmek mümkün olabilir.

`preference` de birkaç olası değere sahiptir: 

  * `MERGE_PREFERENCE_NONE`: kullanıcının tercihi yoktur.
  * `MERGE_PREFERENCE_NO_FASTFORWARD`: hızlı birleştirme işlemlerine izin vermeyin.
  * `MERGE_PREFERENCE_FASTFORWARD_ONLY`: yalnızca hızlı birleştirme işlemlerine izin verin ve başka bir türüne (çatışmalara neden olabilecek) izin vermeyin. `preference`, depo veya global git yapılandırması aracılığıyla kontrol edilebilir.

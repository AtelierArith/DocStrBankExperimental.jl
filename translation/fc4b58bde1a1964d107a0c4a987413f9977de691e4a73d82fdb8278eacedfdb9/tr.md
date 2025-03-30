```
ZeroPivotException <: Exception
```

Bir matris faktörizasyonu/çözümü, bir pivot (diyagonal) konumunda sıfırla karşılaştığında ve devam edemediğinde fırlatılan istisna. Bu, matrisin tekil olduğu anlamına *gelmeyebilir*: yanıltıcı sıfır pivotları ortadan kaldırmak için değişkenleri yeniden sıralayabilen pivotlu LU gibi farklı bir faktörizasyona geçmek faydalı olabilir. `info` alanı, sıfır pivotlardan (birinden) birinin konumunu gösterir.

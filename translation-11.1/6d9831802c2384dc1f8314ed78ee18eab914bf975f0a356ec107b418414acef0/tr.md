```
var
```

`var"#example#"` sözdizimi, `#example#` geçerli bir Julia tanımlayıcı adı olmasa da, `Symbol("#example#")` adında bir değişkene atıfta bulunur.

Bu, geçerli tanımlayıcıların oluşturulması için farklı kurallara sahip programlama dilleriyle birlikte çalışabilirlik için yararlı olabilir. Örneğin, `R` değişkeni `draw.segments`'e atıfta bulunmak için, Julia kodunuzda `var"draw.segments"` kullanabilirsiniz.

Ayrıca, makro hijyeninden geçmiş veya normalde ayrıştırılamayan değişken adlarını içeren julia kaynak kodunu `show` etmek için de kullanılır.

Bu sözdiziminin ayrıştırıcı desteği gerektirdiğini ve normal bir dize makrosu `@var_str` olarak uygulanmak yerine doğrudan ayrıştırıcı tarafından genişletildiğini unutmayın.

!!! compat "Julia 1.3"
    Bu sözdizimi en az Julia 1.3 gerektirir.


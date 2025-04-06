```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

`N` iç içe döngüleri oluşturur, `itersym` döngü değişkenleri için önek olarak kullanılır. `rangeexpr` bir anonim fonksiyon ifadesi veya basit bir sembol `var` olabilir; bu durumda aralık `axes(var, d)` şeklindedir ve `d` boyutunu temsil eder.

İsteğe bağlı olarak, "ön" ve "son" ifadeleri sağlayabilirsiniz. Bu ifadeler, her döngünün gövdesinde ilk ve son olarak yürütülür. Örneğin:

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

şu şekilde bir çıktı üretecektir:

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

Sadece bir son ifadesi istiyorsanız, ön ifadesi için [`nothing`](@ref) sağlayabilirsiniz. Parantezler ve noktalı virgüller kullanarak çoklu ifade sağlayabilirsiniz.

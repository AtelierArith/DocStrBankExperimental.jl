```
rethrow()
```

Mevcut istisnayı bir `catch` bloğundan yeniden fırlatır. Yeniden fırlatılan istisna, yakalanmamış gibi yayılmaya devam edecektir.

!!! not
    Alternatif form `rethrow(e)`, mevcut geri izleme ile alternatif bir istisna nesnesi `e` ilişkilendirmenize olanak tanır. Ancak bu, hata anındaki program durumunu yanlış yansıttığı için, bunun yerine `throw(e)` kullanarak yeni bir istisna fırlatmanız teşvik edilir. Julia 1.1 ve üzeri sürümlerde, `throw(e)` kullanmak, yığın üzerindeki kök neden istisnasını koruyacaktır; bu, [`current_exceptions`](@ref) bölümünde açıklanmıştır.


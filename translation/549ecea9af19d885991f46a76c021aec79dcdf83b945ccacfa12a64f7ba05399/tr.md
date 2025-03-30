```
Test.Error <: Test.Result
```

Test koşulu bir istisna nedeniyle değerlendirilemedi veya [`Bool`](@ref) dışında bir şeye değerlendirildi. `@test_broken` durumunda, beklenmeyen bir `Pass` `Result`'ın meydana geldiğini belirtmek için kullanılır.

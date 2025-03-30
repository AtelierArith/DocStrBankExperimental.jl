```
as
```

`as`, `import` veya `using` ile kapsamda getirilen bir tanımlayıcıyı yeniden adlandırmak için bir anahtar kelime olarak kullanılır; bu, ad çakışmalarını aşmak ve isimleri kısaltmak amacıyla yapılır. (`import` veya `using` ifadeleri dışında, `as` bir anahtar kelime değildir ve sıradan bir tanımlayıcı olarak kullanılabilir.)

`import LinearAlgebra as LA`, içe aktarılan `LinearAlgebra` standart kütüphanesini `LA` olarak kapsamda getirir.

`import LinearAlgebra: eigen as eig, cholesky as chol`, `LinearAlgebra`'dan `eigen` ve `cholesky` yöntemlerini sırasıyla `eig` ve `chol` olarak kapsamda getirir.

`as`, yalnızca bireysel tanımlayıcılar kapsamda getirildiğinde `using` ile çalışır. Örneğin, `using LinearAlgebra: eigen as eig` veya `using LinearAlgebra: eigen as eig, cholesky as chol` geçerlidir, ancak `using LinearAlgebra as LA` geçersiz bir sözdizimidir, çünkü `LinearAlgebra`'dan *tüm* dışa aktarılan isimleri `LA` olarak yeniden adlandırmak mantıksızdır.

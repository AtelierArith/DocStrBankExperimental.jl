```
;
```

`;` Julia'da birçok C benzeri dilde olduğu gibi, önceki ifadenin sonunu ayırmak için kullanılır.

`;` bir satırın sonunda gerekli değildir, ancak birden fazla ifadeyi tek bir satırda ayırmak veya ifadeleri tek bir ifade haline getirmek için kullanılabilir.

REPL'de bir satırın sonuna `;` eklemek, o ifadenin sonucunun yazdırılmasını engeller.

Fonksiyon bildirimlerinde ve isteğe bağlı olarak çağrılarda, `;` normal argümanları anahtar kelimelerden ayırır.

Dizi literallerinde, noktalı virgülle ayrılmış argümanlar içeriklerini birleştirir. Tek bir `;` ile yapılan bir ayırıcı dikey olarak birleştirir (yani birinci boyut boyunca), `;;` yatay olarak birleştirir (ikinci boyut), `;;;` üçüncü boyut boyunca birleştirir, vb. Böyle bir ayırıcı, kare parantezlerin son konumunda da kullanılabilir ve 1 uzunluğunda ek boyutlar ekler.

Parantezler içinde ilk konumda bir `;` kullanılarak adlandırılmış bir demet oluşturulabilir. Atama işleminin sol tarafında aynı `(; ...)` sözdizimi, özellik ayrıştırması için de kullanılır.

Standart REPL'de, boş bir satıra `;` yazarak kabuk moduna geçiş yapılır.

# Örnekler

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # ; veya bir son virgül olmadan bu x'e atama yapar
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # özellik ayrıştırması kullanarak b ve x değişkenlerini ayarla

julia> b, x
(2, 1)

julia> ; # ; yazıldığında, istem değişir (yerinde) olarak: shell>
shell> echo hello
hello
```

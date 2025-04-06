# Belgelendirme

Fonksiyonlar, yöntemler ve türler, tanımın önüne bir dize yerleştirerek belgelenebilir:

```
"""
# Foo Fonksiyonu
`foo(x)`: `x`'i çok fazla Foo yap.
"""
foo(x) = ...
```

`@doc` makrosu, belgeleri / meta verileri ayarlamak ve almak için doğrudan kullanılabilir. Makro, belgelenmiş nesnenin bir sonraki satırda yer alabilmesi için özel bir ayrıştırma yapar:

```
@doc "blah"
function foo() ...
```

Varsayılan olarak, belgeler Markdown olarak yazılır, ancak ilk argüman olarak herhangi bir nesne kullanılabilir.

## Nesneleri tanımlarından ayrı olarak belgelendirme

Bir nesneyi tanımından önce veya sonra belgeleyebilirsiniz:

```
@doc "foo" function_to_doc
@doc "bar" TypeToDoc
```

Makrolar için sözdizimi `@doc "macro doc" :(Module.@macro)` veya dize makroları için `@doc "macro doc" :(string_macro"")` şeklindedir. Alıntı olmadan `:()` makronun genişlemesi belgelenir.

## Belgeleri Alma

Fonksiyonlar, makrolar ve diğer nesneler için belgeleri şu şekilde alabilirsiniz:

```
@doc foo
@doc @time
@doc md""
```

## Fonksiyonlar & Yöntemler

Bir yöntem tanımının önüne belge yerleştirmek (örneğin `function foo() ...` veya `foo() = ...`) o belirli yöntemin belgelenmesine neden olur, tüm fonksiyonun değil. Yöntem belgeleri, fonksiyon için belgeler sağlamak amacıyla tanımlandıkları sırayla birleştirilir.

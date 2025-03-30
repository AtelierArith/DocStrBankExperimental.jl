```
credential_callback(...) -> Cint
```

Bağlantı protokolüne göre farklı kimlik bilgisi edinme işlevselliği sağlayan bir LibGit2 kimlik bilgisi geri çağırma işlevi. `payload_ptr`'ın bir `LibGit2.CredentialPayload` nesnesini içermesi gerekmektedir; bu nesne durum ve ayarları takip edecektir.

`allowed_types`, hangi kimlik doğrulama yöntemlerinin denenmesi gerektiğini belirten bir bitmask olan `LibGit2.Consts.GIT_CREDTYPE` değerlerini içerir.

Kimlik bilgisi doğrulaması aşağıdaki sırayla yapılır (destekleniyorsa):

  * SSH ajanı
  * SSH özel/kamu anahtar çifti
  * Kullanıcı adı/parola düz metin

Bir kullanıcıya bir kimlik bilgisi istemi sunulduğunda, istemi iptal etmek için `^D` yazarak (control tuşuna basarak ve `d` tuşuna birlikte basarak) iptal edebilirler.

**Not**: `libgit2` kimlik doğrulama prosedürünün özellikleri nedeniyle, kimlik doğrulama başarısız olduğunda, bu işlev tekrar çağrılır; ancak kimlik doğrulamanın başarılı olup olmadığına dair herhangi bir belirti yoktur. Aynı hatalı kimlik bilgilerini tekrar tekrar kullanmaktan kaçınmak için durumu payload ile takip edeceğiz.

Ek detaylar için LibGit2 kılavuzuna [bir sunucuya karşı kimlik doğrulama](https://libgit2.org/docs/guides/authentication/) bakın.

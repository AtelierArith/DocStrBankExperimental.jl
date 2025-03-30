# [Installation](@id man-installation)

Julia'yı kurmanın birçok yolu vardır. Aşağıdaki bölümler, her bir ana desteklenen platform için önerilen yöntemi vurgulamakta ve ardından özel durumlarda faydalı olabilecek alternatif yolları sunmaktadır.

Mevcut kurulum önerisi, Juliaup'a dayalı bir çözümdür. Daha önce Julia'yı Juliaup'a dayalı olmayan bir yöntemle kurduysanız ve sisteminizi Juliaup'a dayalı bir kuruluşa geçirmek istiyorsanız, önceki tüm Julia sürümlerini kaldırmanızı, `PATH` değişkeninizden Julia ile ilgili her şeyi çıkardığınızdan emin olmanızı ve ardından aşağıda açıklanan yöntemlerden biriyle Julia'yı kurmanızı öneririz.

## Windows

Windows'ta Julia, Windows mağazasından doğrudan [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN) ile kurulabilir. Aynı sürümü, aşağıdaki komutu çalıştırarak da kurabilirsiniz.

```
winget install julia -s msstore
```

herhangi bir kabukta.

## Mac and Linux

Julia, Linux veya Mac üzerinde çalıştırılarak kurulabilir.

```
curl -fsSL https://install.julialang.org | sh
```

bir kabukta.

### Command line arguments

Birçok komut satırı argümanı Julia yükleyicisine geçirilebilir. Yükleyici argümanlarının sözdizimi şudur:

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

Burada `<ARGS>` bir veya daha fazla aşağıdaki argümanla değiştirilmelidir:

  * `--yes` (veya `-y`): Yükleyiciyi etkileşimli olmayan bir modda çalıştırın. Tüm yapılandırma değerleri varsayılan değerlerini veya komut satırı argümanı olarak sağlanan bir değeri kullanır.
  * `--default-channel=<NAME>`: Varsayılan Juliaup kanalını yapılandırın. Örneğin `--default-channel lts`, `lts` kanalını yükler ve onu varsayılan olarak yapılandırır.
  * `--add-to-path=<evet|hayır>`: Julia'nın `PATH` ortam değişkenine eklenip eklenmeyeceğini yapılandırın. Geçerli değerler `evet` (varsayılan) ve `hayır`dır.
  * `--background-selfupdate=<SECONDS>`: `<SECONDS>` değeri 0'dan büyükse, Juliaup'ı otomatik güncelleyen isteğe bağlı bir CRON görevi yapılandırır. Gerçek değer, CRON görevinin yeni bir Juliaup sürümü kontrol etmek için kaç saniyede bir çalışacağını kontrol eder. Varsayılan değer 0'dır, yani hiçbir CRON görevi oluşturulmayacaktır.
  * `--startup-selfupdate=<DAKİKA>`: Julia'nın başlatıldığında Juliaup'un yeni sürümlerini ne sıklıkla kontrol edeceğini yapılandırır. Varsayılan değer her 1440 dakikadır.
  * `-p=<PATH>` (veya `--path`): Julia ve Juliaup ikili dosyalarının nereye yükleneceğini yapılandırır. Varsayılan `~/.juliaup`'dır.

## Alternative installation methods

Not edin ki, yukarıda açıklanan kurulum yöntemlerinden hiçbiri sisteminiz için işe yaramıyorsa, aşağıdaki yöntemleri *sadece* öneriyoruz.

Aşağıda açıklanan bazı kurulum yöntemleri, `juliaup` adlı bir paketin kurulmasını önermektedir. Bununla birlikte, bu yine de yalnızca Juliaup değil, tamamen işlevsel bir Julia sistemi kurar.

### App Installer (Windows)

Eğer bir sistemde Windows Store engellenmişse, alternatif bir [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) tabanlı kurulumumuz var. App Installer sürümünü kullanmak için [this](https://install.julialang.org/Julia.appinstaller) dosyasını indirin ve üzerine çift tıklayarak açın.

### MSI Installer (Windows)

Eğer Windows sisteminizde Windows Store veya App Installer sürümü çalışmıyorsa, MSI tabanlı bir yükleyici de kullanabilirsiniz. Bu yükleme yönteminin ciddi sınırlamaları olduğunu ve başka bir yöntem çalışmadıkça genellikle önerilmediğini unutmayın. Örneğin, bu yükleme yöntemiyle Juliaup için otomatik bir güncelleme mekanizması yoktur. MSI yükleyicisinin 64 bit sürümü [here](https://install.julialang.org/Julia-x64.msi) adresinden indirilebilir ve 32 bit sürümü [here](https://install.julialang.org/Julia-x86.msi) adresinden indirilebilir.

Varsayılan olarak, kurulum kullanıcı başına bir kurulum olacaktır ve yükseltme gerektirmeyecektir. Ayrıca, aşağıdaki komutu bir kabuktan çalıştırarak sistem kurulumu da yapabilirsiniz:

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

Brew ile sistemlerde, Julia'yı kurmak için şu komutu çalıştırabilirsiniz:

```
brew install juliaup
```

bir kabukta. Juliaup'ı standart brew komutlarıyla güncellemeniz gerektiğini unutmayın.

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

Arch Linux'ta, Juliaup mevcut [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/).

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

openSUSE Tumbleweed'de Julia'yı kurmak için şu komutu çalıştırabilirsiniz:

```sh
zypper install juliaup
```

kök ayrıcalıklarıyla bir kabukta.

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

Julia'yı Rust'ın cargo'su aracılığıyla kurmak için şunu çalıştırın:

```sh
cargo install juliaup
```

# [Installation](@id man-installation)

Il existe plusieurs façons d'installer Julia. Les sections suivantes mettent en évidence la méthode recommandée pour chacune des principales plateformes prises en charge, puis présentent des méthodes alternatives qui pourraient être utiles dans des situations spécialisées.

La recommandation d'installation actuelle est une solution basée sur Juliaup. Si vous avez installé Julia précédemment avec une méthode qui n'est *pas* basée sur Juliaup et que vous souhaitez passer votre système à une installation basée sur Juliaup, nous vous recommandons de désinstaller toutes les versions précédentes de Julia, de vous assurer que vous supprimez tout ce qui est lié à Julia de votre variable `PATH`, puis d'installer Julia avec l'une des méthodes décrites ci-dessous.

## Windows

Sur Windows, Julia peut être installée directement depuis le Windows Store [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN). On peut également installer exactement la même version en exécutant

```
winget install julia -s msstore
```

dans n'importe quel shell.

## Mac and Linux

Julia peut être installé sur Linux ou Mac en exécutant

```
curl -fsSL https://install.julialang.org | sh
```

dans un shell.

### Command line arguments

On peut passer divers arguments de ligne de commande à l'installateur Julia. La syntaxe pour les arguments de l'installateur est

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

Ici `<ARGS>` doit être remplacé par un ou plusieurs des arguments suivants :

  * `--yes` (ou `-y`) : Exécutez l'installateur en mode non interactif. Toutes les valeurs de configuration utilisent leur valeur par défaut ou une valeur fournie en tant qu'argument de ligne de commande.
  * `--default-channel=<NOM>` : Configure le canal par défaut de Juliaup. Par exemple, `--default-channel lts` installerait le canal `lts` et le configurerait comme canal par défaut.
  * `--add-to-path=<oui|non>` : Configure si Julia doit être ajoutée à la variable d'environnement `PATH`. Les valeurs valides sont `oui` (par défaut) et `non`.
  * `--background-selfupdate=<SECONDS>` : Configurez un travail CRON optionnel qui met à jour automatiquement Juliaup si `<SECONDS>` a une valeur supérieure à 0. La valeur réelle contrôle la fréquence à laquelle le travail CRON s'exécutera pour vérifier une nouvelle version de Juliaup en secondes. La valeur par défaut est 0, c'est-à-dire qu'aucun travail CRON ne sera créé.
  * `--startup-selfupdate=<MINUTES>` : Configure la fréquence à laquelle Julia vérifiera les nouvelles versions de Juliaup lors du démarrage de Julia. La valeur par défaut est de 1440 minutes.
  * `-p=<CHEMIN>` (ou `--path`): Configure l'emplacement où les binaires Julia et Juliaup sont installés. La valeur par défaut est `~/.juliaup`.

## Alternative installation methods

Notez que nous recommandons les méthodes suivantes *uniquement* si aucune des méthodes d'installation décrites ci-dessus ne fonctionne pour votre système.

Certaines des méthodes d'installation décrites ci-dessous recommandent d'installer un package appelé `juliaup`. Notez que cela installe néanmoins un système Julia entièrement fonctionnel, pas seulement Juliaup.

### App Installer (Windows)

Si le Windows Store est bloqué sur un système, nous avons une alternative [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) basée sur la configuration. Pour utiliser la version App Installer, téléchargez le fichier [this](https://install.julialang.org/Julia.appinstaller) et ouvrez-le en double-cliquant dessus.

### MSI Installer (Windows)

Si ni le Windows Store ni la version de l'App Installer ne fonctionnent sur votre système Windows, vous pouvez également utiliser un installateur basé sur MSI. Notez que cette méthode d'installation présente de sérieuses limitations et n'est généralement pas recommandée à moins qu'aucune autre méthode ne fonctionne. Par exemple, il n'y a pas de mécanisme de mise à jour automatique pour Juliaup avec cette méthode d'installation. La version 64 bits de l'installateur MSI peut être téléchargée depuis [here](https://install.julialang.org/Julia-x64.msi) et la version 32 bits depuis [here](https://install.julialang.org/Julia-x86.msi).

Par défaut, l'installation sera une installation par utilisateur qui ne nécessite pas d'élévation. Vous pouvez également effectuer une installation système en exécutant la commande suivante depuis un terminal :

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

Sur les systèmes avec brew, vous pouvez installer Julia en exécutant

```
brew install juliaup
```

dans un shell. Notez que vous devrez mettre à jour Juliaup avec des commandes brew standard.

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

Sur Arch Linux, Juliaup est disponible [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/).

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

Sur openSUSE Tumbleweed, vous pouvez installer Julia en exécutant

```sh
zypper install juliaup
```

dans un shell avec des privilèges root.

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

Pour installer Julia via cargo de Rust, exécutez :

```sh
cargo install juliaup
```

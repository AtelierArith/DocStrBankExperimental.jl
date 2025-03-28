```
download(url, [ output = tempname() ];
    [ method = "GET", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ downloader = <default>, ]
) -> output

    url        :: AbstractString
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (total::Integer, now::Integer) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    downloader :: Downloader
```

Téléchargez un fichier à partir de l'URL donnée, en le sauvegardant dans `output` ou, si non spécifié, dans un chemin temporaire. L'`output` peut également être un handle `IO`, auquel cas le corps de la réponse est diffusé vers ce handle et le handle est retourné. Si `output` est une commande, la commande est exécutée et la sortie lui est envoyée sur stdin.

Si l'argument clé `downloader` est fourni, il doit s'agir d'un objet `Downloader`. Les ressources et les connexions seront partagées entre les téléchargements effectués par le même `Downloader` et nettoyées automatiquement lorsque l'objet est collecté par le ramasse-miettes ou qu'aucun téléchargement n'a été effectué avec lui pendant une période de grâce. Voir `Downloader` pour plus d'informations sur la configuration et l'utilisation.

Si l'argument clé `headers` est fourni, il doit s'agir d'un vecteur ou d'un dictionnaire dont les éléments sont tous des paires de chaînes. Ces paires sont passées en tant qu'en-têtes lors du téléchargement d'URL avec des protocoles qui les prennent en charge, tels que HTTP/S.

L'argument clé `timeout` spécifie un délai d'attente pour que le téléchargement soit terminé en secondes, avec une résolution en millisecondes. Par défaut, aucun délai d'attente n'est défini, mais cela peut également être explicitement demandé en passant une valeur de délai d'attente de `Inf`. Séparément, si 20 secondes s'écoulent sans recevoir de données, le téléchargement expirera. Voir l'aide étendue pour savoir comment désactiver ce délai d'attente.

Si l'argument clé `progress` est fourni, il doit s'agir d'une fonction de rappel qui sera appelée chaque fois qu'il y a des mises à jour sur la taille et l'état du téléchargement en cours. Le rappel doit prendre deux arguments entiers : `total` et `now`, qui sont la taille totale du téléchargement en octets et le nombre d'octets qui ont été téléchargés jusqu'à présent. Notez que `total` commence à zéro et reste à zéro jusqu'à ce que le serveur donne une indication de la taille totale du téléchargement (par exemple, avec un en-tête `Content-Length`), ce qui peut ne jamais se produire. Ainsi, un rappel de progression bien conçu devrait gérer une taille totale de zéro de manière appropriée.

Si l'option `verbose` est définie sur true, `libcurl`, qui est utilisé pour implémenter la fonctionnalité de téléchargement, imprimera des informations de débogage sur `stderr`. Si l'option `debug` est définie sur une fonction acceptant deux arguments `String`, alors l'option verbose est ignorée et les données qui auraient été imprimées sur `stderr` sont passées au rappel `debug` avec les arguments `type` et `message`. L'argument `type` indique quel type d'événement s'est produit, et est l'un des suivants : `TEXT`, `HEADER IN`, `HEADER OUT`, `DATA IN`, `DATA OUT`, `SSL DATA IN` ou `SSL DATA OUT`. L'argument `message` est la description de l'événement de débogage.

## Aide Étendue

Pour une personnalisation supplémentaire, utilisez un [`Downloader`](@ref) et des [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads). Par exemple, pour désactiver le délai d'attente de 20 secondes lorsque aucune donnée n'est reçue, vous pouvez utiliser ce qui suit :

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```

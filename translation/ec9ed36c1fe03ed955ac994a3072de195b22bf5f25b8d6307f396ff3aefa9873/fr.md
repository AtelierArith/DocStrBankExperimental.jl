```
request(url;
    [ input = <none>, ]
    [ output = <none>, ]
    [ method = input ? "PUT" : output ? "GET" : "HEAD", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ throw = true, ]
    [ downloader = <default>, ]
    [ interrupt = <none>, ]
) -> Union{Response, RequestError}

    url        :: AbstractString
    input      :: Union{AbstractString, AbstractCmd, IO}
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (dl_total, dl_now, ul_total, ul_now) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    throw      :: Bool
    downloader :: Downloader
    interrupt  :: Base.Event
```

Faites une requête à l'URL donnée, retournant un objet `Response` capturant le statut, les en-têtes et d'autres informations sur la réponse. Le corps de la réponse est écrit dans `output` si spécifié et ignoré sinon. Pour les requêtes HTTP/S, si un flux `input` est donné, une requête `PUT` est effectuée ; sinon, si un flux `output` est donné, une requête `GET` est effectuée ; si aucun n'est donné, une requête `HEAD` est effectuée. Pour d'autres protocoles, des méthodes par défaut appropriées sont utilisées en fonction de la combinaison d'input et d'output demandée. Les options suivantes diffèrent de la fonction `download` :

  * `input` permet de fournir un corps de requête ; si fourni, par défaut à une requête `PUT`
  * `progress` est un rappel prenant quatre entiers pour le progrès de téléchargement et d'upload
  * `throw` contrôle si une erreur doit être levée ou si une `RequestError` doit être retournée en cas d'erreur de requête

Notez que contrairement à `download` qui lève une erreur si l'URL demandée ne peut pas être téléchargée (indiquée par un code de statut non-2xx), `request` retourne un objet `Response` peu importe le code de statut de la réponse. S'il y a une erreur pour obtenir une réponse, alors une `RequestError` est levée ou retournée.

Si l'argument clé `interrupt` est fourni, il doit s'agir d'un objet `Base.Event`. Si l'événement est déclenché pendant que la requête est en cours, la requête sera annulée et une erreur sera levée. Cela peut être utilisé pour interrompre une requête de longue durée, par exemple si l'utilisateur souhaite annuler un téléchargement.

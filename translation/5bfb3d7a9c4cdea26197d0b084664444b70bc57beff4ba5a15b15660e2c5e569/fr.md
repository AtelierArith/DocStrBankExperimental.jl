```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError` est un type capturant les propriétés d'une réponse échouée à une requête en tant qu'objet d'exception :

  * `url` : l'URL d'origine qui a été demandée sans aucune redirection
  * `code` : le code d'erreur libcurl ; `0` si une erreur de protocole uniquement s'est produite
  * `message` : le message d'erreur libcurl indiquant ce qui a mal tourné
  * `response` : objet de réponse capturant les informations de réponse disponibles

Le même type `RequestError` est lancé par `download` si la requête a réussi mais qu'il y avait une erreur au niveau du protocole indiquée par un code d'état qui n'est pas dans la plage 2xx, auquel cas `code` sera zéro et le champ `message` sera une chaîne vide. L'API `request` ne lance une `RequestError` que si le code d'erreur libcurl est non nul, auquel cas l'objet `response` inclus aura probablement un `status` de zéro et un message vide. Cependant, il existe des situations où une erreur au niveau de curl est lancée en raison d'une erreur de protocole, auquel cas à la fois le code et le message internes et externes peuvent être d'un intérêt.

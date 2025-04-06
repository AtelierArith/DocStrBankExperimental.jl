```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response` est un type capturant les propriétés d'une réponse réussie à une requête sous forme d'objet. Il a les champs suivants :

  * `proto` : le protocole qui a été utilisé pour obtenir la réponse
  * `url` : l'URL qui a finalement été demandée après avoir suivi les redirections
  * `status` : le code d'état de la réponse, indiquant le succès, l'échec, etc.
  * `message` : un message textuel décrivant la nature de la réponse
  * `headers` : tous les en-têtes qui ont été renvoyés avec la réponse

La signification et la disponibilité de certaines de ces réponses dépendent du protocole utilisé pour la requête. Pour de nombreux protocoles, y compris HTTP/S et S/FTP, un code d'état 2xx indique une réponse réussie. Pour les réponses dans des protocoles qui ne prennent pas en charge les en-têtes, le vecteur d'en-têtes sera vide. HTTP/2 n'inclut pas de message d'état, seulement un code d'état, donc le message sera vide.

# Web API da riga di comando

## GitHub

Accedi a informazioni pubbliche di profilo:

```
curl https://api.github.com/users/<USERNAME>
```

Repository di un utente (pubbliche):

```
curl https://api.github.com/users/<USERNAME>/repos
```

Informazioni sull'organizzazione di questo corso ed i suoi membri:

```
curl https://api.github.com/orgs/DigiPlatMOOC
curl https://api.github.com/orgs/DigiPlatMOOC/members
```

Caricamento di un file su Gist:

```
curl --user "<USERNAME>" --data @github-sample-gist.json https://api.github.com/gists
```

La password di GitHub verrà richiesta da riga di comando.
Il comando non funziona nel caso sia attivata l'autenticazione “2 factor”.

## Spotify

```
curl https://api.spotify.com/v1/artists/4X42BfuhWCAZ2swiVze9O0
curl https://api.spotify.com/v1/albums/34FJe0y8eKh3caqEoL8qqW
```

## JSON placeholder API

Semplice API _RESTful_ di prova, che ritorna dati in formato JSON.

```
http://jsonplaceholder.typicode.com/posts
http://jsonplaceholder.typicode.com/posts/1
http://jsonplaceholder.typicode.com/posts/1/comments
http://jsonplaceholder.typicode.com/users/1
```

## API Program-O online

Effettua una conversazione con un bot [Program-O](http://program-o.com) online (un interprete di codice AIML).

```
http://api.program-o.com/v2/chatbot/?say=TEXT&bot_id=6&format=json&convo_id=CONVO-ID
```

## Random.org

Genera numeri _realmente_ casuali.
È necessario innanzitutto generare una **chiave** di accesso alle API, tramite la [pagina relativa](https://api.random.org/api-keys/beta).
La chiave va inclusa nelle richieste alle API.

```
curl --request POST --data '{"jsonrpc":"2.0","method":"generateIntegers","params":{"apiKey":"APIKEY","n":10,"min":1,"max":6},"id":42}' https://api.random.org/json-rpc/1/invoke
```

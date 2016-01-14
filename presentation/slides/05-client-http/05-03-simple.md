## Protocole très simple

1/ On envoie une requête texte (HTTP)

2/ On attend la réponse


=> Testons avec un petit telnet

```
$ telnet perdu.com 80
Trying 208.97.177.124...
Connected to perdu.com.
Escape character is '^]'.
GET / HTTP/1.1
host: perdu.com
```

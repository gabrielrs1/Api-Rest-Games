# API de Games
Esta API pode ser utilizada no gerenciamento de criação, leitura, edição e deleção de qualquer item cadastrado em sua loja de games eletrônicos por exemplo.
## Endpoints
### GET /games
Esse endpoint é responsável por retornar a listagem de todos os games cadastrados no banco de dados.
#### Parametros
Nenhum
#### Respostas
##### OK! 200
Caso essa resposta aconteça você vai recebar a listagem de todos os games.

Exemplo de resposta:
```

[
    {
        "id": 23,
        "title": "Call of duty MW",
        "year": 2019,
        "price": 60
    },
    {
        "id": 65,
        "title": "Sea of thieves",
        "year": 2018,
        "price": 40
    },
    {
        "id": 2,
        "title": "Minecraft",
        "year": 2012,
        "price": 20
    }
]

```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
<hr>
<hr>

### GET /game/:id
Esse endpoint é responsável por encontrar um game cadastrado, pelo seu id.
#### Parâmetros
id: id de um game cadastrado, sendo passado na rota da aplicação

Exemplo:
``` 
   http://localhost:45679/game/1
```
#### Respostas
##### Requisição inválida! 400
Caso essa resposta seja retornada, o id não é válido, pelo motivo que na rota de deve ser passado apenas números

Exemplo da resposta:
```
   Bad Request
```
##### Não encontrado! 404
Caso essa resposta seja retornada, o game com id passado não está cadastrado

Exemplo da resposta:
```
   Not Found
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
##### OK! 200
Caso essa resposta seja retornada, tudo ocorreu com sucesso

Exemplo da resposta:
```
{
  "game": {
    "id": 2,
    "title": "Minecraft",
    "year": 2012,
    "price": 20
  },
  "_links": [
    {
      "href": "http://localhost:45679/game/2",
      "method": "DELETE",
      "rel": "delete_game"
    },
    {
      "href": "http://localhost:45679/game/2",
      "method": "GET",
      "rel": "get_game"
    },
    {
      "href": "http://localhost:45679/game/2",
      "method": "PUT",
      "rel": "edit_game"
    },
    {
      "href": "http://localhost:45679/games",
      "method": "GET",
      "rel": "get_all_games"
    }
  ]
}
```
<hr>
<hr>

### POST /game
Esse endpoint é responsável por criar um novo game
#### Parametros
title: Nome do game para ser cadastrado

price: Preço do game para ser cadastrado

year: Ano do game para ser cadastrado

Exemplo: 
```
{
   "title": "seu_email",
   "price": "preco_jogo"
   "year": "ano_jogo",
}
```
#### Respostas
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
##### OK! 200
Caso essa resposta aconteça, tudo ocorreu com sucesso

Exemplo da resposta:
```
   OK
```
<hr>
<hr>

### DELETE /game/:id
Esse endpoint é responsável por deletar um game cadastrado
#### Parametros
id: id de um game cadastrado, sendo passado na rota da aplicação

Exemplo:
```
   http://localhost:45679/game/1
```
#### Respostas
##### Requisição inválida! 400
Caso essa resposta seja retornada, o id não é válido, pelo motivo que na rota de deve ser passado apenas números

Exemplo da resposta:
```
   Bad Request
```
##### Não encontrado! 404
Caso essa resposta seja retornada, o game com id passado não está cadastrado

Exemplo da resposta:
```
   Not Found
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
##### OK! 200
Caso essa resposta aconteça, tudo ocorreu com sucesso

Exemplo da resposta:
```
   OK
```
<hr>
<hr>

### PUT /game/:id
Esse endpoint é responsável por editar um game cadastrado
#### Parametros
id: id de um game cadastrado, sendo passado na rota da aplicação

Exemplo:
```
   http://localhost:45679/game/1
```
#### Respostas
##### Requisição inválida! 400
Caso essa resposta seja retornada, o id não é válido, pelo motivo que na rota de deve ser passado apenas números

Exemplo da resposta:
```
   Bad Request
```
##### Não encontrado! 404
Caso essa resposta seja retornada, o game com id passado não está cadastrado

Exemplo da resposta:
```
   Not Found
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
##### OK! 200
Caso essa resposta aconteça, tudo ocorreu com sucesso

Exemplo da resposta:
```
   OK
```
<hr>
<hr>

### POST /auth
Esse endpoint é responsável por retornar fazer o processo de login.
#### Parametros
email: E-mail do usuário cadastrado no sistema.

password: Senha do usuário cadastrado no sistema, com aquele determinado e-mail.

Exemplo:
```
{
   "email": "victordevtb@guiadoprogramador.com",
   "password": "nodejs<3"
}
```
#### Respostas
##### OK! 200
Caso essa resposta aconteça você vai receber o token JWT para conseguir acessar endpoints protegidos na API.

Exemplo de resposta:
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJ2aWN0b3JkZXZ0YkBndWlhZG9wcm9ncmFtYWRvci5jb20iLCJpYXQiOjE1OTE3ODI0NzUsImV4cCI6MTU5MTk1NTI3NX0.y8kp3BxKgC86KFiq6-tAABukR6vi1guTPeRQhO8IdwU"
}
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Senha ou e-mail incorretos.

Exemplo de resposta:
```
{
   "err": "Credenciais inválidas!"
}
```
##### Não encontrado! 404
Caso essa resposta seja retornada, o game com id passado não está cadastrado

Exemplo da resposta:
```
{
   "err": "O E-mail enviado não existe na base de dados!"
}
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, isso significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```
{
   "err": "Token inválido!"
}
```
##### Requisição inválida! 400
Caso essa resposta seja retornada, o e-mail passado não foi passado para a requisição

Exemplo da resposta:
```
{
   "err": "O E-mail enviado é inválido"
}
```

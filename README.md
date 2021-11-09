<h1 align='center'>
    JSON Server React da API Cookin'

## Endpoints

A url base da API é https://###############

## Rotas que não precisam de autenticação

<br/>

<h2 align='center'> Usuários </h2>
<h3 align='center'> Cadastro de usuário</h3>

`POST /register - FORMATO DA REQUISIÇÃO - STATUS 201`

```json
{
  "name": "nome do usuário",
  "email": "email do usuário",
  "sexo": "sexo do usuário",
  "pasword": "senha do usuário"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmF0b3N1Z3VpeUBnbWFpbC5jb20iLCJpYXQiOjE2MzUxODgyNDMsImV4cCI6MTYzNTE5MTg0Mywic3ViIjoiMiJ9.2RlYnFu1xmqEEbmJM89YmMI8YFu745cksdgkR5pSDr4",
  "user": {
    "name": "nome do usuário",
    "email": "email do usuário",
    "sexo": "sexo do usuário",
    "id": "id do usuário"
  }
}
```

<br/>

<h3 align='center'> Login </h3>

`POST /login - FORMATO DA REQUISIÇÃO - STATUS 201`

```json
{
  "email": "email do usuário",
  "password": "senha do usuário"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmF0b3N1Z3VpeUBnbWFpbC5jb20iLCJpYXQiOjE2MzUxODk0NTcsImV4cCI6MTYzNTE5MzA1Nywic3ViIjoiMiJ9.ICDyqztTS7PYM8hebNx77LD48US91sMecMSqJQuJ3JM",
  "user": {
    "name": "nome do usuário",
    "email": "email do usuário",
    "sexo": "sexo do usuário",
    "id": "id do usuário"
  }
}
```

## Rotas que precisam de autenticação

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir acessar os endpoints abaixo:

<br/>
<h2 align='center'> Receitas Particulares </h2>

<h3 align='center'> Adicionar Receitas Particulares</h3>

`POST /myrecipes - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "título da receita",
  "ingredients": [
    "ingrediente",
    "ingrediente",
    "ingrediente",
    "ingrediente"
    ],
  "instructions": [
    "passo",
    "passo",
    "passo",
    "passo"
    ],
    "category": "salgado || doce || bebida",
    "author":"Mark",
    "userId": "1",
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "título da receita",
  "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
  "instructions": ["passo", "passo", "passo", "passo"],
  "category": "salgado || doce || bebida",
  "author": "Mark",
  "userId": "1",
  "id": "1"
}
```

<br/>

<h3 align='center'> Ver Receitas Particulares </h3>

`GET /myrecipes - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
[
  {
    "title": "título da receita",
    "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
    "instructions": ["passo", "passo", "passo", "passo"],
    "category": "salgado || doce || bebida",
    "author": "Mark",
    "userId": "1",
    "id": "1"
  }
]
```

<br/>

<h3 align='center'> Deletar Receitas Particulares </h3>

`DELETE /myrecipes/${myrecipeID} - FORMATO DA RESPOSTA - STATUS 200`

Este endpoint não possui resposta

<br/>

<h3 align='center'> Editar Receitas Particulares</h3>

`POST /myrecipes/${myrecipeID} - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "título da receita",
  "ingredients": [
    "ingrediente",
    "ingrediente",
    "ingrediente",
    "ingrediente"
    ],
  "instructions": [
    "passo",
    "passo",
    "passo",
    "passo"
    ],
    "category": "salgado || doce || bebida",
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "título da receita",
  "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
  "instructions": ["passo", "passo", "passo", "passo"],
  "category": "salgado || doce || bebida",
  "author": "Mark",
  "userId": "1",
  "id": "1"
}
```

<br/>
<h2 align='center'> Receitas Públicas </h2>
<h3 align='center'> Adicionar Receitas Públicas</h3>

`POST /recipes - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "título da receita",
  "ingredients": [
    "ingrediente",
    "ingrediente",
    "ingrediente",
    "ingrediente"
    ],
  "instructions": [
    "passo",
    "passo",
    "passo",
    "passo"
    ],
    "category": "salgado || doce || bebida",
    "author":"Mark",
    "review": [],
    "userId": "1"
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "título da receita",
  "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
  "instructions": ["passo", "passo", "passo", "passo"],
  "category": "salgado || doce || bebida",
  "author": "Mark",
  "review": [],
  "userId": "1",
  "id": "1"
}
```

<br/>

<h3 align='center'> Ver Receitas Públicas </h3>

`GET /recipes - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
[
  {
    "title": "título da receita",
    "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
    "instructions": ["passo", "passo", "passo", "passo"],
    "category": "salgado || doce || bebida",
    "author": "Mark",
    "review": [],
    "userId": "1",
    "id": "1"
  }
]
```

<br/>
<h2 align='center'> Favoritas </h2>
<h3 align='center'> Adicionar Receitas Favoritas</h3>

`POST /favorites - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "título da receita",
  "ingredients": [
    "ingrediente",
    "ingrediente",
    "ingrediente",
    "ingrediente"
    ],
  "instructions": [
    "passo",
    "passo",
    "passo",
    "passo"
    ],
    "category": "salgado || doce || bebida",
    "author":"Mark",
    "userId": "1",
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "título da receita",
  "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
  "instructions": ["passo", "passo", "passo", "passo"],
  "category": "salgado || doce || bebida",
  "author": "Mark",
  "userId": "1",
  "id": "1"
}
```

<br/>

<h3 align='center'> Ver Receitas Favoritas </h3>

`GET /favorites - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
[
  {
    "title": "título da receita",
    "ingredients": ["ingrediente", "ingrediente", "ingrediente", "ingrediente"],
    "instructions": ["passo", "passo", "passo", "passo"],
    "category": "salgado || doce || bebida",
    "author": "Mark",
    "userId": "1",
    "id": "1"
  }
]
```

<br/>

<h3 align='center'> Deletar Receitas favorites </h3>

`DELETE /favorites/${favoritesID} - FORMATO DA RESPOSTA - STATUS 200`

Este endpoint não possui resposta

<br/>


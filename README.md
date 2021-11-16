<h1 align='center'>
    JSON Server React da API Cookin'

## Endpoints

A url base da API é https://api-cookin.herokuapp.com

## Rotas que não precisam de autenticação

<br/>

<h2 align='center'> Usuários </h2>
<h3 align='center'> Cadastro de usuário</h3>

`POST /register - FORMATO DA REQUISIÇÃO - STATUS 201`

```json
{
  "name": "Philipe Compê",
  "email": "pcompe@email.com",
  "sexo": "m",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InBjb21wZUBlbWFpbC5jb20iLCJpYXQiOjE2MzY0ODU0NjEsImV4cCI6MTYzNjQ4OTA2MSwic3ViIjoiMiJ9.CcAbGr4YPxgvTVrfadAuibSFFTOVP15CLB6LnAwVmLU",
  "user": {
    "email": "pcompe@email.com",
    "name": "Philipe Compê",
    "sexo": "m",
    "id": 2
  }
}
```

<br/>

<h3 align='center'> Login </h3>

`POST /login - FORMATO DA REQUISIÇÃO - STATUS 201`

```json
{
  "email": "pcompe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InBjb21wZUBlbWFpbC5jb20iLCJpYXQiOjE2MzY0ODU2NTAsImV4cCI6MTYzNjQ4OTI1MCwic3ViIjoiMiJ9.bshw8mx1ZvLIaW56DOF34NsxFpsCXqBlJ9xy4_BakuQ",
  "user": {
    "email": "pcompe@email.com",
    "name": "Philipe Compê",
    "sexo": "m",
    "id": 2
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
  "title": "Bolo de Laranja Vegano",
  "ingredients": [
    "1 laranja em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "userId": "1"
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "Bolo de Laranja Vegano",
  "ingredients": [
    "1 laranja em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "userId": "1",
  "id": 1
}
```

<br/>

<h3 align='center'> Ver Receitas Particulares </h3>

`GET /myrecipes - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
[
  {
    "title": "Bolo de Laranja Vegano",
    "ingredients": [
      "1 laranja em cubos",
      "1/2 xícara de suco de laranja",
      "3/4 de xícara de óleo",
      "1 xícara de açúcar",
      "2 xícaras de farinha de trigo",
      "1 colher de sopa de fermento em pó",
      "Pitada de sal"
    ],
    "instructions": [
      "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
      "Misturar em uma tigela a farinha e o fermento em pó.",
      "Incorporar a mistura do liquidificador na farinha com o fermento.",
      "Colocar a massa em uma forma untada e enfarinhada.",
      "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
    ],
    "category": "doce",
    "author": "Mark",
    "userId": "1",
    "id": 1
  }
]
```

<br/>

<h3 align='center'> Deletar Receitas Particulares </h3>

`DELETE /myrecipes/${myrecipeID} - FORMATO DA RESPOSTA - STATUS 200`

Este endpoint não possui resposta

<br/>

<h3 align='center'> Editar Receitas Particulares</h3>

`PATCH /myrecipes/${myrecipeID} - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "Bolo de Maçã Vegano",
  "ingredients": [
    "1 maçã em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "userId": "1",
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "Bolo de Laranja Vegano",
  "ingredients": [
    "1 laranja em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "userId": "1",
  "id": 1
}
```

<br/>
<h2 align='center'> Receitas Públicas </h2>
<h3 align='center'> Adicionar Receitas Públicas</h3>

`POST /recipes - FORMATO DA REQUISIÇÃO - STATUS 201`

```JSON
{
  "title": "Bolo de Maçã Vegano",
  "ingredients": [
    "1 maçã em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "favorites_users": [],
  "myrecipesId": 1, 
  "userId": "1"
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "title": "Bolo de Laranja Vegano",
  "ingredients": [
    "1 laranja em cubos",
    "1/2 xícara de suco de laranja",
    "3/4 de xícara de óleo",
    "1 xícara de açúcar",
    "2 xícaras de farinha de trigo",
    "1 colher de sopa de fermento em pó",
    "Pitada de sal"
  ],
  "instructions": [
    "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
    "Misturar em uma tigela a farinha e o fermento em pó.",
    "Incorporar a mistura do liquidificador na farinha com o fermento.",
    "Colocar a massa em uma forma untada e enfarinhada.",
    "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
  ],
  "category": "doce",
  "author": "Mark",
  "favorites_users": [],
  "myrecipesId": 1, 
  "userId": "1",
  "id": 1
}
```

<br/>

<h3 align='center'> Ver Receitas Públicas </h3>

`GET /recipes - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
[
  {
    "title": "Bolo de Maçã Vegano",
    "ingredients": [
      "1 maçã em cubos",
      "1/2 xícara de suco de laranja",
      "3/4 de xícara de óleo",
      "1 xícara de açúcar",
      "2 xícaras de farinha de trigo",
      "1 colher de sopa de fermento em pó",
      "Pitada de sal"
    ],
    "instructions": [
      "Bater no liquidificador a laranja, o suco, o óleo, o açúcar e o sal e reservar.",
      "Misturar em uma tigela a farinha e o fermento em pó.",
      "Incorporar a mistura do liquidificador na farinha com o fermento.",
      "Colocar a massa em uma forma untada e enfarinhada.",
      "Assar por 40 a 50 minutos em forno pré-aquecido a 180ºC."
    ],
    "category": "doce",
    "author": "Mark",
    "favorites_users": [],
    "myrecipesId": 1, 
    "userId": "1",
    "id": 1
  }
]
```

<br/>


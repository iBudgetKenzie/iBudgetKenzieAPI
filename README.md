<h1 align="center">
  iBudget API
</h1>

<p align = "center">
Este é o backend da aplicação iBudget - Uma aplicação web que permite que os usuários registrem seus dados, alimente um formulário com os dados do cliente e os valores a serem calculados, baseado nos custos fixos e variáveis, além do calculo da hora de trabalho. Podendo então gerar um histórico de orçamentos e exibi-los de forma clara e objetiva.
</p>

## **Endpoints**

- A API tem um total de 8 endpoints, sendo em volta do usuário (dev) - podendo cadastrar seu perfil, logar e registrar orçamentos (budgets) realizados. <br/>
- O JSON para utilizar no Insomnia é este aqui -> https://drive.google.com/file/d/16q7Pc-B5hMU1xBLSauvSx1npuWZxscDI/view?usp=sharing <br/>
- Para importar o JSON no Insomnia é só baixar o arquivo. Na palavra "Insomnia" no canto superior esquerdo. Nesse dropdown é só clicar em "Import / Export > Import Data > From File" e selecionar o arquivo que foi feito download.

- O URL base da API é https://ibudget-kenzie.herokuapp.com

## Rotas que NÃO precisam de autenticação (token no header)

<h2 align ='center'> Login de usuário </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "alvrinho6@kenzie.com",
  "password": "123456"
}

```
`FORMATO DA RESPOSTA`

```json
{
	"accessToken": "token-aqui",
	"user": {
		"email": "alvrinho6@kenzie.com",
		"name": "Álvaro Alencar",
		"username": "alvrinho",
		"position": "Front-end developer",
		"imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512",
		"id": 7
	}
}
```
<h2 align ='center'> Cadastro de usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "alvrinho6@kenzie.com",
  "password": "123456",
  "name": "Álvaro Alencar",
  "username": "alvrinho",
  "position": "Front-end developer",
  "imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512"
}
```

`FORMATO DA RESPOSTA`

```json
{
	"accessToken": "token-aqui",
	"user": {
		"email": "alvrinho6@kenzie.com",
		"name": "Álvaro Alencar",
		"username": "alvrinho",
		"position": "Front-end developer",
		"imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512",
		"id": 7
	}
}
```

## Rotas que PRECISAM de autenticação (token no header)

<h2 align ='center'> Informações do usuário e orçamentos (budgets) </h2>

`GET /users/{userId}?_embed=budgets - FORMATO DA REQUISIÇÃO`

```
Não precisa de body.
```

`FORMATO DA RESPOSTA`

```json
{
	"email": "alvrinho1@kenzie.com",
	"password": "$2a$10$hAFB1p6qVibfXHVAYf0ew.CnLied6gF7/SJBuLYmARHWGpOBQJxpq",
	"name": "Alvrinho",
	"username": "alvrinho",
	"position": "Frontend developer",
	"imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512",
	"id": 2,
	"budgets": [
		{
			"projectName": "Landing page para petshop",
			"projectTime": "2",
			"fixedCost": 1000,
			"variableCost": 300,
			"userId": 2,
			"id": 2
		}
	]
}
```

<h2 align ='center'> Editar usuário </h2>

`PATCH /users/{userId} - FORMATO DA REQUISIÇÃO`

```json
{
	"email": "alvrinho1@kenzie.com",
	"name": "Alvrinho",
	"position": "Back-end developer"
}
```

`FORMATO DA RESPOSTA`

```json
{
	"email": "alvrinho1@kenzie.com",
	"password": "$2a$10$6X49f9Pz9awZuwiOEmrFeuwP8unDAMWKCTN0tJfh3M5CIgvYYPHUS",
	"name": "Alvrinho",
	"username": "alvrinho",
	"position": "Back-end developer",
	"imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512",
	"id": 3
}
```

<h2 align ='center'> Excluir usuário </h2>

`DELETE /users/{userId} - FORMATO DA REQUISIÇÃO`

```
Não precisa de body.
```

`FORMATO DA RESPOSTA - STATUS 200`

<h2 align ='center'> Cadastro de orçamento (budget) </h2>

`POST /budgets - FORMATO DA REQUISIÇÃO`

```json
{
	"projectName": "Landing page para barbershop",
	"projectTime": "2",
	"fixedCost": 1000,
	"variableCost": 300,
	"userId": 2
}
```

`FORMATO DA RESPOSTA`

```json
{
	"projectName": "Landing page para barbershop",
	"projectTime": "2",
	"fixedCost": 1000,
	"variableCost": 300,
	"userId": 2,
	"id": 3
}
```

<h2 align ='center'> Alteração de orçamento (budget) </h2>

`PATCH /budgets/{budgetId} - FORMATO DA REQUISIÇÃO`

```json
{
	 "fixedCost": 900
}
```

`FORMATO DA RESPOSTA`

```json
{
	"projectName": "Landing page para barbershop",
	"projectTime": "2",
	"fixedCost": 900,
	"variableCost": 300,
	"userId": 2,
	"id": 3
}
```

<h2 align ='center'> Deletando um orçamento (budget) </h2>

`DELETE /budgets/{budgetId} - FORMATO DA REQUISIÇÃO`

```
Não precisa de body.
```

`FORMATO DA RESPOSTA - STATUS 200`

---

Feito por alvaroallencar :)

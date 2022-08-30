<h1 align="center">
  iBudget API
</h1>

<p align = "center">
Este é o backend da aplicação iBudget - Uma aplicação web que permite que os usuários registrem seus dados, alimente um formulário com os dados do cliente e os valores a serem calculados, baseado nos custos fixos e variáveis, além do calculo da hora de trabalho. Podendo então gerar um histórico de orçamentos e exibi-los de forma clara e objetiva.
</p>

## **Endpoints**

- A API tem um total de 8 endpoints, sendo em volta do usuário (dev) - podendo cadastrar seu perfil, orçamentos (budgets) realizados. <br/>
- O JSON para utilizar no Insomnia é este aqui -> link do drive <br/>
- Para importar o JSON no Insomnia é só baixar o arquivo. Na palavra "Insomnia" no canto superior esquerdo. Nesse dropdown é só clicar em "Import / Export > Import Data > From File" e selecionar o arquivo que foi feito download.

- O URL base da API é https://ibudget-kenzie.herokuapp.com

## Rotas que não precisam de autenticação

<h2 align ='center'> Login de usuário </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "alvrinho@kenzie.com",
  "password": "123456"
}
```
<h2 align ='center'> Cadastro de usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "alvrinho@kenzie.com",
  "password": "123456",
  "name": "Alvrinho",
  "username": "alvrinho",
  "position": "Front-end developer",
  "imageUrl": "https://ca.slack-edge.com/TQZR39SET-U035WCR5001-b76f4c1838fd-512"
}
```

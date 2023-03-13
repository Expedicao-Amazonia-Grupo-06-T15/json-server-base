<h1 align="center">Travel Agency - Expedição Amazônia - API 🚀</h1>

Este é o backend da aplicação Travel Agency - Expedição Amazônia. O objetivo desta aplicação é fornecer os endpoints necessários para criar uma aplicação front-end que tenha o seu prórpio bacnk-end. A API possui diversas rotas, com foco no usuário e em suas interações com agendamento de hotéis, passeios, bem como a possibilidade de favoritar as atividades preferidas.


## Endpoints

A API tem 19 endpoints.  Abaixo, alguns exemplos de formato de requisição e resposta esperada.

**## Importante:** URL base: https://expedicao-amazonia.herokuapp.com/

**<h3>Rotas que não precisam de autenticação:</h3>**

### Cadastro:
Formato da requisição: POST /register
A API também aceita: POST /signup e POST /users

``` 
{
	"email": "ana@email.com",
	"password": "123456",
	"name": "Ana",
	"phone_number": "85985480645"
} 

Formato da resposta - Status 201:

 {
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFuYUBlbWFpbC5jb20iLCJpYXQiOjE2NzgyOTEyMTIsImV4cCI6MTY3ODI5NDgxMiwic3ViIjoiNSJ9.XIc6QN2tIHVIJd8FpcwW7JKdaU2fDWScUiHHFO1ncks",
	"user": {
		"email": "ana@email.com",
		"name": "Ana",
		"phone_number": "85985480645",
		"id": 5
	}
} 
```
### Login:
Formato da requisição: POST /login 
A API também aceita: POST /signin

```
{
	"email": "kenzinho@mail.com",
	"password": "123456"
}

Formato da resposta - Status 200:

{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImtlbnppbmhvQG1haWwuY29tIiwiaWF0IjoxNjc4NzM2MDMzLCJleHAiOjE2Nzg3Mzk2MzMsInN1YiI6IjEifQ.2RCNgduj7ensLPyUkGwZxWuiqZiCdP2K687UwNDwx5Y",
	"user": {
		"email": "kenzinho@mail.com",
		"name": "Kenzinho",
		"phone_number": "8599875656",
		"id": 1
	}
}
```

### Listar todos os hotéis:
Formato da requisição: GET /hotels

Formato da resposta - Status 200:
```
[
	{
		"id": 1,
		"name": "Holiday Inn Manaus",
		"price": 149,
		"address": "Av. Rodrigo Otávio, 3721 - Japiim, Manaus - AM, 69073-177, Brazil",
		"img": "https://images.pexels.com/photos/13696647/pexels-photo-13696647.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
		"reviews": 4.5,
		"rooms": 13,
		"description": "Está cerca de 6KM do Centro Histórico e de fácil acesso ao Aeroporto Internacional Eduardo Gomes hotel Holiday Inn® Manaus oferece a localização e estrutura perfeita para viagens de negócios, lazer e grupos com protocolos de limpeza e biossegurança. Situado na zona industrial próximo as principais empresas da região como Samsung, P&G, Honda, White Martins, entre outras"
	},
...
]
```

### Listar todas as atividades:
Formato da requisição: GET /activities

Formato da resposta - Status 200:
```
[
	{
		"id": 1,
		"name": "Encontro das águas",
		"price": 60,
		"type": "aquatica",
		"img": "https://amz.live/wp-content/uploads/2021/05/Encontro-das-A%CC%81guas.jpg",
		"reviews": null,
		"description": "Trata-se de um incrível fenômeno da natureza onde as águas barrentas do Rio Solimões e as águas escuras do Rio Negro se encontram e percorrem, lado a lado, por um trecho de seis quilômetros de extensão, mas não chegam a se misturar nunca. Para presenciar essa maravilha natural, um passeio de barco, que tem duração de um pouco mais de uma hora e passa por outras lindas paisagens da região, lhe levará até o ponto de encontro das águas desses dois importantes rios."
	},
...
]
```

**<h3>Rotas que necessitam de autorização:</h3>**
Informar no cabeçalho da requisição o campo "Authorization", dessa forma:
```
	Authorization: Bearer {token}
  
  ```
  
 **Atividades**

Listar todas as atividades favoritas do usuário: GET/favoritesActivities 
Adicionar atividade favorita do usuário: POST/favoritesActivities 
Deletar atividade favorita do usuário: DELETE/favoritesActivities/1 - id do usuário

**Hotéis**

Listar hotéis favoritos do usuário: GET/favoritesHotels 
Adicionar hotel favorito do usuário: POST/favoritesHotels  
Deletar hotel favorito do usuário: DELETE/favoritesHotels/2 - id do usuário

**Reservas de Hotel**

Listar todas as reservas do usuário: GET/reservedHotels 
Adicionar reserva do usuário: POST/reservedHotels  
Deletar reserva do usuário: DELETE/reservedHotels/1 - id do usuário

**Reservas de Atividades**

Listar todas as reservas de atividades do usuário: GET/reservedActivities 
Adicionar reserva de atividade do usuário: POST/reservedActivities   
Deletar reserva de atividade do usuário: DELETE/reservedActivities/1 - id do usuário

Listas as avaliações de Hotel: GET /hotels/3/hotelsReviews - id do hotel
Adicionar avaliação de Hotel: POST/hotelsReviews

Listas as avaliações de Atividade: GET/activities/4/activitiesReviews
Adicionar avaliação de Atividade: POST/activitiesReviews


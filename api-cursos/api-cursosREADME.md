# API de Cursos

## Aula 01 — Fluxo Cliente e Servidor

A API de Cursos funciona através da comunicação entre um cliente e um servidor utilizando o protocolo HTTP.

Quando o cliente realiza uma requisição `GET /cursos`, o fluxo acontece da seguinte forma:

**Cliente → Requisição HTTP → Back-end → Processamento → Resposta HTTP → Cliente**

### Cliente

O cliente é responsável por fazer a solicitação. Neste projeto, ele pode ser um navegador, Postman ou outra aplicação que envie requisições HTTP.

### Requisição HTTP (Request)

O cliente envia uma requisição `GET` para o endereço `/cursos`.

Essa requisição significa que o cliente deseja consultar e receber a lista de cursos cadastrados.

### Back-end / Servidor

O servidor é a aplicação desenvolvida com Spring Boot. Ele recebe a requisição HTTP e encaminha a solicitação para o Controller.

O Controller será responsável por receber a requisição e encaminhá-la para as próximas camadas da aplicação.

### Processamento

Durante o processamento, o back-end verifica a solicitação e realiza as operações necessárias para obter os cursos cadastrados.

Em uma API completa, o Controller encaminha a solicitação para o Service, que utiliza o Repository para acessar os dados armazenados.

### Resposta HTTP (Response)

Depois do processamento, o servidor envia uma resposta HTTP para o cliente.

Em caso de sucesso, a requisição `GET /cursos` deverá retornar:

`200 OK`

A resposta conterá a lista de cursos cadastrados em formato JSON.

### Fluxo completo

```text
Cliente
   ↓
GET /cursos
   ↓
Requisição HTTP (Request)
   ↓
Servidor / Back-end
   ↓
Processamento
   ↓
Resposta HTTP (Response)
   ↓
200 OK + lista de cursos em JSON
   ↓
Cliente
```

Portanto, o cliente solicita a lista de cursos através de uma requisição HTTP. O servidor recebe essa solicitação, realiza o processamento necessário e devolve uma resposta HTTP contendo os cursos cadastrados.

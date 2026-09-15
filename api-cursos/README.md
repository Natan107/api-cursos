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

### Processamento

Durante o processamento, o back-end verifica a solicitação e realiza as operações necessárias para obter os cursos cadastrados.

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

---

## Aula 02 — Responsabilidades do Back-end

Quando o cliente realizar um cadastro de curso, o back-end será responsável por receber a solicitação, processar os dados e realizar as operações necessárias antes de devolver uma resposta.

O back-end não funciona apenas como uma tela. Ele é responsável por processar as informações recebidas do cliente, aplicar as regras do sistema e armazenar os dados.

As principais ações realizadas pelo back-end serão:

### 1. Receber os dados enviados pelo cliente

O cliente enviará os dados do curso através de uma requisição HTTP `POST /cursos`.

Exemplo:

```json
{
    "nome": "Back-End Frameworks",
    "cargaHoraria": 60
}
```

### 2. Transformar os dados em um objeto Java

Depois de receber os dados em formato JSON, o Spring Boot irá transformar essas informações em um objeto Java da classe `Curso`.

Esse objeto possuirá os atributos:

* `id`
* `nome`
* `cargaHoraria`

### 3. Verificar as regras do curso

O back-end deverá verificar se os dados enviados estão de acordo com as regras definidas para o sistema.

As regras são:

* o nome do curso não pode ser nulo;
* o nome não pode ficar em branco;
* a carga horária deve ser maior que zero.

### 4. Salvar o curso

Depois que os dados forem recebidos e validados, o back-end deverá salvar o curso.

O curso será encaminhado para a camada responsável pelo acesso aos dados e posteriormente armazenado no banco de dados.

O identificador (`id`) será gerado automaticamente.

### 5. Devolver uma resposta ao cliente

Depois de concluir o cadastro, o back-end deverá enviar uma resposta HTTP para o cliente.

Quando o cadastro for realizado com sucesso, a API deverá retornar:

`201 Created`

A resposta poderá conter os dados do curso cadastrado, incluindo o `id` gerado automaticamente.

### Fluxo do cadastro

```text
Cliente
   ↓
POST /cursos
   ↓
Dados em JSON
   ↓
Back-end recebe os dados
   ↓
Transforma em objeto Java
   ↓
Verifica as regras do curso
   ↓
Salva o curso
   ↓
Devolve resposta HTTP
   ↓
201 Created
   ↓
Cliente
```

Portanto, o back-end não funciona apenas como uma tela. Ele recebe as informações do cliente, transforma e processa os dados, verifica as regras de negócio, salva as informações e devolve uma resposta adequada ao cliente.

---

## Aula 03 — Contrato Inicial da API

A API de Cursos oferecerá operações para cadastrar, consultar, atualizar e remover cursos. As operações serão realizadas através de requisições HTTP.

### Endpoints disponíveis

| Método HTTP | URL            | Operação                     | Resultado esperado                  |
| ----------- | -------------- | ---------------------------- | ----------------------------------- |
| GET         | `/cursos`      | Listar todos os cursos       | `200 OK`                            |
| GET         | `/cursos/{id}` | Buscar um curso pelo ID      | `200 OK` ou `404 Not Found`         |
| POST        | `/cursos`      | Cadastrar um novo curso      | `201 Created`                       |
| PUT         | `/cursos/{id}` | Atualizar um curso existente | `200 OK` ou `404 Not Found`         |
| DELETE      | `/cursos/{id}` | Remover um curso             | `204 No Content` ou `404 Not Found` |

### 1. Listar todos os cursos

**Método:** `GET`

**URL:**

```text
/cursos
```

Essa operação retorna todos os cursos cadastrados na API.

**Resposta esperada:**

```text
200 OK
```

---

### 2. Buscar curso pelo ID

**Método:** `GET`

**URL:**

```text
/cursos/{id}
```

O `{id}` deve ser substituído pelo identificador do curso que será consultado.

Exemplo:

```text
/cursos/1
```

Se o curso existir, a API retorna:

```text
200 OK
```

Caso o curso não seja encontrado:

```text
404 Not Found
```

---

### 3. Cadastrar curso

**Método:** `POST`

**URL:**

```text
/cursos
```

O cliente deverá enviar os dados do curso no corpo da

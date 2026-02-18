# QA API — Casos de Teste

## Sobre

Documentação dos **casos de teste de API** realizados para fins de estudo em QA,
utilizando a API de tutoriais (Bezkoder) executada localmente via Docker.

Os testes são executados principalmente com **Postman**, validando:

* Status code
* Body da resposta
* Regras de negócio
* Validações de erro

---

## Estrutura dos Casos de Teste

Cada caso contém:

* ID
* Título
* Descrição
* Endpoint
* Método
* Pré-condições
* Passos
* Resultado esperado

---

# Casos de Teste

---

## CT-001 — Criar tutorial com dados válidos

**ID:** CT-API-001
**Título:** Criar tutorial com dados válidos
**Descrição:** Testar a criação de um tutorial válido dentro da API.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Pré-condições:**

* Sistema disponível (subido via Docker)

**Passos:**

1. Abrir Postman
2. Selecionar método POST
3. Inserir a URL + endpoint
4. Adicionar body:

```json
{
  "title": "Teste QA",
  "description": "Criando tutorial",
  "published": true
}
```

5. Configurar header `Content-Type: application/json`
6. Clicar em Send

**Resultado esperado:**

* Status **200 OK**
* Body semelhante a:

```json
{
  "id": 1,
  "title": "Teste QA",
  "description": "Criando tutorial",
  "published": true,
  "createdAt": "2026-02-05T02:11:32.000Z",
  "updatedAt": "2026-02-05T02:11:32.000Z"
}
```

---

## CT-002 — Buscar lista de tutoriais

**ID:** CT-API-002
**Título:** Buscar lista de tutoriais
**Descrição:** Testar a busca completa de tutoriais cadastrados.

**Endpoint:** `/api/tutorials`
**Método:** GET

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Selecionar método GET
3. Inserir URL + endpoint
4. Clicar em Send

**Resultado esperado:**

* Status **200 OK**
* Retorno de lista de tutoriais cadastrados

---

## CT-003 — Criar tutorial inválido

**ID:** CT-API-003
**Título:** Criar tutorial com dados inválidos
**Descrição:** Testar criação sem campo obrigatório (title).

**Endpoint:** `/api/tutorials`
**Método:** POST

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body sem título:

```json
{
  "description": "Criando tutorial",
  "published": true
}
```

5. Header `Content-Type: application/json`
6. Send

**Resultado esperado:**

* Status **400 Bad Request**
* Mensagem de erro:

```json
{
  "message": "Content can not be empty!"
}
```

---

## CT-004 — Buscar tutoriais publicados

**ID:** CT-API-004
**Título:** Buscar tutoriais publicados
**Descrição:** Validar retorno apenas de tutoriais com `published = true`.

**Endpoint:** `/api/tutorials/published`
**Método:** GET

**Pré-condições:**

* Sistema disponível
* Existirem tutoriais publicados

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint
4. Send

**Resultado esperado:**

* Status **200 OK**
* Retorno apenas de registros publicados

---

## CT-005 — Buscar publicados sem dados

**ID:** CT-API-005
**Título:** Buscar publicados sem registros
**Descrição:** Validar comportamento quando não há tutoriais publicados.

**Endpoint:** `/api/tutorials/published`
**Método:** GET

**Pré-condições:**

* Sistema disponível
* Nenhum tutorial publicado

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint
4. Send

**Resultado esperado:**

* Status **200 OK**
* Body vazio ou mensagem informativa

---

## CT-006 — Buscar tutorial por ID válido

**ID:** CT-API-006
**Título:** Buscar tutorial por ID válido
**Descrição:** Validar busca individual por ID existente.

**Endpoint:** `/api/tutorials/{id}`
**Método:** GET

**Pré-condições:**

* Sistema disponível
* Existir ID válido

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint + ID
4. Send

**Resultado esperado:**

* Status **200 OK**
* Retorno do tutorial correspondente

---

## CT-007 — Buscar tutorial por ID inválido

**ID:** CT-API-007
**Título:** Buscar tutorial por ID inválido
**Descrição:** Validar comportamento para ID inexistente.

**Endpoint:** `/api/tutorials/{id}`
**Método:** GET

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint + ID inválido
4. Send

**Resultado esperado:**

* Status **400 Bad Request** (ou 404 dependendo da API)
* Mensagem de erro indicando ID não encontrado

---

## CT-008 — atualiza tutorial por ID válido

**ID:** CT-API-008
**Título:** Atualiza tutorial por ID válido
**Descrição:** Validar comportamento para ID e dados válidos para atualização.

**Endpoint:** `/api/tutorials/{id}`
**Método:** PUT

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método PUT
3. Inserir endpoint + ID válido
4. configurar o JSON com atualizações corretas
5. Send

**Resultado esperado:**

* Status **200 OK** 
* Mensagem de atualização realizada com sucesso.

---


## CT-009 — atualiza tutorial por ID inválido

**ID:** CT-API-009
**Título:** Atualiza tutorial por ID inválido + dados válidos.
**Descrição:** Validar comportamento para ID inválido e dados válidos para atualização.

**Endpoint:** `/api/tutorials/{id}`
**Método:** PUT

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método PUT
3. Inserir endpoint + ID inválido 
4. configurar o JSON com atualizações corretas
5. Send

**Resultado esperado:**

* Status **400 Bad Request** 
* Mensagem de ID inválido ou inexistente.

---

## CT-010 — atualiza tutorial por ID válido + dados inválidos

**ID:** CT-API-010
**Título:** Atualiza tutorial por ID válido + dados inválidos.
**Descrição:** Validar comportamento para ID válido e dados inválidos para atualização.

**Endpoint:** `/api/tutorials/{id}`
**Método:** PUT

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método PUT
3. Inserir endpoint + ID válido 
4. configurar o JSON com atualizações inválidos 
5. Send

**Resultado esperado:**

* Status **400 Bad Request** 
* Mensagem de atualização não permitida.

---

## CT-011 — deleta tutorial por ID válido 

**ID:** CT-API-011
**Título:** Deleta tutorial por ID válido. 
**Descrição:** Validar comportamento para deletar um ID válido.

**Endpoint:** `/api/tutorials/{id}`
**Método:** DELETE

**Pré-condições:**

* Sistema disponível
* Existir ID válido

**Passos:**

1. Abrir Postman
2. Método DELETE
3. Inserir endpoint + ID válido 
4. Send

**Resultado esperado:**

* Status **200 OK** 
* Mensagem de tutorial/ID deletado com sucesso.

---

## CT-012 — deleta tutorial por ID inválido 

**ID:** CT-API-012
**Título:** Deleta tutorial por ID inválido. 
**Descrição:** Validar comportamento para deletar um ID inválido de tutorial não existente.

**Endpoint:** `/api/tutorials/{id}`
**Método:** DELETE

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método DELETE
3. Inserir endpoint + ID inválido 
4. Send

**Resultado esperado:**

* Status **400 Bad request** 
* Mensagem de tutorial/ID inexistente para deletar.

---

## CT-013 — deleta todos tutoriais

**ID:** CT-API-013
**Título:** Deleta todos tutoriais. 
**Descrição:** Validar comportamento para deletar todos tutoriais existentes.

**Endpoint:** `/api/tutorials`
**Método:** DELETE

**Pré-condições:**

* Sistema disponível
* Possuir tutoriais 

**Passos:**

1. Abrir Postman
2. Método DELETE
3. Inserir endpoint
4. Send

**Resultado esperado:**

* Status **200 OK** 
* Mensagem de tutoriais deletados com sucesso.

---

## CT-014 — Criar tutorial com dados duplicados

**ID:** CT-API-014
**Título:** Criar tutorial com dados duplicados
**Descrição:** Testar a criação de um tutorial válido com dados duplicados (que ja existem em outro tutorial) dentro da API.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Pré-condições:**

* Sistema disponível (subido via Docker)

**Passos:**

1. Abrir Postman
2. Selecionar método POST
3. Inserir a URL + endpoint
4. Adicionar body:

```json
{
  "title": "Teste QA",
  "description": "Criando tutorial",
  "published": true
}
```

5. Configurar header `Content-Type: application/json`
6. Clicar em Send

**Resultado esperado:**

* Status **200 OK**
* API permite duplicidade.
* Novo registro criado.

---

## CT-015 — Criar tutorial apenas com campo obrigatório

**ID:** CT-API-015
**Título:** Criar tutorial apenas com title
**Descrição:** Validar criação contendo somente campo obrigatório.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Pré-condições:**

* Sistema disponível

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body:

```json
{
  "title": "Somente titulo"
}
```

5. Send

**Resultado esperado:**

* Status **200 OK**
* Tutorial criado com campos opcionais null/default

---

## CT-016 — Criar tutorial com published = false

**ID:** CT-API-016
**Título:** Criar tutorial não publicado
**Descrição:** Validar criação com published falso.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body:


```json
{
  "title": "Tutorial não publicado",
  "published": false
}
```
5. Send

**Resultado esperado:**

* Status **200 OK**
* Campo published = false

---

## CT-017 — Criar tutorial com title vazio

**ID:** CT-API-017
**Título:** Criar tutorial com title vazio
**Descrição:** Validar criação com campo obrigatório vazio.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body:


```json
{
  "title": "",
  "published": true
}
```
5. Send

**Resultado esperado:**

* Status **400 Bad request**
* mensagem de erro de campo obrigatorio vazio.

---

## CT-018 — Criar tutorial com tipo inválido em title

**ID:** CT-API-018
**Título:** Criar tutorial com title numérico
**Descrição:** Validar criação com dados inválidos (title com caracteres numericos).

**Endpoint:** `/api/tutorials`
**Método:** POST

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body:


```json
{
  "title": "1234"
}
```
5. Send

**Resultado esperado:**

* Status **400 Bad request**
* Mensagem de titullo inválido.

---

## CT-019 — Criar tutorial com published inválido

**ID:** CT-API-019
**Título:** Criar tutorial com published string
**Descrição:** Validar criação com campo published de tipo inválido.

**Endpoint:** `/api/tutorials`
**Método:** POST

**Passos:**

1. Abrir Postman
2. Método POST
3. Inserir endpoint
4. Body:


```json
{
  "title": "titulo ok",
  "published": "sim"
}
```
5. Send

**Resultado esperado:**

* Status **400 Bad request**

---

## CT-020 — Listar tutoriais sem registros

**ID:** CT-API-020
**Título:** Listar sem dados cadastrados
**Descrição:** Validar busca sem dados cadastrados de tutoriais.

**Endpoint:** `/api/tutorials`
**Método:** GET

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint
4. Send 

**Resultado esperado:**

* Status **200 OK**
* Lista vazia

---

## CT-021 — Validar estrutura do retorno

**ID:** CT-API-021
**Título:** Validar contrato da resposta

**Validações:**

* id existente
* title string
* published boolean
* createdAt presente

---

## CT-022 — Buscar tutorial com ID tipo inválido

**ID:** CT-API-022
**Título:** Buscar com tipo inválido no ID
**Descrição:** Validar busca com ID de tipo inválido.

**Endpoint:** `/api/tutorials/{id}`
**Método:** GET

**Passos:**

1. Abrir Postman
2. Método GET
3. Inserir endpoint + ID de tipo string
4. Send 

**Resultado esperado:**

* Status **400 Bad request**
* tipo de ID inválido

---

## CT-023 — Atualizar tutorial sem body

**ID:** CT-API-023
**Título:** atualizar sem body
**Descrição:** Validar atialização com body vazio.

**Endpoint:** `/api/tutorials`
**Método:** PUT

**Passos:**

1. Abrir Postman
2. Método PUT
3. Inserir endpoint
4. body vazio de atualização
5. Send 

**Resultado esperado:**

* Status **400 Bad request**

---

## CT-024 — Deletar todos sem registros

**ID:** CT-API-024
**Título:** Deleta todos tutoriais sem dados criados. 
**Descrição:** Validar comportamento para deletar tutoriais mas sem possuir tutoriais criados.

**Endpoint:** `/api/tutorials`
**Método:** DELETE

**Pré-condições:**

* Sistema disponível
* base de tutoriais vazia

**Passos:**

1. Abrir Postman
2. Método DELETE
3. Inserir endpoint
4. Send

**Resultado esperado:**

* Status **200 OK** 

---

## Observações

Os casos de teste estão em expansão conforme novos endpoints e regras são validados.
Possível melhoria: impedir duplicidade.







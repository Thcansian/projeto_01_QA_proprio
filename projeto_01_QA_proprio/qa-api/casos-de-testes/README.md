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

## Observações

Os casos de teste estão em expansão conforme novos endpoints e regras são validados.
